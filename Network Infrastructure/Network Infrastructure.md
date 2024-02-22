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