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
2. Logistical systems such as fueling or base management (HVAC, power distribuition, water treatment etc) - https://www.airforce.com/careers/detail/heating-ventilation-air-conditioning-and-refrigeration

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
Port:44818 1763 - I found 684 devices with the top three countries being the United States, Spain, and Denmark. 
  
### Mobile - IoT
#### 1.	What are some dynamic and static reverse engineering tools for Android applications?
APKInspector, APKTool, Objection, Sign.jar, Btyecode viewer, Jadx, Qark. List found from: https://andreafortuna.org/2019/07/18/reverse-engineering-and-penetration-testing-on-android-apps-my-own-list-of-tools/

#### 2.	What are some dynamic and static reverse engineering tools for iPhone applications?
GDB/LLDB, Cycript, Logify, Blacktop/IPSW, IOS Header Dumps, FlexDecrypt
#### 3.	Identify and discuss two cyber-attacks / exploits deployed to mobile devices.  How could they have been mitigated?
1. ForcedEntry/Pegasus spyware: This attack was allegedly developed by the NSO Group in Israel to delploy their Pegasus spyware. The exploit disguised a PDF file as a GIF to inject code and cause an integer overflow in the devices core graphics system resulting in a backdoor/installation of spyware. This attack could have been mitigated by the user being less trusting when downloading files from individuals and Apple could have not had an exploitable buffer overflow. 
2. A more broad example of mobile cyber-attacks would be phishing attacks. Attacker can use URL padding to create large URLs that look like they go to innocent websites when displayed on the smaller screens of mobile devices but actually take the user to malicious websites. Additionally, attackers can simply trick individuals into downloading malicious files from spoofed/blatantly malicious texts or emails. These can be mitigated by being less-trusting, double checking files and URLs before downloading them, and educating people how to spot phishing attempts.

#### 4.	 Use Shodan to find three Internet of Thing (IoT) devices (security cameras, baby cameras, etc.)
Found 3 million security cameras with the following Shodan search: camera product:"Hikvision IP Camera"

#### 5.	What are the different use cases for IoT devices?
In short, IoT devices are pieces of hardware that are connected to the internet or can communicate with other devices over another network. They have many use cases a few being transmiting sensor data, automating machinery, moving actuators, various appliances, medical equipments, etc.

#### 6.	If someone asks you to assess an application to find out if it is malicious, what are the tools/methods you could use?
The first thing I would do is Google the application's name to find out more about it. If its well known and has thousands of reviews/a media following it probably isn't malicious. Next, I would see if there are any virus scanners I could use to scan it or other forms of mobile security that could flag it. Finally, if it was already installed I would check to see if it had access to permissions it didn't need or if it was using data more than it reasonably shoud. 

#### 7.	What are some anti-reverse engineering methods developers have in place to protect their application and the data it processes?
One method is to check if the application is being ran in a virtual machine and if it is corrupt the data/do something else very bad. Another is to have anti-debugging methods in place that check poplar debugging sustem API calls or use code exceptions to check for them and once again do something bad like corrupting the application data or encrpyting it. To protect the data the application can encrypt it or scramble it when not in use so static analysis is much harder.
#### 8.	What are some third-party libraries available to store mobile application data? 
Spring Framework, ANTLR 4, Apache Commons

#### 9.	Why do most home routers have a built-in web server for administration?  Why might that be a security concern? 
For the most part to provide an easy interface for the admin to set up the router. It would be expensive to add a hardware interface that would do the same job (some type of control panel and screen) and you would have to physically access the router everytime you want to make a change (a lot of the time they are put in high places). This is a security concern because people don't need physical access to the device to access the admin website and most of the time the provided credentials are not changed and are probably listed on the router itself.

#### 10. How many IP addresses does a mobile phone have, which protocols use them, and how do you find those addresses? 
A mobile phone has 4 IP addresses. Protocols include Mobile IP (MIP) and ICMP Router Discovery Protocol (IRDP). You can find the addresses by going to your phone's settings and looking at about my device/network settings.
#### 11. How many MAC addresses does a mobile phone have, which protocols use them, and how do you find those addresses? 
A mobile phone has 1 MAC address, one protocol that uses them is ARP, and you can find the MAC addresses by going to your phones settings and consulting my device/network settings.

#### 12. What are the ways that mobile applications can send and receive data between other applications?  For example, you can launch the camera from a messaging application (e.g., Whatsapp) on an Android device.  
Most mobile appplications and the underlying operating system allows for API calls to hardware devices or programs so they can be used by other approved applications. An example of this is Android's Intent. 

#### 13. How does inter-process communication differ from Android to iPhone devices? 
Android makes use of 'intents' or the Adorid sharesheet. The recieved data has a MIME type set by the providing app and the data can be recieved by an Activity with a matching intent-filter tag in the manifest, one or more ChooserTarget objects returned by the ChooserTargetService, or by using sharing shortcuts published by the app. Iphones don't allow processes to directly communicate between programs and implements IPC through sending notification flags or chunks of data using specific programs such as XPC, CPDistributedMessagingCenter, or Unix Sockets to name some.

#### 14. How might a threat actor install an unwanted application on a mobile phone?
If the mobile phone uses the google play store a threat actor could use social engineering to harvest the credentials and use the google play store to remotely install applications. Another way would be to send a malicious script that when ran downloads the application or installs a backdoor that lets the threat actor control the phone remotely. 

