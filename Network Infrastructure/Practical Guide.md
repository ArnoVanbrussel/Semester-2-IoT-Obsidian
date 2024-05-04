# Overall
## Set Hostname
```
ena
conf t
hostname <hostname>
```
## Add Banner
```
enable
configure terminal
banner motd
#
#  +--------------------------------------+
#  |                  @@                  |
#  |              @@@@@@@@@               |
#  |           @@@@@@@@@@@@@@@@           |
#  |        @@@@@@@@@@@@@@@@@@@@@         |
#  |        @@@@@@@@@@@@@@@@@@@@@@        |
#  |        @@@   @@@@@@@@@@   @@@        |
#  |        @@@       @@       @@@        |
#  |        @@@                @@@        |
#  |        @@@                @@@        |
#  |        @@@                @@@        |
#  |        @@@    @@    @@    @@@        |
#  |          @    @@@@@@@@    @          |
#  |               @@@@@@@@               |
#  |                                      |
#  |     ,--.   ,--. ,-----.,--------.    |
#  |     |   `.'   |'  .--./'--.  .--'    |
#  |     |  |'.'|  ||  |       |  |       |
#  |     |  |   |  |'  '--'\   |  |       |
#  |     `--'   `--' `-----'   `--'       |
#  |                                      |
#  |                                      |
#  |~^~^~^~^~^~^~^~^~^~^~^~^~^~^~^~^~^~^~^|
#  |                                      |
#  |             ___     ______           |
#  |            / \ \   / / __ )          |  
#  |           / _ \ \ / /|  _ \          |   
#  |          / ___ \ V / | |_) |         |  
#  |         /_/   \_\_/  |____/          | 
#  |                                      |
#  |    Welcome to my managed router!     |
#  |   Beware! This is a secure zone!     |
#  |                                      |
#  +--------------------------------------+
#
```

## Errors wegdoen
```
ena
conf t
no ip domain-lookup
no service config
```
## Save config
```
copy r s
```
## Remove config
```
erase startup-config
del vlan.dat
reload
setup
	no
```
## Backup config
```
copy running-config tftp
	ip
	file name
```
## Set up SSH
```
hostname <hostname>
ip domain-name <domain-name>
username <username> privilege 15 password 0 admin
vlan 20
name MGT
int vlan20
ip address <IP> <subnet mask>
no shut
exit
crypto key generate rsa
	1024
line vty 0 15
access-class 20 in
transport input ssh
```
# Layer 2 Switch
## VLAN
```
ena
conf t

vlan 10
name <vlan-naam>

int vlan10
descr <vlan descr>
no ip address
no shut

interface range fa0/1-8
switchport mode access
switchport access vlan 10
spanning-tree portfast
no shut
```
## VLAN Trunk
```
ena
conf t
int gi1/0/24
descr <trunk-port>
switchport mode trunk
switchport trunk native vlan 999
no shut
```
## Creating port-channel
```
default int fa0/23
default int fa0/24

int range fa0/23-24
channel-group 1 mode active

int port-channel1
descr <port-channel-descr>
switchport mode trunk
switchport trunk native vlan 999
```
# Layer 3 Switch
## VLAN
```
ena
conf t
ip routing

vlan 30
name <vlan-naam>

int vlan30
descr <vlan descr>
ip address 192.168.30.1 255.255.255.0
ip helper-address <ip addr of DHCP server>
no shut

int range gi1/0/1-8
switchport mode access
spanning-tree portfast
switchport access vlan 30
```
## VLAN Trunk
```
ena
conf t
int gi1/0/24
descr <trunk-port>
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan 10, 20, 30
switchport trunk native vlan 999
no shut
```
## Creating port-channel
```
default int gi1/0/23
default int gi1/0/24

int range gi1/0/23-24
channel-group 1 mode active

int port-channel1
descr <port-channel-descr>
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk native vlan 999
```
# Router
## Configuring WAN interface
```
conf t
int fa0/0
ip address dhcp
descr WAN
ip nat outside
no shut
```
## Configuring LAN interface
```
conf t
int fa0/1
descr LAN
ip address <ip addr> <subnet mask>
ip nat inside
no shut
```
## Configuring a static route
```
conf t
ip route 0.0.0.0 0.0.0.0 <WAN interface> #only one static route!!!
ip route 0.0.0.0 0.0.0.0 <IP addr next-hop router>
ip route <dest. network addr> <subnet mask> <IP next-hop router>
```
## Configuring nat
```
conf t
ip nat inside source list 1 interface <WAN interface> overload
access-list 1 permit <LAN subnet> <LAN subnet mask>
```
## Configuring subinterfaces (Routing between L2 VLANS, using 802.1Q/VLAN Tagging)
```
int fa0/1
descr LAN
######### IMPORTANT
no ip address
no shut

int fa0/1.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
ip nat inside
no shut

int fa0/1.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
ip nat inside
ip helper address 192.168.10.11
no shut

int fa0/1.999
encapsulation dot1Q 999 native
no shut
end

## Vergeet access-list voor vlans niet toe te voegen
```
## Router as DHCP server
```
conf t
service dhcp
ip dhcp pool <name>
network <(sub)network address> <subnet mask>
default-router <default gateway>
dns-server <dns server 1> <dns server 2>
domai me <domain FQDN>1
ip dhcp excluded-address <one IP>
ip dhcp excluded-address <first IP> <last IP>
show ip dhcp binding
```
## VPN
```
# WAN IP STATISCH INSELLEN OP BEIDE ROUTERS
#site 1 met WAN IP: 78.55.44.2 255.255.255.0

crypto isakmp policy 1

encr 3des
hash md5
authentication pre-share
group 2
lifetime 86400
crypto isakmp key firewallcx address 78.55.44.1
ip access-list extended VPN-TRAFFIC
permit ip 192.168.0.0 0.0.0.255 192.168.1.0 0.0.0.255
crypto ipsec transform-set TS esp-3des esp-md5-hmac

crypto map CMAP 10 ipsec-isakmp

set peer 78.55.44.1
set transform-set TS
match address VPN-TRAFFIC
int fa0/1 # WAN port
crypto map CMAP

conf t
ip nat inside source list 100 interface fa0/1 overload
access-list 100 remark -=[Define NAT Service]=-  
access-list 100 deny ip 192.168.0.0 0.0.0.255 192.168.1.0 0.0.0.255
access-list 100 permit ip 192.168.0.0 0.0.0.255 any  
access-list 100 remark
end

# Andere access list weg doen

# site 2 met WAN IP: 78.55.44.1 255.255.255.0

crypto isakmp policy 1

encr 3des
hash md5
authentication pre-share
group 2
lifetime 86400

crypto isakmp key firewallcx address 78.55.44.2

ip access-list extended VPN-TRAFFIC
permit ip 192.168.1.0 0.0.0.255 192.168.0.0 0.0.0.255

crypto ipsec transform-set TS esp-3des esp-md5-hmac

crypto map CMAP 10 ipsec-isakmp

set peer 78.55.44.2
set transform-set TS
match address VPN-TRAFFIC

int fa0/1
crypto map CMAP

conf t
ip nat inside source list 100 interface fa0/1 overload
access-list 100 remark -=[Define NAT Service]=-  
access-list 100 deny ip 192.168.1.0 0.0.0.255 192.168.0.0 0.0.0.255
access-list 100 permit ip 192.168.1.0 0.0.0.255 any  
access-list 100 remark
end
```
![[Configuring Site to Site IPSec VPN Tunnel Between Cisco Routers (2).pdf]]
