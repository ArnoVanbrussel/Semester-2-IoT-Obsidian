```
## Multiple Choice Questions with Answers:

**1. Welk protocol wordt gebruikt om domeinnamen te vertalen naar IP-adressen?**

(a) DHCP - Onjuist. DHCP wordt gebruikt om IP-adressen en andere netwerkconfiguratie-instellingen toe te wijzen aan apparaten op een netwerk.
(b) DNS - **Juist**. DNS (Domain Name System) is verantwoordelijk voor het vertalen van domeinnamen (zoals [www.google.com](https://www.google.com/)) naar de bijbehorende IP-adressen (zoals 142.250.189.142).
(c) HTTP - Onjuist. HTTP (Hypertext Transfer Protocol) wordt gebruikt voor het verzenden en ontvangen van webpagina's en andere gegevens over het internet.
(d) FTP - Onjuist. FTP (File Transfer Protocol) wordt gebruikt voor het overzetten van bestanden tussen computers.

**2. Wat is het voordeel van het gebruik van VLAN's?**

(a) Verhoogt de netwerksnelheid - Onjuist. VLAN's beïnvloeden de netwerksnelheid direct niet.
(b) Verbetert de netwerkbeveiliging - **Juist**. VLAN's isoleren verkeer van verschillende netwerksegmenten, waardoor onbevoegde toegang en beveiligingsrisico's worden verminderd.
(c) Vermindert netwerkcongestie - Juist. VLAN's kunnen netwerkcongestie verminderen door verkeer te segmenteren en te voorkomen dat overtollig verkeer door het hele netwerk wordt verzonden.
(d) Alle bovenstaande - Juist. VLAN's bieden alle genoemde voordelen: verbeterde beveiliging, verminderde congestie en flexibiliteit in netwerkbeheer.

**3. Welke DHCP-optie is essentieel om verbinding te maken met internet?**

(a) Subnetmasker - Onjuist. Hoewel een subnetmasker belangrijk is voor netwerkidentificatie, is het niet direct essentieel voor internetverbinding.
(b) Default gateway - **Juist**. De default gateway is het IP-adres van de router die verkeer naar andere netwerken routeert, inclusief internet.
(c) DNS-servers - Juist. DNS-servers zijn nodig om domeinnamen te vertalen naar IP-adressen, wat essentieel is voor het bezoeken van websites.
(d) Alle bovenstaande - Juist. Alle drie de opties (default gateway, DNS-servers en leasetijd) zijn essentieel voor een succesvolle internetverbinding via DHCP.

**4. Wat is het doel van een nameserver?**

(a) Om e-mailberichten te verzenden en te ontvangen - Onjuist. E-mail wordt verzonden via mailservers, niet via nameservers.
(b) Om bestanden op te slaan en op te halen - Onjuist. Bestanden worden opgeslagen op servers, niet op nameservers.
(c) Om domeinnamen te vertalen naar IP-adressen - **Juist**. Dit is de primaire functie van een nameserver.
(d) Om websites weer te geven - Onjuist. Websites worden weergegeven door webservers, niet door nameservers.

**5. Wat is het verschil tussen NAT en port forwarding?**

(a) NAT verbergt IP-adressen, terwijl port forwarding poorten opent. - **Juist**. NAT (Network Address Translation) verbergt de interne IP-adressen van apparaten op een netwerk achter één extern IP-adres. Port forwarding stuurt verkeer van internet naar een specifiek apparaat op het interne netwerk door een bepaalde poort te openen.
(b) NAT is een routerfunctie, terwijl port forwarding een firewallfunctie is. - Onjuist. Zowel NAT als port forwarding kunnen worden geconfigureerd op routers en firewalls.
(c) NAT wordt gebruikt voor interne netwerken, terwijl port forwarding wordt gebruikt voor externe netwerken. - Onjuist. NAT wordt gebruikt op zowel interne als externe netwerken, terwijl port forwarding primair wordt gebruikt voor extern verkeer.
(d) Alle bovenstaande - Onjuist. Niet alle beweringen zijn correct.

**6. Welk routingprotocol wordt gebruikt om de beste route naar een bestemming te bepalen?**

(a) RIP - Onjuist. RIP (Routing Information Protocol) is een eenvoudig protocol met beperkte schaalbaarheid.
(b) OSPF - Juist. OSPF (Open Shortest Path First) is een geavanceerder protocol dat dynamische routing en load balancing biedt.
(c) BGP - Juist. BGP (Border Gateway Protocol) wordt gebruikt voor routing tussen autonome systemen (AS

**2. Link Aggregation:**

Link aggregation, also known as bonding, combines multiple physical network connections into one logical connection. This increases bandwidth, improves redundancy, and provides fault tolerance. Link aggregation is beneficial in scenarios where high bandwidth is required, such as cloud computing, streaming media, or network storage.

**4. DNS (Deep Dive):**

- **Nameservers:** Servers that translate domain names into IP addresses.
- **DNS record types:**
    - A record: Maps a domain name to an IPv4 address.
    - MX record: Specifies the mail server for a domain.
    - CNAME record: Alias for another domain name.
    - NS record: Defines the nameservers for a domain.
    - SOA record: Contains startup information about a domain.
- **Split-DNS configurations:** Separate internal and external DNS records for different purposes.
- **DNSSEC:** Provides security for DNS traffic using cryptography.

**5. NAT & Port Forwarding:**

| NAT Type | Description | Source NAT | Destination NAT |
| --- | --- | --- | --- |
| Hide NAT | Hides all internal IP addresses behind one external IP address. | Common in home networks. | Limited functionality for external access. |
| PAT (Port Address Translation) | Translates internal IP addresses and port numbers to one external IP address and port number. | Allows more flexibility for external access. | Requires port forwarding for specific devices and services. |
| Multi-NAT | Implements NAT on multiple routers or firewalls for layered security. | More complex to configure and manage. | Provides enhanced security and flexibility for large networks. |

drive_spreadsheetExporteren naar Spreadsheets

**Port forwarding:**

- **Open ports:** Select ports to open (higher than 5xxx) to allow external access to specific services.
- **Port mapping:** Bind internal IP addresses and port numbers to the opened external ports.
- **Well-known ports:** Forward common ports used by specific services (e.g., 80 for HTTP, 25 for SMTP).

**6. Routing Protocols:**

| Protocol | Description | Advantages | Disadvantages |
| --- | --- | --- | --- |
| RIP (Routing Information Protocol) | Simple, compatible with older devices. | Limited scalability, not suitable for large networks. |  |
| OSPF (Open Shortest Path First) | Dynamic, scalable, supports load balancing. | More complex configuration and management. |  |
| BGP (Border Gateway Protocol) | Used for inter-AS routing on the internet. | Highly complex, requires specialized expertise. |  |

drive_spreadsheetExporteren naar Spreadsheets

**7. IPv6: In-Depth:**

- **Advantages of IPv6 over IPv4:**
    - **Larger address space:** IPv6 has 128-bit addresses, providing a vast address space compared to IPv4's 32-bit addresses.
    - **Reduced risk of address depletion:** The vast address space of IPv6 minimizes the risk of running out of IP addresses, a growing concern with IPv4.
    - **Simplified header structure:** IPv6 has a simplified header structure, making it more efficient for routing and processing.
    - **Enhanced security:** IPv6 incorporates security features like IPsec, providing better protection against network attacks.
- **Simplification of network administration:** IPv6's autoconfiguration features and reduced address conflicts can simplify network administration tasks.
- **Importance of ICMPv6:** ICMPv6 is the equivalent of ICMPv4 in IPv6, responsible for error reporting, neighbor discovery, and other essential network functions.
- **Understanding default route:** The default route in IPv6, as in IPv4, points to the router that handles traffic destined for networks other than the local one.
- **Addressing Android device issues:** Some older Android devices may have compatibility issues with IPv6, requiring network configuration or software updates.
```