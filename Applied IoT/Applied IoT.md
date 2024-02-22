# Week 1
## The Big Picture - part 1...
![[Pasted image 20240212110617.png]]
## The Big Picture - part 2...
![[Pasted image 20240212110658.png]]
## [MQTT](https://nl.wikipedia.org/wiki/MQTT)
- Client - Server (broker)
- TCP
	- 1883 (unsecure)
	- 8883 (secure) - [TLS](https://nl.wikipedia.org/wiki/Transport_Layer_Security)
- Topic en subtopics
	- Case sensitive
	- Must not start with '/'
	- Good practice: 
		- Beperk levels
		- Korte topics
		- Geen forward \
		- Geen speciale characters
	- Bv.:
		- AccessControl
			- AccessContol/MAC
		- House 
			- House/LivingRoom/Bulb1
			- House/+/Bulb1
- Subscribe op topic
	- Altijd met uniek client ID
- Publish van message op topic
	- Plain text
	- Binary string
	- JSON
# Week 2
## ESP32
- SoC low cost IoT device
	- System on Chip
- It's created and developed by Esprissif Systems
- It is a microprocessor with built-in Wi-Fi, Radio Frequency and Bluetooth
- It achieves ultra-low power consumption
### ESP32 Break-out board
- Why?
	- Cheap
	- Micropython
	- Wi-Fi, Radio Frequency and bluetooth
	- Ultra-low power consumption
### Power Supply
- There are three mutually exclusive ways to provide power to the board
	- Micro USB port
	- 5V/Gnd header pins
	- 3V3/GND header pins
### GPIO Pins
- All GPIO pins run at 3.3V
- Lot of versions