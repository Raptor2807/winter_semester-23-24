## Why is most security research focused on Android?
-  1: It is completely open source ![[Pasted image 20231110111023.png]]
- 2 : The market : the android holds nearly 73.48% of all smartphones' market share.
### [[Smartphone Securtiy]]
#### Threat Models
- 1 : Hardware Based Attacks
	- *Malicious charger/ Docking Station*
		- Micro-computers are hidden in charging station (Raspberry pi or Beagle-board)
		- When user plugs in their phone, the software on the micro-computer attacks and compromises the phone's OS and achieves root privileges.
		- Android : USB - Potential Attack Surface
			- Zero day exploits : error in file system driver or media manager when mounting external hard drive
			- AT commands: Exposed [[USB CDC ACM interface]] (USB Modem Interface); allows bricking/resetting phones, making calls, enabling ADB debugging, Reading file system, unlocking the phone and sending touch events and many more.
	- Rogue Base Station
		- Fake base station can be easily built.
			- OpenBTS/OpenBSC software
			- Dedicated hardware($1000) or a Motorola C123
		- No mutual authentication between phone and cellular network
			- Network does not have to authenticate to phone
		- Fallback to GPRS/EDGE when UMTS/HSPA unavailable
		- MITM attacks
			- in this attacker's base station is placed in between the phone and real base station.
			- IMSI (International Mobile Subscriber Identity) catcher, downgrade encryption, redirect/alter traffic,......
- 2: Runtime Attacks
	- *Baseband Attacks*
		- The baseband means having control over the baseband side of a Phone which allows an adversary to perform a variety of interesting attacks related to the “phone” part of a device, such as monitoring incoming and outgoing calls, performing calls, sending and intercepting short messages, intercepting IP traffic, etc
		- The baseband OS is often less hardened against software exploits
		- Fuzzing the baseband with specially crafted SMS from a rogue base station revealed software vulnerabilities.
			- Compromise the baseband OS
- 3: Privacy Violations and Malware
	- Malware
		- Malware authors identified smartphone platforms early on as valuable target
		- Malware attack vectors adapt to platform evolution
			- For example : premium SMS decreased; UI deception/A11y/ adminAPI/app-plugins added; from root to kernel exploits; pre-installed malware apps
			- “Potentially Harmful Application” (PHA) classification by Google (https://developers.google.com/android/play-protect/phacategories)
			- Backdoors, Billing fraud, DoD, Hostile downloaders, Phishing, Privilege abuse, Ransomware, Rooting, Spam, Spyware, Trojans 
			- New vectors: Infecting IDEs to disseminate infected apps
				- Recent example: XCodeGhost

### *Android Platform Security Model : Threat Model*
- Hardware
	- Lost, stolen, lent/ borrowed
	- Direct physical access must be assumed possible in different device states: Powered off, screen locked, screen unlocked by different user, physical proximity
- Operating System / Platform 
	- Malicious apps due to use of untrusted apps → privacy threats for user, security threats for OS
	- Direct attacks over network interfaces (cell network, WLAN, Bluetooth, NFC) due to use of untrusted networks.
- Apps
	- Secure coding practices not used widely
	- Exploiting bugs in apps or OS, due to use of untrusted content
	- Privacy violations by apps (eg. location services)
- User 
	- Authentication to mobile devices is hard to make secure and usable
	- User needs to be able to trust the smartphone -> problem of masquerading apps
### [[Actors in the ecosystem (with Security Impact)]]
![[Pasted image 20231110131852.png]]
Android Platform Security Model: Multi-part consent
![[Pasted image 20231117170217.png]]
