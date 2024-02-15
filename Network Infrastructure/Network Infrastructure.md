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
![[IP Routing.pdf]]
![[Static_Routing.pdf]]