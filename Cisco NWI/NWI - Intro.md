# 1 Networking Today
## 1.1 Networks Affect our Lives
> Nothing important

## 1.2 Network Components
### 1.2.1 Host Roles

**Hosts**
> All computers connected to a network and who participate directly in network communication/

- has IP address
	- Identifies the host and the network to which host is attached

**Servers**
> Computers with software that allow them to provide information, like email or web pages, to end devices.

- Server software per service
- Service can be provided to multiple clients simultaneously

**Clients**
> Clients are a type of host, who have software for requesting and displaying the information obtained from the server.

![[Pasted image 20240303104149.png|600]]
### 1.2.2 Peer-to-Peer

- 1 host can be both client and server
	- E.g.: small businesses & homes
	- = Peer-to-Peer network
![[Pasted image 20240303104450.png]]
**Advantages:**
- Easy to set up
- Less complex
- Lower cost because network devices and dedicated servers may not be required
- Can be used for simple tasks such as transferring files and sharing printers
**Disadvantages:**
- No centralized admin
- Not as secure
- Not scalable
- May slow performance

### 1.2.3 End Devices

- Each end device on a network has an address
	- Source address
	- Destination Address
- E.g.: Phone, Laptop

### 1.2.4 Intermediary Devices

> Connect the individual end devices to the network. Can connect multiple individual networks to form internetwork.

**Common intermediary devices:**
- Wireless router
- LAN switch
- Router
- Multilayer switch
- Firewall appliance

### 1.2.5 Network Media

> Communication transmits across a network on media. The media provides the channel over which the message travels from source to destination.

**3 typical media:**
- Copper wire:
	- Ethernet
	- Coax
- Fiber-optic
- Wireless

## 1.3 Network Representations and Topologies
### 1.3.1 Network Representations
![[Pasted image 20240303105459.png]]
- Network Interface Card (NIC)
	- Physically connects the end device to a network
- Physical Port
	- A connector or outlet on a networking device where the media connects
- Interface
	- Specialized ports on a networking device that connect to individual networks
	- Because routers connect to networks, the ports on a router are referred to as network interfaces
### 1.3.2 Topology Diagrams

**Physical Topology Diagrams**
- Show physical location of intermediary devices and cable installation
![[Pasted image 20240303105851.png]]
**Logical Topology Diagrams**
- Illustrate devices, ports and the addressing scheme of the network
![[Pasted image 20240303105931.png]]
## 1.4 Common Types of Networks
### 1.4.1 Networks of Many Sizes
- SOHO = Small Office and Home Office networks
- Small home networks
	- connect a few computers to each other and to the internet.
- The SOHO network
	- allows computers in a home office or a remote office to connect to a corporate network, or access centralized, shared resources.
- Medium to large networks
	- can have many locations with hundreds or thousands of interconnected hosts
- The internet
	- is a network of networks that connects hundreds of millions of computers world-wide
### 1.4.2 LANs and WANs
- Network infrastructures vary greatly in terms of:
	- Size of the area covered
	- Number of users connected
	- Number and types of services available
	- Area of responsibility
- LAN = Local Area Network
- WAN = Wide Area Network
![[Pasted image 20240303113125.png]]
**LAN**
- Small geographical area
- Characteristics
	- Interconnect end devices in a limited area
	- Usually administrated by single organization or individual
		- Admin control is enforced at the network level and governs the security and access control policies
	- Provide high-speed bandwidth to internal end devices and intermediary devices
![[Pasted image 20240303113315.png]]
**WAN**
- Wide geographical area
- Characteristics:
	- WANs interconnect LANs over wide geographical areas such as between cities, states, provinces, countries, or continents.
	- WANs are usually administered by multiple service providers.
	- WANs typically provide slower speed links between LANs.
![[Pasted image 20240303113352.png]]
### 1.4.3 The Internet
> Worldwide collection of interconnected networks

- LANs use WAN services to interconnect

### 1.4.4 Intranets and Extranets
**Intranet**
- Term used to refer to a private connection of LANs and WANs that belong to an organization
- Designed to be accessible only by the organizations members, employees, etc

**Extranet**
> Organization may use extranet to provide secure and save access to individuals who work for a different organization but require access to the organization's data

- Examples:
	- Company that is providing access to outside suppliers and contractors
	- Hospital that is providing a booking system to doctors so they can make appointments for their patients
	- Local office of education that is providing budget and personnel info to the schools in its district
![[Pasted image 20240303113850.png]]
## 1.5 Internet Connections
### 1.5.1 Internet Access Technologies
- **Home Users and Small Offices:**
    - Connect to the internet via ISPs.
    - Options include broadband cable, DSL, wireless WANs, and mobile services.
- **Organizations:**
    - Require fast connections for internal and external communications.
    - Business-class services provided by Service Providers (SPs).
    - Options include business DSL, leased lines, and Metro Ethernet.
- **Common Connection Technologies:**
    - Broadband cable: High-speed internet via cable television lines.
    - DSL: Digital Subscriber Line providing internet access over telephone lines.
    - Wireless WANs: Wireless Wide Area Networks for remote connectivity.
    - Mobile services: Internet access through mobile networks.
    - Leased lines: Dedicated and private communication lines for businesses.
    - Metro Ethernet: High-speed data connections within a metropolitan area.
### 1.5.2 Home and Small Office Internet Connections
![[Pasted image 20240303114146.png]]
- **Cable:**
    - Offered by cable TV providers.
    - Uses the same cable for television and internet data.
    - Provides high bandwidth, high availability, and always-on connectivity.
- **DSL:**
    - Digital Subscriber Lines run over telephone lines.
    - Offers high bandwidth, availability, and always-on connection.
    - Commonly used for Asymmetrical DSL (ADSL), with faster download than upload speeds.
- **Cellular:**
    - Utilizes cell phone networks for internet access.
    - Coverage available wherever there is a cellular signal.
    - Performance depends on phone and cell tower capabilities.
- **Satellite:**
    - Ideal for areas with no other internet connectivity.
    - Requires a clear line of sight to the satellite.
- **Dial-up Telephone:**
    - Inexpensive option using any phone line and a modem.
    - Low bandwidth limits large data transfers.
    - Suitable for basic mobile access during travel.
### 1.5.3 Businesses Internet Connections
![[Pasted image 20240303114342.png]]
- **Dedicated Leased Line:**
    - Reserved circuits within the service provider’s network.
    - Connects geographically separated offices for private voice and data networking.
    - Rented at a monthly or yearly rate.
- **Metro Ethernet:**
    - Also known as Ethernet WAN.
    - Extends LAN access technology into the WAN.
    - Utilizes Ethernet, a LAN technology.
- **Business DSL:**
    - Available in various formats.
    - Symmetric Digital Subscriber Line (SDSL) is a popular choice.
    - Provides high-speed uploads and downloads.
- **Satellite:**
    - Offers a connection in areas where wired solutions are not available.
    - Useful for overcoming limitations in remote or inaccessible locations.
### 1.5.4 The Converging Network
**Traditional Separate Networks**
![[Pasted image 20240303114524.png]]
**Converged Networks**
- Converged data networks carry multiple services on one network.
![[Pasted image 20240303114551.png]]
## 1.6 Reliable Networks
### 1.6.1 Network Architecture
- **Fault Tolerance:**
    - Ensures network resilience against failures through redundancy and backup mechanisms.
- **Scalability:**
    - Enables the network to handle growth and increased demand without performance degradation.
- **Quality of Service (QoS):**
    - Maintains consistent performance by prioritizing critical applications and optimizing resource usage.
- **Security:**
    - Safeguards data, devices, and infrastructure from unauthorized access and potential threats, ensuring confidentiality and integrity.
### 1.6.2 Fault Tolerance
- **Fault Tolerant Network:**
    - Limits affected devices during failures.
    - Facilitates quick recovery from failures.
    - Depends on multiple paths between source and destination.
- **Redundancy through Packet Switching:**
    - Splits traffic into packets for shared network routing.
    - Each packet contains addressing information.
    - Routers dynamically switch packets, allowing different paths for a single message.
    - Users remain unaware and unaffected by dynamic route changes during failures.
![[Pasted image 20240303115430.png]]
### 1.6.3 Scalability
**Scalable Network:**
- Expands rapidly to accommodate new users and applications.
- Maintains performance for existing users accessing services.
- Addition of new networks illustrated in the figure.
- Relies on accepted standards and protocols.
- Allows software and hardware vendors to enhance products and services without redesigning network rules.
![[Pasted image 20240303115509.png]]
### 1.6.4 Quality of Service
- **QoS Importance:**
    - Vital for network service quality.
    - Crucial for voice, video expectations.
- **Congestion:**
    - Bandwidth demand exeeds capacity.
    - Measured in bps.
- **Bandwidth Impact:**
    - Determines data transmission.
    - Overuse leads to congestion.
- **Packet Handling:**
    - Hold in memory during congestion.
    - Wait for available resources.
- **QoS Role:**
    - Manages congestion.
    - Ensures reliable content delivery.
- **Traffic Priority:**
    - Prioritize time-sensitive (voice).
    - Type, not content, matters.
- **Example Scenario:**
    - Illustration of one user requesting a web page and another on a phone call.
    - QoS policies enable routers to manage and prioritize data and voice traffic during congestion.
![[Pasted image 20240303164527.png]]
### 1.6.5 Network Security
- **Network Security Concerns:**
    - Infrastructure security.
    - Information security.
- **Infrastructure Security:**
    - Physically secure devices.
    - Prevent unauthorized access to management software.
- **Network Topology:**
    - PCs, IP phones, switch, router.
    - Software and hardware security measures.
- **Internet Security:**
    - Protect from unauthorized access.
    - Utilize login and password credentials.
- **Information Protection:**
    - Secure transmitted packet data.
    - Safeguard data on network devices.
- **Network Security Goals:**
    - Confidentiality: Authorized data access.
    - Integrity: Unaltered data transmission.
    - Availability: Timely and reliable data access.
![[Pasted image 20240303164856.png]]
## 1.7 Network Trends
### 1.7.1 Recent Trends
- Bring your own device (BYOD)
- Online collaboration
- Video communications
- Cloud computing
### 1.7.2 Bring Your Own Device (BYOD)
- Global trend
	- "Any device, any content, any manner"
	- Shift in device usage and connectivity
- User personal tools on business networks
### 1.7.3 Online Collaboration 
- Connect to network to collaborate with one another
- Joint projects
- E.g.: Cisco WebEx
### 1.7.4 Video Communications
- Video calls
	- Require internet connection
	- Powerful tool for communicating
### 1.7.5 Video - Cisco Webex for Huddles
nothing important
### 1.7.6 Cloud Computing
- Basics
	- Data access and storage over the internet
	- Applications accessible via the cloud
- Business Advantages:
	- Extends IT capabilities without infrastructure investment
	- On-demand services, globally accessible
- Data Centers Role
	- Facilities for computer systems
	- Vary in size
- Cloud Adoption Strategies
	- Large organizations use private data centers
	- Smaller ones lease from cloud providers
- Security Measures
	- Cloud providers store data in distributed centers
	- Enhances reliability, fault tolerance and security
- Cloud Types
	- **Public Clouds:**
		- General population access, pay-per-use
	- **Private Clouds:**
		- Exclusive for specific organizations, costly to set up
	- **Hybrid Clouds:**
		- Combining public and private
	- **Community Clouds:**
		- Exclusive use by specific entities, tailored to common needs
### 1.7.7 Technology Trends in the Home
- Impact of Networking Trends:
    - Changes in communication at work, school, and home.
- Emerging Home Trend:
    - Smart home technology.
- Smart Home Integration:
    - Everyday appliances connected.
    - Enables automation and smart functionalities.
- Example Scenario:
    - Program a smart oven remotely.
    - Sync with calendar for optimal cooking times.
    - Adjusts based on schedule changes.
- Remote Control:
    - Smartphone or tablet connection.
    - Direct adjustments to smart appliances.
- Alerts and Notifications:
    - Oven sends alerts when food is ready.
    - Notifications to specified recipients.
- Expanding Scope:
    - Smart technology in every room.
    - Development driven by home networking and high-speed internet expansion.
### 1.7.8 Powerline Networking
> Use existing electrical wiring to connect devices

- Home Setup:
    - Open floorplan.
    - Three PLEK400 4-port powerline adapters in different outlets.
- Adapter Features:
    - Each adapter connects to devices (desktops, TVs).
    - Wired connections between adapters.
- Components:
    - PLEK400 4-Port Powerline Adapter.
    - Wireless-N Router.
    - PLE400PLSK400 4-Port Powerline Adapter.
- Powerline Connection:
    - Devices connect to the LAN via electrical outlets.
    - No need for additional data cables.
- Data Transmission:
    - Information sent through electrical wiring.
    - Uses specific frequencies.
- Use Cases:
    - Useful where wireless signals can't reach all devices.
    - Not a substitute for dedicated cabling but an alternative when not possible or effective.
![[Pasted image 20240303171922.png]]
### 1.7.9 Wireless Broadband
- Wireless Internet in Remote Areas:
    - Cable and DSL unavailable.
    - Wireless serves as an alternative.
- Wireless Internet Service Provider (WISP):
    - Connects subscribers using wireless tech.
    - Common in rural areas without DSL or cable.
- WISP Infrastructure:
    - Antenna on elevated structures.
    - Subscriber's roof-mounted dish or antenna.
- Connection Setup:
    - Similar to DSL or cable for home users.
    - Main difference: Wireless connection instead of a physical cable.
- Wireless Broadband Service:
    - Alternative for homes, small businesses.
    - Utilizes cellular technology like smartphones.
- Home Setup:
    - Antenna outside for wireless or wired connectivity.
    - Competing with DSL and cable services in many areas.
## Network Security