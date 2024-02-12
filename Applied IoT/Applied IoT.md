# Week 1
## The Big Picture - part 1...
![[Pasted image 20240212110617.png]]
## The Big Picture - part 2...
![[Pasted image 20240212110658.png]]
## MQTT
- Client - Server (broker)
- TCP
	- 1883 (unsecure)
	- 8883 (secure) - [TLS](https://nl.wikipedia.org/wiki/Transport_Layer_Security)
- Topic en subtopics
	- Case sensitive
	- Must not start with '/'
	- Good practice: beperk levels
	- Bv.:
		- AccessControl
			- AccessContol/MAC
		- House 
			- House/LivingRoom/Bulb1
			- House/+/Bulb1
- Subscribe op topic
- Publish van message op topic
	- Plain text
	- Binary string
	- JSON