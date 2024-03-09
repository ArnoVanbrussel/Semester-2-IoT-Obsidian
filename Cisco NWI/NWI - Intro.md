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
## 1.8 Network Security
### 1.8.1 Security Threats
- Network Security Priority
- In all environments
- Balance between Security and QoS
- Components of network security:
	- Protocols, technologies, devices, tools and techniques
- External threat vectors:
	- Viruses, worms, trojans
	- spyware, adware, zero-day attacks
	- threat actor attacks, DoS
	- Data interception, theft, identity theft
- Internal threats:
	- Common data breaches from internal users
	- Lost/stolen devices, accidental misuse, malicious employees
- Evolving BYOD strategies
	- Increased vulnerability of corporate data
### 1.8.2 Security Solutions
- Layered Security Approach
	- Multiple solutions for diverse threats
	- Redundancy
- Home Network Security Components
	- Antivirus and antispyware for end devices
	- Firewall filtering at point of internet connection
- Corporate Network Security Components
	- Dedicated firewall systems
	- Access control list (ACL)
		- Filters based on IP addresses and applications
		- Enhances control over network traffic
	- Intrusion prevention systems (IPS)
		- Identifies fast-spreading threats
		- Targets zero-day/hour attacks
	- Virtual private networks (VPN)
		- Provides secure remote access
		- Essential for remote workers
- Advanced Firewall Capabilities
	- Used in larger networks for granular filtering
	- Provides more sophisticated protection
- Security adaptability
	- Balances security with user expectations
- Network Security Study
	- Understanding switching and routing infrastructure
	- Foundation for addressing threats and implementing mitigation techniques
# 2 Basic Switch and End Device Configuration
## 2.1 Cisco IOS Access
### 2.1.1 Operating Systems 
![[Pasted image 20240304094620.png]]
- **Operating System Components:**
    - **Kernel:** Manages communication between hardware and software, allocates resources to meet software needs.
    - **Shell:** User interface facilitating interaction with the computer, accepts commands via CLI or GUI.
    - **Hardware:** Physical components of the computer, including electronics.
- **CLI Interaction:**
    - **Definition:** Text-based interface allowing users to input commands directly at a command prompt.
    - **Execution:** System processes commands, providing textual output.
    - **Knowledge Requirement:** Users need familiarity with command structures for effective interaction.
```
analyst@secOps ~]$ ls
Desktop Downloads 
lab.support.files second_drive 
[analyst@secOps ~]$
```
- **GUI Interaction:**
    - **Definition:** Graphical User Interface enabling user interaction through visual elements.
    - **Execution:** Users interact with the system through graphical elements instead of command inputs.
    - **Ease of Use:** GUIs generally have a lower learning curve compared to CLIs but may have higher overhead.
### 2.1.2 GUI
- **GUI Overview:**
    - Examples: Windows, macOS, Linux KDE, Apple iOS, Android.
    - Interface: Utilizes graphical icons, menus, and windows for user interaction.
    - User-Friendly: Requires less knowledge of underlying command structure, making it accessible to most users.
- **GUI Limitations:**
    - May not offer all features available with CLI.
    - Prone to failures, crashes, or operational deviations.
- **CLI Preference for Network Devices:**
    - Network devices are accessed through CLI for stability and lower resource intensity.
- **Cisco Internetwork Operating System (IOS):**
    - Family of network operating systems used on Cisco devices.
    - Commonly found on routers and switches, irrespective of size or type.
    - Variants: IOS XE, IOS XR, and NX-OS.
- **Home Routers Operating System:**
    - Typically referred to as firmware.
    - Configuration often done through web browser-based GUI.
    - Differs from network devices where CLI is favored for stability and efficiency.
### 2.1.3 Purpose of an OS
- **PC Operating System (GUI):**
    - Enables users to:
        - Use a mouse for selections and program execution.
        - Enter text and text-based commands.
        - View output on a monitor.
- **Network Operating System (CLI):**
    - In the case of Cisco IOS on switches or routers:
        - Allows network technicians to:
            - Use a keyboard for CLI-based network programs.
            - Enter text and text-based commands.
            - View output on a monitor.
- **Cisco IOS Versions:**
    - Cisco networking devices operate on specific IOS versions.
    - IOS version depends on the device type and required features.
- **Default and Upgrading:**
    - All devices come with a default IOS and feature set.
    - Possibility to upgrade the IOS version or feature set for additional capabilities.
### 2.1.4 Access Methods
- **Default Behavior of a Switch:**
    - Forwards traffic by default.
    - No explicit configuration needed for basic communication between connected hosts.
- **Configuration and Security:**
    - Despite default behavior, all switches should be configured and secured for optimal performance and safety.
- **Methods for Configuration:**
    - **Console:**
        - Physical management port for out-of-band access.
        - Used for device maintenance, requires a console cable and terminal emulation software.
    - **Secure Shell (SSH):**
        - In-band method for secure CLI connection over the network.
        - Requires active networking services and configured interface.
        - Encrypted connection recommended for remote access.
    - **Telnet:**
        - Insecure, in-band method for remote CLI session.
        - No encryption, suitable only for lab environments.
        - Cisco IOS includes Telnet server and client, but SSH is preferred for security.
- **Additional Note:**
    - Some devices, like routers, may support a legacy auxiliary port.
    - AUX port used for out-of-band CLI sessions, similar to a console connection.
    - Does not require configured networking services, historically used for remote access via modem and telephone connection.
## 2.2 IOS Navigation
### 2.2.1 Primary Command Modes

**User Exec Mode:**
- Limited capabilities for basic operations.
- Allows only a set of basic monitoring commands.
- Does not permit commands that might change the device configuration.
- Often referred to as "view-only" mode.
- Identified by CLI prompt ending with the > symbol.
- Default Device Prompt:
    - Switch>
    - Router>

**Privileged Exec Mode:**
- Provides access to all commands and features.
- Enables the execution of monitoring, configuration, and management commands.
- Required for accessing higher configuration modes like global configuration mode.
- Identified by CLI prompt ending with the # symbol.
- Default Device Prompt:
    - Switch#
    - Router#

### 2.2.2 Configuration Mode and Subconfiguration Modes

**Global Configuration Mode:**
- Commonly referred to as global config mode.
- CLI configuration changes made here affect the entire device.
- Identified by a prompt ending with (config)# after the device name.
- Example prompt: Switch(config)#

**Subconfiguration Modes:**
- Accessed from global config mode.
- Each mode allows configuration of a specific part or function of the IOS device.
- Two common subconfiguration modes:
    - Line Configuration Mode:
        - Used for configuring console, SSH, Telnet, or AUX access.
        - Identified by the prompt ending with (config-line)# after the device name.
        - Example prompt: Switch(config-line)#
    - Interface Configuration Mode:
        - Used for configuring a switch port or router network interface.
        - Identified by the prompt ending with (config-if)# after the device name.
        - Example prompt: Switch(config-if)#

**CLI Prompt Identification:**
- The prompt is unique to each configuration mode.
- Every prompt begins with the device name, followed by an indication of the mode.
- Example default prompts:
    - Global Configuration Mode: Switch(config)#
    - Line Configuration Mode: Switch(config-line)#
    - Interface Configuration Mode: Switch(config-if)#

### 2.2.3 [2.2.3 Video - IOS CLI Primary Command Modes](https://contenthub.netacad.com/itn-dl/2.2.3)
### 2.2.4 Navigate Between IOS Modes

**User EXEC Mode to Privileged EXEC Mode:**
- Move from user EXEC mode to privileged EXEC mode using the `enable` command.
- Return to user EXEC mode from privileged EXEC mode using the `disable` command.
- Note: Privileged EXEC mode is sometimes referred to as enable mode.

**Global Configuration Mode:**
- Move from privileged EXEC mode to global configuration mode using the `configure terminal` command.
- Return to privileged EXEC mode from global configuration mode using the `exit` command.

**Subconfiguration Modes:**
- To enter line subconfiguration mode, use the `line` command followed by the management line type and number.
- Use the `exit` command to leave a subconfiguration mode and return to global configuration mode.

**Exiting Subconfiguration Modes:**
- To move from any subconfiguration mode to the mode one step above it, use the `exit` command.
- To move from any subconfiguration mode directly to privileged EXEC mode, use the `end` command or Ctrl+Z.

**Moving Between Subconfiguration Modes:**
- Move directly from one subconfiguration mode to another (e.g., from line configuration mode to interface configuration mode).

Example:
```
Switch(config)# line console 0
Switch(config-line)# exit
Switch(config)#

Switch(config-line)# end
Switch#

```

**Interface Subconfiguration Mode:**
- After selecting an interface, the command prompt changes to indicate the specific interface subconfiguration mode.

Example:
```
Switch(config-line)# interface FastEthernet 0/1
Switch(config-if)#
```

### 2.2.5 [2.2.5 Video - Navigate Between IOS Modes](https://contenthub.netacad.com/itn-dl/2.2.5)
## 2.3 The Command Structure
### 2.3.1 Basic IOS Command Structure
![[Pasted image 20240304100743.png]]
- **Importance of Command Structure:**
    - Understanding the basic IOS command structure is crucial for device configuration using the CLI.
- **Command Syntax:**
    - Each IOS command has a specific syntax.
    - Syntax includes the command itself, followed by appropriate keywords and arguments.
- **General Syntax Diagram:**
    - The general syntax for a switch command is prompt, command, space, and keyword(s) or argument(s).
- **Examples:**
    - Example 1: `Switch>show ip protocols`
        - Prompt: Switch>
        - Command: show
        - Keywords: ip protocols
    - Example 2: `Switch>ping 192.168.10.5`
        - Prompt: Switch>
        - Command: ping
        - Argument: 192.168.10.5
- **Keyword vs. Argument:**
    - Keyword: A specific parameter defined in the operating system (e.g., ip protocols).
    - Argument: Not predefined; a value or variable defined by the user (e.g., 192.168.10.5).
- **Executing Commands:**
    - After entering a complete command, including keywords and arguments, press Enter to submit the command to the command interpreter.
### 2.3.2 IOS Command Syntax Check
**Conventions:**
- **Boldface Text:**
    - Indicates commands and keywords entered literally as shown.
- **Italic Text:**
    - Indicates arguments for which users provide values.
- **Square Brackets `[x]`:**
    - Indicate an optional element (keyword or argument).
- **Braces {x}:**
    - Indicate a required element (keyword or argument).
- **Choice within Optional Element `[x {y | z }]`:**
    - Braces and vertical lines within square brackets indicate a required choice within an optional element.

**Example Syntax:**
- The syntax for the `description` command is `description string`.
    - "string" is an argument provided by the user.
    - Used to identify the purpose of an interface.

**Examples:**
1. `ping ip-address`
    - Command: ping
    - Argument: ip-address (user-defined)
    - Example: `ping 10.10.10.5`
2. `traceroute ip-address`
    - Command: traceroute
    - Argument: ip-address (user-defined)
    - Example: `traceroute 192.168.254.254`

**Complex Command Example:**
- If a command is complex with multiple arguments, it may be represented like:
    - `Switch(config-if)# switchport port-security aging { static | time time | type {absolute | inactivity}}`

**Additional Information:**
- The Cisco IOS Command Reference is the ultimate source for detailed information on a specific IOS command.
### 2.3.3 IOS Help Features
**Context-Sensitive Help:**
- Enables quick access to information about available commands, their starting characters, and associated arguments/keywords.
- Helps answer questions like:
    - Which commands are available in each command mode?
    - What commands start with specific characters or groups?
    - Which arguments and keywords are available for particular commands?
- Accessed by entering a question mark, `?`, at the CLI.

**Command Syntax Check:**
- Verifies the validity of a command entered by the user.
- The command line interpreter evaluates the command from left to right.
- If the interpreter understands the command, the action is executed, and the CLI returns to the appropriate prompt.
- If the interpreter cannot understand the command, it provides feedback describing what is wrong with the command.

These help features are valuable for users to navigate and use the Cisco IOS CLI effectively. The context-sensitive help provides quick reference information, while the command syntax check ensures the accuracy and validity of the entered commands.

### 2.3.4 [2.3.4 Video - Context Sensitive Help and Command Syntax Check](https://contenthub.netacad.com/itn-dl/2.3.4)

### 2.3.5 Hot Keys and Shortcuts

**Command Abbreviation:**
- Commands and keywords can be abbreviated to the minimum number of characters needed for a unique selection.
    - Example: `configure` can be shortened to `conf`, but `con` may not work if multiple commands start with "con."

**Keystrokes for Command Line Editing:**

| Keystroke             | Description                                                                      |
| --------------------- | -------------------------------------------------------------------------------- |
| Tab                   | Completes a partial command name entry.                                          |
| Backspace             | Erases the character to the left of the cursor.                                  |
| Ctrl+D                | Erases the character at the cursor.                                              |
| Ctrl+K                | Erases all characters from the cursor to the end of the command line.            |
| Esc D                 | Erases all characters from the cursor to the end of the word.                    |
| Ctrl+U or Ctrl+X      | Erases all characters from the cursor back to the beginning of the command line. |
| Ctrl+W                | Erases the word to the left of the cursor.                                       |
| Ctrl+A                | Moves the cursor to the beginning of the line.                                   |
| Left Arrow or Ctrl+B  | Moves the cursor one character to the left.                                      |
| Esc B                 | Moves the cursor back one word to the left.                                      |
| Esc F                 | Moves the cursor forward one word to the right.                                  |
| Right Arrow or Ctrl+F | Moves the cursor one character to the right.                                     |
| Ctrl+E                | Moves the cursor to the end of the command line.                                 |
| Up Arrow or Ctrl+P    | Recalls the previous command in the history buffer.                              |
| Down Arrow or Ctrl+N  | Goes to the next line in the history buffer.                                     |
| Ctrl+R or Ctrl+I or   | Redisplays the system prompt and command line after a                            |
| Ctrl+L                | console message is received.                                                     |
**Navigation during --More-- Prompt:**

| Keystroke             | Description                                           |
|-----------------------|-------------------------------------------------------|
| Enter Key             | Displays the next line.                               |
| Space Bar             | Displays the next screen.                             |
| Any other key except "y"| Ends the display, returning to the previous prompt.   |


**Exiting Configuration Mode:**

| Keystroke    | Description                                                                    |
| ------------ | ------------------------------------------------------------------------------ |
| Ctrl-C       | Ends configuration mode and returns to privileged EXEC mode.                   |
| Ctrl-Z       | Ends configuration mode and returns to privileged EXEC mode.                   |
| Ctrl-Shift-6 | All-purpose break sequence used to abort DNS lookups, traceroutes, pings, etc. |
### 2.3.6 [Video - Hot Keys and Shortcuts](https://contenthub.netacad.com/itn-dl/2.3.6)

### 2.3.7 [Packet Tracer - Navigate the IOS](![[2.3.7-packet-tracer---navigate-the-ios.pka]])
## 2.4 Basic Device Configuration
### 2.4.1 Device Names
- **Naming Guidelines:**
    - Start with a letter.
    - Avoid spaces, use only letters, digits, and dashes.
    - End with a letter or digit.
    - Keep it under 64 characters.
    - Preserve capitalization and lowercase.
- **Naming Convention Example:**
    - Include location and purpose.
    - Maintain a consistent format.
- **Documentation:**
    - Update documentation for device changes.
    - Identify devices by location, purpose, and address.
- **CLI Configuration:**
    - Access privileged EXEC mode: `Switch#`
    - Enter global configuration mode: `Switch# configure terminal`
    - Change hostname: `Sw-Floor-1(config)# hostname Sw-Floor-1`
    - Verify: `Sw-Floor-1(config)#`
    - Return to default: `Sw-Floor-1(config)# no hostname`
- **SSH Access:**
    - Enhances remote access identification via SSH.
### 2.4.2 Password Guidelines
- **Security Concerns:**
    - Weak passwords are a major security risk.
    - Configure passwords for limited admin access.
- **Cisco IOS Configuration:**
    - Use hierarchical mode passwords for diverse access.
- **Access Limitation:**
    - Secure privileged EXEC, user EXEC, and Telnet access.
    - Encrypt passwords, provide legal notifications.
- **Password Strength:**
    - Opt for strong, diverse passwords.
    - Avoid common words, use varied characters.
- **Password Generation:**
    - Use online generators with custom parameters.
- **Lab Passwords:**
    - "cisco" or "class" in labs are for convenience, not for production.
### 2.4.3 Configure Passwords
- **Securing User EXEC Mode:**
    - Access user EXEC mode via console using `line console 0`.
    - Set a password with `password` and enable with `login`.
    - Example:
```
configure terminal
line console 0
password cisco
login
end
```
- **Privileged EXEC Mode:**
    - For full device access, secure privileged EXEC with `enable secret`.
    - Example:
```
configure terminal
enable secret class
exit
```
- **Virtual Terminal (VTY) Lines:**
    - Enable remote access via Telnet or SSH using `line vty 0 15`.
    - Set a password with `password` and enable with `login`.
    - Example:
```
configure terminal
line vty 0 15
password cisco
login
end
```
### 2.4.4 Encrypt Passwords
**Encrypting Passwords:**
- Use `service password-encryption` to encrypt plaintext passwords.
- Example:
```
configure terminal
service password-encryption
```
- **Encryption Details:**
    - Weak encryption applied to unencrypted passwords.
    - Applies to passwords in the configuration file, not during network transmission.
    - Prevents unauthorized access to passwords in the configuration file.
- **Verification:**
    - Confirm encryption with `show running-config`.
    - Example:
```
end
show running-config
```
- **Output Example:**
```
line con 0
password 7 094F471A1A0A
login line vty 0 4
	password 7 094F471A1A0A
	login
line vty 5 15
	password 7 094F471A1A0A 
	login
```
### 2.4.5 Banner Messages
- **Adding a Banner:**
    - Enhance security by adding a banner to declare authorized access.
    - Use `banner motd # message #` in global config mode.
- **Banner Details:**
    - The delimiting character (#) surrounds the message.
    - Helps in legal processes and user notifications.
- **Configuration Example:**
    `configure terminal banner motd #Authorized Access Only#`
- **Effect:**
    - The configured banner will be displayed on every access attempt until removed.
### 2.4.6 [Video - Secure Administrative Access to a Switch](https://contenthub.netacad.com/itn-dl/2.4.6)
### 2.4.7 Syntax Checker - Basic Device Configuration
```
# Enter global configuration mode.
	Switch#configure terminal

# Name the switch “Sw-Floor-1”.
	Switch(config)#hostname Sw-Floor-1

# Secure user EXEC mode access by entering **line console 0**, assign the password **cisco**, enable login, and return to the global configuration mode using **exit.**
	Sw-Floor-1(config)#line console 0
	Sw-Floor-1(config-line)#password cisco
	Sw-Floor-1(config-line)#login
	Sw-Floor-1(config-line)#exit

# Secure privileged EXEC mode access using the password **class.**
	Sw-Floor-1(config)#enable secret class

# Secure the VTY lines 0 through 15, assign the password **cisco**, enable login, and return to the global configuration mode using **exit.**
	Sw-Floor-1(config)#line vty 0 15
	Sw-Floor-1(config-line)#password cisco
	Sw-Floor-1(config-line)#login
	Sw-Floor-1(config-line)#exit

# Encrypt all plaintext passwords.
	Sw-Floor-1(config)#service password-encryption

# Create a banner message using the “**#**” symbol as the delimiter. The banner should display exactly: **Warning! Authorized access only!**
	Sw-Floor-1(config)#banner motd #Warning! Authorized access only!#
```
## 2.5 Save Configurations
### 2.5.1 Configuration Files
- **Configuration Files:**
    - `startup-config`: Stored in NVRAM, contains commands used upon device startup or reboot.
    - `running-config`: Stored in RAM, reflects the current configuration, and is volatile.
- **Viewing Configuration:**
    - `show running-config`: Displays the current configuration stored in RAM.
    - `show startup-config`: Used to view the startup configuration file.
- **Memory Types:**
    - NVRAM (Non-Volatile RAM): Persists through power cycles, holds the startup configuration.
    - RAM (Random Access Memory): Volatile memory, loses content on device restart.
- **Saving Configurations:**
    - `copy running-config startup-config`: Command to save changes made to the running configuration to the startup configuration file.
- **Preventing Data Loss:**
    - If power is lost or device is restarted without saving, configuration changes will be lost.
- **Example Output:**
    - `Sw-Floor-1# show running-config`: Displays the current configuration in RAM.
    - `Sw-Floor-1# show startup-config`: Displays the startup configuration file.
### 2.5.2 Alter the Running Configuration
- **Restoring Previous Configuration:**
    - If changes in running config are undesirable and not saved, individual commands can be removed.
    - Alternatively, use `reload` privileged EXEC command to restore the startup-config.
- **Downtime Concerns:**
    - Reloading the device using `reload` causes brief network downtime.
    - During the reload, the device detects unsaved changes and prompts to save or discard.
- **Prompt for Changes on Reload:**
    - When `reload` is initiated, IOS prompts to save changes in running config.
    - Enter 'n' or 'no' to discard changes if desired.
- **Clearing All Configurations:**
    - To remove undesired changes saved to startup config, use `erase startup-config` command.
    - Confirmation prompt appears; press Enter to accept.
- **Reloading After Clearing Startup Config:**
    - After erasing startup config, reload the device to remove current running config from RAM.
    - The switch will load the default startup config shipped with the device on reload.
### 2.5.3 [Video - Alter the Running Configuration](https://contenthub.netacad.com/itn-dl/2.5.3)
### 2.5.4 Capture Configuration to a Text File
- **Saving Configuration to Text File:**
    - **Step 1:** Open terminal emulation software (e.g., PuTTY or Tera Term) connected to the switch.
    - **Step 2:** Enable logging, specify a name and file location (e.g., MySwitchLogs).
    - **Step 3:** Execute `show running-config` or `show startup-config` at privileged EXEC prompt. Output is saved to the specified file.
        `Sw-Floor-1# show running-config Building configuration... (output omitted)`
    - **Step 4:** Disable logging to end the session, choosing the 'None' session logging option.
- **Using Saved Configuration File:**
    - **To Restore Configuration:**
        - **Step 1:** Enter global configuration mode on the device.
        - **Step 2:** Copy and paste the text file content into the terminal window connected to the switch.
    - **Result:**
        - The text file commands are applied as CLI commands, becoming the running configuration on the device.
        - Useful for manually configuring a device or restoring a saved configuration.
- **Note:**
    - The saved text file can serve as a record of the current device implementation.
    - Editing may be required before using the file to restore configuration to a device.
## 2.6 Ports and Addresses
### 2.6.1 IP Addresses
- **IP Addresses:**
    - **IPv4:**
        - Represented in dotted decimal notation (four decimal numbers between 0 and 255).
        - Assigned to individual devices for network communication.
        - Example: 192.168.1.10
    - **IPv6:**
        - 128-bit length, written as hexadecimal values, separated by colons.
        - Example: 2001:db8:acad:10::10
- **End Devices:**
    - Devices requiring IP addresses for communication:
        - Computers (workstations, laptops, servers)
        - Network printers
        - VoIP phones
        - Security cameras
        - Smartphones
        - Handheld devices (e.g., wireless barcode scanners)
- **IPv4 Subnetting:**
    - Subnet mask (32-bit) differentiates network and host portions of the IP address.
    - Coupled with IPv4 address, determines device's subnet membership.
    - Example: IP 192.168.1.10, Subnet Mask 255.255.255.0, Default Gateway 192.168.1.1
- **IPv6 Address Format:**
    - 128 bits in length, written as hexadecimal values.
    - Groups of four hexadecimal digits separated by colons.
    - Example: IPv6 Address 2001:db8:acad:10::10, Subnet Prefix Length 64, Default Gateway fe80::1
- **Note:**
    - IP refers to both IPv4 and IPv6 in this context.
    - IPv6 is replacing the more common IPv4 for future internet communication.
### 2.6.2 Interfaces and Ports
- **Network Media Types:**
    - **Twisted-Pair Copper Cables:**
        - Common for Ethernet connections.
        - Varied categories (e.g., Cat5e, Cat6) with different data transmission capabilities.
    - **Fiber-Optic Cables:**
        - Transmit data using light signals.
        - High bandwidth, immune to electromagnetic interference.
    - **Coaxial Cables:**
        - Common for cable television.
        - Suitable for certain network connections.
    - **Wireless:**
        - Utilizes radio waves for communication.
        - Provides flexibility in device mobility.
- **Considerations for Network Media Selection:**
    - **Distance:** Varies based on media type.
    - **Environment:** Different media for different environments (e.g., indoor vs. outdoor).
    - **Data Transmission:** Varies in terms of speed and data capacity.
    - **Cost:** Cost of media and installation may differ.
- **Network Technology:**
    - **Ethernet:**
        - Most common LAN technology.
        - Found on end-user devices, switches, and other networking devices.
- **Switch Virtual Interfaces (SVIs):**
    - **Function:**
        - Allow remote management of Layer 2 switches over IPv4 and IPv6.
        - Created in software; no physical hardware associated.
    - **Default Configuration:**
        - Default SVI: Interface VLAN1.
    - **Note:**
        - Layer 2 switches don't require an IP address for their operations.
        - IP assigned to SVI enables remote access to the switch.
## 2.7 Configure IP Addressing
### 2.7.1 Manual IP Address Configuration for End Devices 
- **Configuring IPv4 Address on Windows:**
    - **Manual Configuration:**
        - Open Control Panel > Network Sharing Center > Change adapter settings.
        - Choose the adapter, right-click, and select Properties.
        - Highlight Internet Protocol Version 4 (TCP/IPv4) and click Properties.
        - Configure IPv4 address, subnet mask, and default gateway.
    - **IPv6 Configuration:**
        - Similar process, using Internet Protocol Version 6 (TCP/IPv6) properties.
    - **DNS Server Addresses:**
        - Represent IPv4 and IPv6 addresses of Domain Name System (DNS) servers.
        - Used for translating IP addresses to domain names.
- **Note:**
    - IPv6 addressing and configuration options mirror those of IPv4.
    - DNS server addresses play a crucial role in domain name resolution.
### 2.7.2 Automatic IP Address Configuration for End Devices
- **DHCP for Automatic IPv4 Configuration:**
    - **Advantages:**
        - Automates IPv4 address configuration for DHCP-enabled end devices.
        - Reduces manual configuration effort and potential misconfigurations.
        - Efficient for networks with numerous users and devices.
- **Manual Configuration Challenges:**
    - **Issues:**
        - Time-consuming for users to manually enter IPv4 address, subnet mask, gateway, and DNS server.
        - High risk of misconfiguration and address duplication.
        - Cumbersome for large organizations with numerous devices.
- **DHCP Configuration on Windows:**
    - **Steps:**
        - Open Control Panel > Network Sharing Center > Change adapter settings.
        - Choose the adapter, right-click, and select Properties.
        - Select "Obtain an IP address automatically" and "Obtain DNS server address automatically."
- **IPv6 Address Allocation:**
    - **Protocols:**
        - DHCPv6 (Dynamic Host Configuration Protocol for IPv6).
        - SLAAC (Stateless Address Autoconfiguration).
- **Note:**
    - IPv6 uses DHCPv6 and SLAAC for dynamic address allocation.
    - Automatic configuration simplifies network setup, especially in large-scale environments.
### 2.7.3 Syntax Checker - Verify Windows PC IP Configuration
``` 
Enter the command to display the IP configuration on a Windows PC.

C:\>ipconfig

Windows IP Configuration  
  
Ethernet adapter Local Area Connection:  
  
Connection-specific DNS Suffix . : cisco.com  
Link-local IPv6 Address . . . . . : fe80::b0ef:ca42:af2c:c6c7%16  
IPv4 Address. . . . . . . . . . . : 192.168.1.10  
Subnet Mask . . . . . . . . . . . : 255.255.255.0  
Default Gateway . . . . . . . . . : 192.168.1.1

You successfully displayed the IP configuration on a Windows PC.
```
### 2.7.4 Switch Virtual Interface Configuration
- Access the switch remotely by configuring an IP address and subnet mask on the Switched Virtual Interface (SVI).
- Use the global configuration mode with the command: `configure terminal`.
- Enter the VLAN 1 interface configuration with: `interface vlan 1`.
- Assign an IPv4 address and subnet mask to the SVI using: `ip address 192.168.1.20 255.255.255.0`.
- Enable the virtual interface with: `no shutdown`.
- Exit the VLAN 1 interface configuration with: `exit`.
- Set the default gateway for the switch with: `ip default-gateway 192.168.1.1`
### 2.7.5 Syntax Checker - Configure a Switch Virtual Interface
```
Switch(config)#interface vlan 1
Switch(config-if)#ip address 192.168.1.20 255.255.255.0
Switch(config-if)#no shutdown
%LINK-5-CHANGED: Interface Vlan1, changed state to up
```
## 2.8 Verify Connectivity
### 2.8.1 [Video Activity - Test the Interface Assignment](https://contenthub.netacad.com/itn-dl/2.8.1)
### 2.8.2 [Video Activity - Test End-to-End Connectivity](https://contenthub.netacad.com/itn-dl/2.8.2)
# 3 Protocols and Models
## 3.1 The Rules
### 3.1.1 [Video - Devices in a Bubble](https://contenthub.netacad.com/itn-dl/3.1.1)
### 3.1.2 Communications Fundamentals
- Networks vary in size, shape, and function, ranging from complex internet-connected devices to simple direct connections between two computers.
- Mere physical connection is insufficient for communication; devices must understand "how" to communicate.
- Communication involves a message source (sender), which can be people or electronic devices needing to convey a message.
- A message destination (receiver) receives and interprets the message from the source.
- The channel serves as the pathway over which the message travels from the source to the destination.
### 3.1.3 Communication Protocols
- Message transmission in both face-to-face and network communication follows rules known as protocols.
- Protocols are specific to the type of communication method, varying between different mediums.
- Rules for personal communication, like a telephone call, differ from those for other mediums, such as sending a letter.
- Similar to personal communication, computer networks employ protocols to govern the process of message transmission.
- The process of sending a letter mirrors aspects of communication within computer networks.
### 3.1.4 Rule Establishment
- Communication relies on rules akin to protocols.
- Proper formatting is crucial for understanding; deviations complicate comprehension.
- Adherence to language and grammar rules enhances clarity.
- Communication protocols must address sender/receiver identification, common language, speed, timing, and acknowledgment.
### 3.1.5 Network Protocol Requirements
- Network protocols
- Source and destination
- Message transmission
- Encoding, formatting, encapsulation
- Message size, timing, delivery options
- Standardized information exchange
### 3.1.6 Message Encoding
- Encoding for network communication depends on the medium.
- Messages are converted to bits by the sending host.
- Bits are then encoded into voltage patterns, light signals, or microwaves.
- The destination host decodes signals to interpret the message.
### 3.1.7 Message Formatting and Encapsulation
- IP acts like an envelope, addressing data packets for network delivery.
- Source and destination identified in IP packets ensure proper delivery.
- IP packets travel across networks like letters through postal services.
### 3.1.8 Message Size
- Long messages split into "frames" for network travel.
- Strict frame size limits vary by network channel.
- Source cuts message to compliant frames with addressing.
- Receiver reassembles frames back to original message.
### 3.1.9 Message Timing
- **Flow control:** Manages data transmission rate, similar to speaking at a pace the receiver can understand.
- **Response timeout:** Sets a waiting time for responses, like deciding to repeat a question if unanswered within an expected timeframe.
- **Access method:** Determines when to send messages, avoiding "collisions" like two people talking over each other.
### 3.1.10 Message Delivery Options
- Network communication offers delivery options:
    - **Unicast:** Delivers to **one** specific device.
    - **Multicast:** Delivers to **multiple** specific devices in a group.
    - **Broadcast:** Delivers to **all** devices on the network.
## 3.2 Protocols
### 3.2.1 Network Protocol Overview
- **Network Communications Protocols:**
    - Enable communication between devices over one or more networks.
    - Examples include IP, Transmission Control Protocol (TCP), and HyperText Transfer Protocol (HTTP).
- **Network Security Protocols:**
    - Secure data by providing authentication, data integrity, and encryption.
    - Examples include Secure Shell (SSH), Secure Sockets Layer (SSL), and Transport Layer Security (TLS).
- **Routing Protocols:**
    - Enable routers to exchange route information and determine the best path to a destination network.
    - Examples include Open Shortest Path First (OSPF) and Border Gateway Protocol (BGP).
- **Service Discovery Protocols:**
    - Used for automatic detection of devices or services.
    - Examples include Dynamic Host Configuration Protocol (DHCP) for IP address allocation and Domain Name System (DNS) for name-to-IP address translation.
### 3.2.2 Network Protocol Functions
1. **Addressing:**
    - IPv4 identifies sender and receiver with source and destination IP addresses.
2. **Reliability:**
    - TCP ensures guaranteed delivery of the message.
3. **Flow Control:**
    - TCP manages efficient data flow between devices.
4. **Sequencing:**
    - TCP labels data segments for correct reassembly at the destination.
5. **Error Detection:**
    - Protocols like Ethernet, IPv4, IPv6, and TCP detect data corruption.
6. **Application Interface:**
    - For web communication, HTTP or HTTPS facilitates process-to-process interaction.
### 3.2.3 Protocol Interaction
- **Hypertext Transfer Protocol (HTTP):**
    - Governs the interaction between a web server and client.
    - Defines the content and formatting of exchanged requests and responses.
    - Implemented by both client and server software as part of the application.
    - Relies on other protocols for message transport.
- **Transmission Control Protocol (TCP):**
    - Manages individual conversations between devices.
    - Ensures reliable delivery of information and handles flow control.
    - Facilitates communication reliability.
- **Internet Protocol (IP):**
    - Responsible for delivering messages from sender to receiver.
    - Used by routers to forward messages across multiple networks.
    - Enables inter-network communication.
- **Ethernet:**
    - Responsible for delivering messages within the same Ethernet local area network (LAN).
    - Facilitates communication between network interface cards (NICs).
## 3.3 Protocol Suites
### 3.3.1 Network Protocol Suites
- Seamless collaboration of inter-related protocols.
- Visualized as a layered stack for interaction.
- Lower layers manage data, provide services.
- Upper layers focus on message content.
- Layered dependencies ensure smooth functionality.
- Similar to OSI or TCP/IP models.
- Goal is seamless protocol integration for an enhanced online experience.
### 3.3.2 Evolution of Protocol Suites
![[Pasted image 20240307095303.png]]
### 3.3.3 TCP/IP Protocol Example
**TCP/IP Protocol Suite:**
- **Application Layer Protocols:** HTTP, DNS, DHCP, FTP
- **Transport Layer Protocols:** TCP, UDP
- **Internet Layer Protocols:** IPv4, IPv6, ICMPv4, ICMPv6
- **Network Access Layer:** No specific TCP/IP protocols
    - **Common LAN Protocols:** Ethernet, WLAN (Wireless LAN)
    - Responsible for delivering IP packets over the physical medium
![[Pasted image 20240307095406.png]]
### 3.3.4 TCP/IP Protocol Suite
![[Pasted image 20240307095453.png]]
- **Application Layer:**
    - **Name System:**
        - DNS (Domain Name System): Translates domain names to IP addresses.
    - **Host Config:**
        - DHCPv4: Dynamically assigns IPv4 addresses.
        - DHCPv6: Dynamically assigns IPv6 addresses.
        - SLAAC: Stateless Address Autoconfiguration for IPv6.
    - **Email:**
        - SMTP: Simple Mail Transfer Protocol.
        - POP3: Post Office Protocol version 3.
        - IMAP: Internet Message Access Protocol.
    - **File Transfer:**
        - FTP: File Transfer Protocol.
        - SFTP: SSH File Transfer Protocol.
        - TFTP: Trivial File Transfer Protocol.
    - **Web and Web Service:**
        - HTTP: Hypertext Transfer Protocol.
        - HTTPS: HTTP Secure.
        - REST: Representational State Transfer.
- **Transport Layer:**
    - **Connection-Oriented:**
        - TCP: Transmission Control Protocol for reliable communication.
    - **Connectionless:**
        - UDP: User Datagram Protocol for faster but unreliable communication.
- **Internet Layer:**
    - **Internet Protocol:**
        - IPv4: Internet Protocol version 4.
        - IPv6: IP version 6.
        - NAT: Network Address Translation.
    - **Messaging:**
        - ICMPv4: Internet Control Message Protocol for IPv4.
        - ICMPv6: ICMP for IPv6.
        - ICMPv6 ND: ICMPv6 Neighbor Discovery.
    - **Routing Protocols:**
        - OSPF: Open Shortest Path First.
        - EIGRP: Enhanced Interior Gateway Routing Protocol.
        - BGP: Border Gateway Protocol.
- **Network Access Layer:**
    - **Address Resolution:**
        - ARP: Address Resolution Protocol.
    - **Data Link Protocols:**
        - Ethernet: Defines rules for wired networks.
        - WLAN: Wireless Local Area Network, defines rules for wireless networks.
## 3.4 Standards Organizations
### 3.4.1 Open Standards
- **Standards in Networking:**
    - Similar to car tires, network components follow standards for compatibility.
    - Open standards ensure fair competition, prevent monopolies, and drive innovation.
- **Wireless Router Example:**
    - Various vendors provide routers with standard protocols (IPv4, IPv6, DHCP, SLAAC, Ethernet, 802.11).
    - Open standards enable cross-platform compatibility (e.g., Apple OS X and Linux) using TCP/IP.
- **Standards Organizations:**
    - Neutral, non-profit entities develop and promote open standards.
    - Maintain an open internet with accessible protocols, fostering collaboration.
    - May adopt proprietary protocols with vendor involvement.
- **Key Impact:**
    - Standards organizations are vital for a cohesive and open networking industry.
### 3.4.2 Internet Standards
- **Internet Standards Organizations:**
    - **Internet Society (ISOC):**
        - Promotes open development and evolution of global internet use.
    - **Internet Architecture Board (IAB):**
        - Manages and develops overall internet standards.
    - **Internet Engineering Task Force (IETF):**
        - Develops, updates, and maintains internet and TCP/IP technologies.
        - Defines protocols through Request for Comments (RFC) documents.
    - **Internet Engineering Steering Group (IESG):**
        - Oversees IETF working groups.
    - **Internet Research Task Force (IRTF):**
        - Focuses on long-term research related to internet and TCP/IP protocols.
- **TCP/IP Standards Organizations:**
    - **Internet Corporation for Assigned Names and Numbers (ICANN):**
        - Based in the United States.
        - Coordinates IP address allocation, domain name management, and protocol identifiers.
    - **Internet Assigned Numbers Authority (IANA):**
        - Oversees IP address allocation, domain name management, and protocol identifiers for ICANN.
### 3.4.3 Electronic and Communications Standards
- **IEEE (Institute of Electrical and Electronics Engineers):**
    - Advances technological innovation and creates standards in various industries.
    - Key networking standards include 802.3 Ethernet and 802.11 WLAN.
- **Electronic Industries Alliance (EIA):**
    - Known for standards related to electrical wiring, connectors, and 19-inch racks for networking equipment.
- **Telecommunications Industry Association (TIA):**
    - Develops communication standards for radio equipment, cellular towers, VoIP devices, satellite communications, and more.
- **ITU-T (International Telecommunications Union-Telecommunication Standardization Sector):**
    - One of the largest and oldest communication standards organizations.
    - Defines standards for video compression, IPTV, broadband communications, such as DSL.
## 3.5 Reference Models
### 3.5.1 The Benefits of Using a Layered Model
- **Layered Model Benefits:**
    - Assists in protocol design with defined information and interfaces.
    - Fosters competition, enabling interoperability among products from different vendors.
    - Prevents changes in one layer from affecting others, ensuring stability.
    - Provides a common language for describing networking functions and capabilities.
- **Layered Models:**
    - **OSI Reference Model:**
        - Application, Presentation, Session, Transport, Network, Data Link, Physical.
        - Associated protocols: HTTP, DNS, DHCP, FTP, TCP, UDP, IPv4, IPv6, ICMPv4, ICMPv6, Ethernet, WLAN, SONET, SDH.
    - **TCP/IP Reference Model:**
        - Application, Transport, Internet, Network Access.
        - Associated protocols: HTTP, DNS, DHCP, FTP, TCP, UDP, IPv4, IPv6, ICMPv4, ICMPv6, Ethernet, WLAN, SONET, SDH.
### 3.5.2 The OSI Reference Model
- **OSI Model Layers:**
    1. **Physical Layer:**
        - Protocols describe mechanical, electrical, and procedural means for bit transmission.
    2. **Data Link Layer:**
        - Protocols describe methods for exchanging data frames over a common media.
    3. **Network Layer:**
        - Provides services to exchange data over the network between identified end devices.
    4. **Transport Layer:**
        - Defines services to segment, transfer, and reassemble data for individual communications.
    5. **Session Layer:**
        - Provides services to organize dialogue and manage data exchange for the presentation layer.
    6. **Presentation Layer:**
        - Provides a common representation of data transferred between application layer services.
    7. **Application Layer:**
        - Contains protocols for process-to-process communications.
- **Note:**
    - The OSI model layers are often referred to by number (Layer 1, Layer 2, etc.) rather than by name.
    - The TCP/IP model layers are typically referred to by name.
### 3.5.3 The TCP/IP Protocol Model
- **TCP/IP Model Layers:**
    1. **Network Access:**
        - Controls hardware devices and media comprising the network.
    2. **Internet:**
        - Determines the best path through the network.
    3. **Transport:**
        - Supports communication between diverse devices across networks.
    4. **Application:**
        - Represents data to the user, includes encoding and dialog control.
- **Additional Information:**
    - The TCP/IP model is also known as the internet model.
    - Serves as both a protocol model and a reference model.
    - Definitions of standards and TCP/IP protocols are discussed in a public forum and defined in publicly available IETF RFCs (Request for Comments).
    - RFCs are authored by networking engineers and reviewed by other IETF members for comments.
### 3.5.4 OSI and TCP/IP Model Comparison
- **TCP/IP and OSI Model Comparison:**
    - **OSI Model Layers (Left) and TCP/IP Model Layers (Right):**
        - **OSI Model:**
            - Application, Presentation, Session, Transport, Network, Data Link, Physical.
        - **TCP/IP Model:**
            - Application, Transport, Internet, Network Access.
- **Model Relationships:**
    - **Similarities:**
        - Transport and network layers align closely between both models.
    - **Differences:**
        - OSI Layers 1 and 2 align with the TCP/IP Network Access layer.
        - The top three OSI layers (5, 6, 7) map to the TCP/IP Application layer.
        - Different ways of relating to layers above and below.
- **Key Correspondences:**
    - **OSI Layer 3 (Network Layer):**
        - Maps directly to the TCP/IP Internet Layer.
        - Describes protocols addressing and routing messages in an internetwork.
    - **OSI Layer 4 (Transport Layer):**
        - Maps directly to the TCP/IP Transport Layer.
        - Describes services providing ordered and reliable data delivery between hosts.
- **Application Layer:**
    - TCP/IP Application Layer includes protocols for specific end-user functionality.
    - OSI Layers 5, 6, and 7 serve as references for application developers and vendors.
- **Common Usage:**
    - Both models are commonly referenced for protocols at various layers.
    - OSI model is often used for lower layers, especially data link and physical, due to their separation.
![[Pasted image 20240309092818.png]]
## 3.6 Data Encapsulation
### 3.6.1 Segmenting Messages
- **Issues with Unsegmented Data:**
    - Delays: Large, unbroken streams lead to significant delays.
    - Risk of Loss: Complete data loss on network failure.
- **Segmentation Process:**
    - Division: Data is segmented into smaller packets.
    - TCP/IP Usage: Transmission as individual IP packets.
- **Multiplexing Benefits:**
    - Interleaved Conversations: Multiplexing allows for multiple conversations concurrently.
- **Segmentation Advantages:**
    - Speed Boost: Enables efficient transmission of large data.
    - Efficiency: Only retransmit failed segments, minimizing data resend.
### 3.6.2 Sequencing
- **Segmentation and Multiplexing Challenge:**
    - Complexity Added: Process becomes more complex with segmentation and multiplexing.
    - Analogy: Sending a 100-page letter in individual envelopes, each requiring separate addressing.
- **Out-of-Order Arrival Issue:**
    - Envelope Analogy: 100 envelopes may arrive out-of-order.
    - Solution: Envelopes need sequence numbers for proper reassembly.
- **Network Communication Process:**
    - Similarity: Each message segment undergoes a process for correct destination and reassembly.
    - TCP's Role: Responsible for sequencing individual segments.
![[Pasted image 20240309093303.png]]
### 3.6.3 Protocol Data Units
- **  
    Encapsulation Process:**
    
    - Definition: Protocol information added at each level as data passes down the protocol stack.
    - Result: Formation of a Protocol Data Unit (PDU) at each layer.
- **PDU Naming Convention:**
    
    - Terminology: PDUs named according to TCP/IP suite protocols.
    - Example: UDP PDU called a datagram; IP packets sometimes referred to as IP datagrams.
- **Encapsulation Steps (Based on TCP/IP Suite):**
    
    - Application Layer: Email data divided into smaller chunks (Data PDU).
    - Transport Layer: Adds a transport header, forming a Segment (Transport layer PDU).
    - Network Layer: Adds a network header, creating a Packet (Network layer PDU).
    - Data Link Layer: Adds a frame header and trailer, resulting in a Frame (Data Link layer PDU).
    - Physical Layer: Represents the Frame as a stream of bits for transmission over the medium (Bits PDU).
- **Illustrative Figure:**
    
    - Visual Representation: Person at a computer sending email data.
    - Data Flow: Email data encapsulated into new PDUs at each layer.
    - Transmission: Bits representing the Frame before reaching a router connected to the cloud.
- **PDU Types:**
    
    - Data: General term for the PDU at the application layer.
    - Segment: Transport layer PDU.
    - Packet: Network layer PDU.
    - Frame: Data Link layer PDU.
    - Bits: Physical layer PDU used for physical data transmission over the medium.
- **Note on Transport Header:**
    
    - TCP vs. UDP: If the Transport header is TCP, it is a Segment; if UDP, it is a Datagram.
![[Pasted image 20240309093505.png]]