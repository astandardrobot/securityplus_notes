# 16.1 Securing Network Devices
- These devices include switches, routers, firewalls, and more
- A **default account** user or admin-level account that is installed on a device by the manufacturer during production
	- Changing default account credentials, as well as default device names should always be considered
- **Weak passwords** should not be short. A *good* password should be at least 14 characters long and include uppercase, lowercase, numbers, and special characters. Moreover, none of these words should be in a dictionary
- **Privilege escalation** occurs when a user is able to gain the rights of another user or admin
	- **Vertical** P.E. occurs when an attacker goes from user level to admin level.
	- **Horizontal** P.E. occurs when an attacker moves from user to user
- **Backdoors** are a way of bypassing normal authentication in a system
- An IPS, proper firewall configs, network segmentation, and updates/patches should be deployed and maintained
- DON'T USE TELNET

# 16.2 Securing Network Media
- Includes copper, fiber optic, and coaxial cabling used as the connectivity method in a wired network
- **Electromagnetic Interference (EMI)** is a disturance that can affect electrical circuits, devices, and cables due to radiation or electromagnetic conduction
	- Can be caused by TVs, microwaves, cordless phones, motors, and other devices
	- Shielding the cables (STP) or the source can minimize EMI
- **Radio Frequency Interference (RFI)** is a disturbance that can affect electrical circuits, devices, and cables due to AM/FM transmissions or cell towers
	- Can cause issues for wireless networks
- **Crosstalk** occurs when a signal transmitted on one copper wire creates an undesired effect on another wire
	- Most modern networks are fine (i.e. Cat5E, Cat6A, etc.)
	- Punch-down blocks that were used for terminals. Networks should always use a 110 block
	- Most organizations use Unshielded twisted-pair cabling due to costs, so it's important to mitigate this.
- **Data Emanation** is the electromagnetic field generated by a network cable or device when transmitting
	- This is commonly reconstructed to gain access to a victim network. While this isn't used much today, if an agent can get physical access to your network, it can be an issue
	- The attacker can achieve this by splitting the wires of a twisted-pair connection
- **Protected Distribution System (PDS)** is a secured system of acble management to ensure that the wired network remains free from eavesdropping, tapping, data emanations, etc.
# 16.3 Securing WiFi Devices
- Much more susceptible to attacks because physical access isn't required
- Remote administration should be disabled
- **Service Set Identifier (SSID)** uniquely identifies the network and is the name of the WAP used by the clients
	- CompTIA recommends to disable this broadcasting to slow down the attacker.. In reality, it doesn't
- **Rogue Access Point** is an unauthorized WAP or Wireless Router allows access to the secure network
	- i.e. if someone doesn't want to plug into an Ethernet port to have access to the Internet, they might want to have a WAP in the room. However, this extends your wired network into the wireless world.
- **Evil Twin** is a rogue, counterfeit, and unauthorized WAP with the same SSID as yoru valid one
# 16.4 Wireless Encryption
- Encryption of data in transit is paramount to security
- **Pre-shared Key**: Same encryption key is used by the access point and the client
	- Scalability is difficult
- (**Wired Equivalent Privacy (WEP)**: Original 802.11 wireless security standard that claims to be as secure as a wired network
	- Originally used with a static, 40-bit PSK, which was upgraded to 64-bit and then 128-bit. 
	- The ISSUE with WEP is the 24-bit Initialization Vector that it uses to establish a connection...it's sent in clear text
 - **WiFi Protected Access (WPA)**: Replacement for WEP which uses TKIP (48-bit Initialization Vector), Message Integrity Check, and RC4 encryption
- **WPA2**: 802.11i standard to provide better wireless security, featuring AES with a 128-bit key, CCMP, and integrity checking
	- Uses a personal mode w PSKs or an enterprise mode with centralized authentication via a server to handle password distribution
- EXAM TIPS
	- Open = Network has no security, no protection
	- WEP = IVs
	- WPA = TKIP and RC4
	- WPA2 = CCMP and AES
- **WiFi Protected Setup (WPS)**: Automated encryption setup for wireless networks at a push of a button, but is severely vulnerable
	- Relies on an 8-digit code, but breaks it up into two 4-digit chunks when its sent. Because of this, brute forcing is significantly more effective
	- ALWAYS DISABLE THIS
- Always use a VPN (or, at least, it's always a good idea). Gives you another layer of encryption
# 16.5 Wireless Access Points
- Wireless security also relies upon proper WAP placement
- In this example, WAPs are using omnidirectional antennas. This is great from a coverage point, but is dangerous.
	- To ehance security, this directionality should be considered 
- Wireless B,G, and N use a 2.4GHz signal; Wireless A,N, and AC use 5GHz. 
	- The lower the number, the further the signal can travel
- **Jamming** is intentional radio frequency interference targeting your wireless network to cause a DoS condition
- **AP Isolation** creates network segments for each client when it connects to prevent them from cmomunicating with other clients on the network
# 16.6 Wireless Attacks
- **War driving** is the act of searching for wireless networks by driving around until you find them
	- Using survey or open source attack tools
- **War chalking** is the act of physically drawing symbols in public places to denote the open, closed, and protected networks in range
- **IV attack** occurs when an attacker observes the operation of a cipher being used with several different keys and finds a mathematical relationship between those keys to determine the clear text data
	- This happened with WEP
- **WiFi disassociation attack** is an attack that targets an individual client connected to a network, force it offline by deauthenticating it, and captures the handshake when it reconnects
	- Used as part of an attack on WPA/WPA2
- **Brute force** occurs when an attacker continually guesses a password until the correct one is found
	- This will ALWAYS find the password...eventually
# 16.7 WPA3
- Introduced in 2018 to strengthen WPA2
- Has an equivalent cryptographic strength of 192-bits using AES-256-bit encryption with SHA-384 hash for integrity checking in enterprise mode
- Uses CCMP-128 as the MINIMUM encryption required for secure connectivity
- Removal of the PSK exchange is the largest improvement
	- Uses Simultaneous Authentication of Equals (SAE), which is a secure password-based authentication and password-authenticated key agreement method
	- This provides forward secrecy
- **Perfect Forward Secrecy** is a feature of key agreement protocols that provides assurance that session keys will not be compromised even if long-term secrets used in the key exchange are compromised
	- Five step process:
		- 1: AP and the client use a public key system to generate a pair of long-term keys
		- 2: The AP and the client exchange a one-time use session key using a secure algorithm like Diffie-Hellman
		- 3: The AP sends the client messages and encrypt them using the session key created in step 2
		- 4: Client decrypts the messages received using the same one-time use session key
		- 5: The process repeats for every message being sent, starting at step 2 to ensure forward secrecy
# 16.8 Other Wireless Technologies
- **Bluejacking vs Bluesnarfing**: Bluejacking SENDS info to a device, and Bluesnarfing TAKES info from a device
- Don't allow Bluetooth devices to use default PINs for pairing
- **Radio Frequency Identification (RFID)**: Devices that use a radio frequency signal to transmit identifying information about the device or token holder
	- Depending on the device, RFID can be used from 10cm to 200m away
- **Near Field Communication (NFC)**: Allows two devices to transmit information when they are within close range through automated pairing and transmission
	- These devices are operated within 4cm from each other