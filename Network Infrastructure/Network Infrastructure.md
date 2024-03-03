# Week 1 - Theorie
## Herhaling subnetting

![[IP Addressing.pdf]]
### Klassen
- Bepaald door 1e byte:

| Class | Mask | Private |
| ---- | ---- | ---- |
| A | /8 | 10.x.x.x |
| B | /16 | 172.16.x.x - 172.31.x.x |
| C | /24 | 192.168.x.x |
| D | / | / |
**Oefening 1**
IP: 192.191.136.210
Mask: 255.255.255.192
- Klasse: 
	- C
- Publiek/privaat
	- Publiek
- Prefix: 
	- /26
- Aantal hosts: 
	- 2^6-2 = 62
	- 32-26 = 6
- Network address: 
	- 192.191.136.192
- Broadcast address: 
	- 192.191.136.255
	- invert van de host bits v/h netwerkadres
- Eerste bruikbare IP
	- 193.191.136.193
- Laatst bruikbare IP
	- 193.191.136.254
**Oefening 2**
IP: 172.16.254.23 /30
- Klasse
	- B
- Classfull Mask
	- 16
- Decimale notatie
	- 255.255.255.252
- Privaat / Publiek
	- Privaat
- Aantal hosts
	- 2^2-2 = 2
- Network address
	- 172.16.254.20
- Broadcast address
	- 172.16.254.23
- Hoeveel subnetten kunnen we maken van het "Classfull" netwerk? (172.16.0.0/16)
netwerkbits - netwerkbits vd classfull = subnetbits
/30 - /16 = /14 -> 2^14 = 16.284 subnets

**Oefening 3**
172.16.0.0/16
- Verdeel dit IP netwerk in subnets van max. 100 hosts. Subnetmask in prefixnotatie?
	- Eerste 'propere macht' van 2 minstens 100 = 128
		- 128 = 2^7
		- 32-7 = 25
		- /25
		- 255.255.255.128
- Geef het laatste subnet van de reeks.
	- 172.16.255.128/25

## Routing

![[Static_Routing.pdf]]

**Waarom subnetten?**
- 172.23.0.0/16 --> netwerk campus
- 172.23.80.0/23 --> iedere klas is /23
- zonder de /16 moest iedere klas een aparte route hebben voor publiek internet
- Communicatie tussen subnetten filteren / blokkeren
- Verkleinen van broadcast range -> sneller netwerk

**Examen**
**Dynamic routing**

# Week 2
## Layer 2- Layer 3 switches
### Layer-2
- Layer-2 switches forward frames fast (wire speed / non-blocking) in hardware, ASIC
- Based on MAC Addresses
- Using a CAM table
![[Pasted image 20240222095751.png]]
- Learning is based on source MAC address (filling CAM table)
	- *Important: the switch does NOT actively learn MAC addresses, it only listens!!!*
- Forwarding is based on destination MAC address
- Flooding, if no MAC address is found in the CAM table
### Types of switches
- By form factor
	- Desktop switch
	- Rack-mountable switch
	- Chassis switch
- By configuration options
	- Unmanaged switch
		- No config interface or options
		- plug-and-play
		- no MAC/IP addresses on its own
	- Managed switch
		- One or more methods to modify the operation of the switch
		- Through CLI, serial, telnet, ssh, web interface or SNMP
		- Has at least one MAC/IP address
		- 2 sub-classes
			- Smart switches
				- Managed switches with limited set of management features
			- Enterprise managed switches
				- full set of management features, including CLI, SNMP agent and web interface
### Extra features
- [Link aggregation](https://en.wikipedia.org/wiki/Link_aggregation)
	- Available on manageable switches (caution: network loops)
	- Protocols: LACP or EtherChannel (by Cisco) or Port Aggregation Protocol (PAgP) (by Cisco)
	- Advantage:
		- Speed (performance)
		- Redundancy
- [Rapid Spanning Tree Protocol](https://en.wikipedia.org/wiki/Spanning_Tree_Protocol#Rapid_Spanning_Tree_Protocol) (RSTP or 802.1w)![[Pasted image 20240222100439.png]]
- VLAN
## Addressing Methods
- if LSB = 0
	- Unicast
- if LSB = 1
	- Multicast
- Multicast
- Broadcast
	- Binary all 1's
- Anycast (zie IPv6)
	- one-to-one-of-many association
## Basics on the Ethernet frame
- Max 1518 byte
- Min 64 Byte
	- If smaller = RUNT Frame
![[Pasted image 20240222084551.png]]
- Preamble = 10101010...
- Data starts after the first 8 bytes
- 2 byte length
	- value <= 1500 = 'native' 802.3 frame
	- value >= 1535 = EtherType (Ethernet-II frame)
		- Some Ethertypes:
			- IPv4 - 0x0800
			- IPv6 - 0x86DD
			- ARP - 0x0806
			- 802.1Q (VLAN tagged frame) - 0x8100
- Data
![[Pasted image 20240222085212.png|350]]![[Pasted image 20240222085229.png|350]]
## Ecapsulation examples
### DNS
![[Pasted image 20240222085408.png]]
### HTTP
![[Pasted image 20240222085448.png]]
### SMTP
![[Pasted image 20240222085504.png]]
### POP3
- Mail lezen
	- Ook kennen:
		- [IMAP4](https://nl.wikipedia.org/wiki/Internet_Message_Access_Protocol)
![[Pasted image 20240222085519.png]]
### ICMP (v4)
- Ping
- Tracert
![[Pasted image 20240222085537.png]]
### SNMP
![[Pasted image 20240222085551.png]]
### FTP
![[Pasted image 20240222085604.png]]
### TFTP
![[Pasted image 20240222085653.png]]
## VLAN versus Subnet (EXAMEN)
![[Pasted image 20240222090609.png]]
1. **VLAN (Virtual Local Area Network):**
    - **Scenario:** When you want to logically segment a single physical network into multiple isolated broadcast domains.
    - **Use Cases:**
        - **Security:** VLANs can be used to enhance security by isolating sensitive or critical network segments from the rest of the network.
        - **Broadcast Control:** By breaking a large broadcast domain into smaller VLANs, you reduce the broadcast traffic within each VLAN, improving overall network performance.
        - **Departmental Isolation:** In enterprise environments, VLANs can be assigned based on departments (e.g., finance, marketing) to logically isolate their traffic.
2. **Subnet:**
    - **Scenario:** When you want to divide a larger IP network into smaller, more manageable segments.
    - **Use Cases:**
        - **Network Segmentation:** Subnets allow you to divide a large network into smaller subnetworks for better organization and management.
        - **Routing and IP Addressing:** Subnets enable efficient routing by breaking down a large network into smaller segments, each with its own IP address range.
        - **Broadcast Domain Control:** Like VLANs, subnets help control broadcast domains, as broadcasts are confined to the specific subnet.

- Layer-2 VLAN
	- VLAN without IP address
- Unnumbered VLAN
	- VLAN without IP address
- Layer-3 VLAN
	- VLAN with IP address
- Numbered VLAN
	- VLAN with IP address
- Native VLAN 
	- Vangnet voor untagged traffic
	- Technisch concept / Security concept
	- Zelf configureren
- Management VLAN
	- Gebruikersconcept, niks technisch
	- VLAN om je device remote te beheren/configureren

**VLAN commando's**
```
# Unnumbered VLAN
vlan 10
name Servers
int vlan10
desc Server
no shut

vlan 20
name Users
int vlan20
desc Users
no shut

vlan 30
name Production
int vlan30
desc Production
no shut

# Numbered VLAN
ip routing (L3-switching)
vlan 10
name Servers
int vlan10
desc Server
ip address 192.168.10.1 255.255.255.0
ip helper-address 192.168.20.254
no shut

ip route 0.0.0.0 0.0.0.0 192.168.10.0

vlan 20
name Users
int vlan20
desc Users
ip address 192.168.20.1 255.255.255.0
no shut

ip route 0.0.0.0 0.0.0.0 192.168.20.0

vlan 30
name Production
int vlan30
desc Production
ip address 192.168.30.1 255.255.255.0
ip helper-address 192.168.20.254
no shut

ip route 0.0.0.0 0.0.0.0 192.168.20.0

vlan 40
name Telefonie
int vlan40
desc Telefonie
no shut

ip route 0.0.0.0 0.0.0.0 192.168.30.0

# Management
int vlan 100
name Mgt
int vlan100
desc Mgt
ip address 192.168.100.1 255.255.255.0
no shut
ip default-gateway 192.168.100.1

int vlan 666
name native
int vlan666
desc native
no shut

int range fa0/1-8
switchport mode access
switchport access vlan 10
desc Servers

int range fa0/9-16
switchport mode access
switchport access vlan 20
desc Users

int range fa0/17-22
switchport mode access
switchport access vlan 40
desc Telefonie

# Typisch L2-switch
int fa0/24
(switchport trunk encapsulation dot1q)
switchport mode trunk
switchport trunk native vlan 666

# Typisch L3-switch
int fa0/24
(switchport trunk encapsulation dot1q)
switchport mode trunk
switchport trunk allowed vlan 10,20,40
switchport trunk native vlan 666

(switchport trunk allowed add vlan 50)
```

## DNS
[FQDN](https://en.wikipedia.org/wiki/Fully_qualified_domain_name) -> ISP

www.sales.microsoft.com(.)
host.subDomain.2ndLevelDomain.topLevelDomain(root)

- nslookup
	- FQDN (forward lookup)
	- Ip (reverse lookup)
- Primary DNS server =/= preferred dns
	- "Zonefile"
		- Records bijmaken (R/W)
- Secondary DNS server =/= alternate dns
	- Read only zonefile
		- Zone transfer (standaard 15 minuten)
- Zonefile
	- DNS records
		- SOA start of authority
			- serienummer
			- TTL
			- email address
			- timers
		- NS records
			- These records specify authoritative DNS servers for the domain. They delegate the responsibility of resolving the domain to these specified name servers.
			- `example.com.    IN    NS    ns1.example.com.`
		- A record
			- These records associate a domain name with an IPv4 address. They are used to point a domain or subdomain to a specific IP address.
			- `www.example.com.    IN    A    192.168.1.1`
		- AAAA records
			- AAAA records are similar to A records, but they are used for IPv6 addresses instead of IPv4 addresses. While A records map a domain or subdomain to an IPv4 address, AAAA records (pronounced "quad-A records") map a domain or subdomain to an IPv6 address.
			- `example.com.    IN    AAAA    2001:0db8:85a3:0000:0000:8a2e:0370:7334`
		- MX records
			- MX (Mail Exchange) records are DNS records that specify the mail servers responsible for receiving emails on behalf of a domain. MX records play a crucial role in the email delivery process by indicating which servers are authorized to accept incoming emails for a particular domain.