# Lab 1: Exploration
## Objective:  	
1.  Introduction to control system devices and provide insight into the types of information you can obtain through publicly available sources.  

2. Use Google, Shodan, and other resources to perform exploratory research into specific control system devices.  You will attempt to answer specific questions about the devices and their operation. 
3.  Identify internet-facing targets (you will not attack or communicate with any targets).
	
## References: 	
[Google](https://www.google.com/)  
[Google Scholar](https://scholar.google.com/)  
[Shodan](https://www.shodan.io/)
## Due Date: 02 April, 2200 

## Instructions: 
* Type the answers to the questions using either latex or markdown.  If you get help from other sources, cite your sources at the end in works cited / bibliography (IEEE style).
* Compress all supporting documentation used to generate the pdf (.md, .tex files, images, etc.) into a file named "lab_01_lastname.zip".  Include a text file with the commands and any additional steps you used to generate the .pdf.  Submit the compressed file through the MS Teams Assignment.  

## Tasks:
**Collect the required information about the listed devices/apps.**  

### MicroLogix 1100 - 1763-L16BWA
#### 1.	What are three applications where you might find a MicroLogix 1100 used in the private sector?
Applications include controlling motors, pumps, fans, or other machinery with Industrial uses.

#### 2.	What are two examples of Air Force applications that might use the MicroLogix 1100?  Provide links to the article(s) or AF websites to support the examples.  Do not include any academic publications such as AFIT theses.
1. Weapons systems such as Nuclear Weapons or Aircraft - https://www.lockheedmartin.com/en-us/products/f-35/f-35-capabilities.html
2. Logistical systems such as fueling or base management (HVAC, power distribuition, water treatment etc) - https://www.businessinsider.com/us-air-force-combat-jets-refuel-navy-military-aerial-fighter-2018-12

#### 3.	Find links to three academic articles related to the MicroLogix 1100.
1. https://www.jstor.org/stable/26486850?casa_token=dXVsh0bWNPIAAAAA%3AogpCnvh0N9YKdE3wVmjwc-V2U-fCLFQQr5fef_ZZH9BUyO70ylUxEpYkugjTX2mUBb3rTUQIWrN_B3Mqfq_9oQ24abQCKdQEVsisp5VKBt8vtQ6YxDE&seq=1
2. https://dl.acm.org/doi/abs/10.1145/3174776.3174780?casa_token=vF2Bdbnfwq8AAAAA:CdyV-dO2sjoJtJGCwJFiKlHrd4bpddPpxTvPoubTpOe3-kYs6wxc_zjr7u7nktfprfbGg9wsUFVbrw
3. https://link.springer.com/chapter/10.1007/978-3-030-30215-3_20

#### 4.	What are two primary communication interfaces featured in these devices (e.g., WiFi, Ethernet, USB, etc.)?
https://literature.rockwellautomation.com/idc/groups/literature/documents/um/1763-um001_-en-p.pdf
1. Ethernet
2. USB

#### 5.	What TCP/UDP-based protocols do these devices use (list at least two)?
1. DHCP
2. DNS

#### 6.	What TCP or UDP ports do the protocols from the previous question use?
1. DHCP - UDP port 67
2. DNS - UDP Port 53

#### 7.	How can you obtain the current IP address and MAC address of the MicroLogix without connecting to it (i.e., using physical access)?
You can find the information using the screen by navigating to Advanced Settings and then ENET Cfg which will list the IP and Mac addresses.

#### 8.	What vendor software is used to program these devices?
RSLogix 500

#### 9.	What does the "IP" in "Ethernet/IP" stand for?  Is this a stupid name? Hint: it is not "internet protocol"
Industrial Protocol. I would say the likeness to internet protocl is unfortunate however seeing that the name comes from the adaptation of the Common Industrial Protocol (CIP) I would say it isn't a stupid name.
#### 10. This device supports CIP; what does CIP stand for?  There are multiple definitions; make sure you get the correct one for this PLC.
Common Industrial Protocol

#### 11. Find and list two vulnerabilities for the MicroLogix 1100 PLC and which firmware versions they affect.  Provide the CVE ID and firmware versions.
1. Denial of Service - CVE-2021-33012 - All versions of Allen-Bradley MicroLogix 1100 - https://www.cybersecurity-help.cz/vdb/SB2021070905
2. Denial of Service - CVE-2020-6111 - Allen-Bradely MicroLogix 1100: 10 - 16 - https://www.cybersecurity-help.cz/vdb/SB2020101370

#### 12. Use Shodan to find at least 500 internet-facing MicroLogix 1100 PLCs (do not visit their IP addresses or communicate with them).  What exact search term did you use? How many devices did you find? What are the top three countries that use these PLCs?  
Port:44818 product:"Rockwell Automation/Allen-Bradley" - Best search I found before I hit the limit of searches. Found 4,455 devices with the top countries being the US, China, and Republic of Korea
  
### Mobile - IoT
#### 1.	What are some dynamic and static reverse engineering tools for Android applications?

#### 2.	What are some dynamic and static reverse engineering tools for iPhone applications?

#### 3.	Identify and discuss two cyber-attacks / exploits deployed to mobile devices.  How could they have been mitigated?

#### 4.	 Use Shodan to find three Internet of Thing (IoT) devices (security cameras, baby cameras, etc.)

#### 5.	What are the different use cases for IoT devices?

#### 6.	If someone asks you to assess an application to find out if it is malicious, what are the tools/methods you could use?

#### 7.	What are some anti-reverse engineering methods developers have in place to protect their application and the data it processes?

#### 8.	What are some third-party libraries available to store mobile application data? 

#### 9.	Why do most home routers have a built-in web server for administration?  Why might that be a security concern? 

#### 10. How many IP addresses does a mobile phone have, which protocols use them, and how do you find those addresses? 

#### 11. How many MAC addresses does a mobile phone have, which protocols use them, and how do you find those addresses? 

#### 12. What are the ways that mobile applications can send and receive data between other applications?  For example, you can launch the camera from a messaging application (e.g., Whatsapp) on an Android device.  

#### 13. How does inter-process communication differ from Android to iPhone devices? 

#### 14. How might a threat actor install an unwanted application on a mobile phone?
