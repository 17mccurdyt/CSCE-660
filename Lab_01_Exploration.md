<div>
<img align="left" src="../img/afit-logo.png" height="150" title="HILICS"><img align="right" src="../img/ccr-logo.png" height="150" title="HILICS">  
</div><br clear="all" /><br>

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
1.	What are three applications where you might find a MicroLogix 1100 used in the private sector?
2.	What are two examples of Air Force applications that might use the MicroLogix 1100?  Provide links to the article(s) or AF websites to support the examples.  Do not include any academic publications such as AFIT theses.
3.	Find links to three academic articles related to the MicroLogix 1100.
4.	What are two primary communication interfaces featured in these devices (e.g., WiFi, Ethernet, USB, etc.)?
5.	What TCP/UDP-based protocols do these devices use (list at least two)?
6.	What TCP or UDP ports do the protocols from the previous question use?
7.	How can you obtain the current IP address and MAC address of the MicroLogix without connecting to it (i.e., using physical access)?
8.	What vendor software is used to program these devices?
9.	What does the "IP" in "Ethernet/IP" stand for?  Is this a stupid name? Hint: it is not "internet protocol".
10.	This device supports CIP; what does CIP stand for?  There are multiple definitions; make sure you get the correct one for this PLC.
11.	Find and list two vulnerabilities for the MicroLogix 1100 PLC and which firmware versions they affect.  Provide the CVE ID and firmware versions.
12.	Use Shodan to find at least 500 internet-facing MicroLogix 1100 PLCs (do not visit their IP addresses or communicate with them).  What exact search term did you use? How many devices did you find? What are the top three countries that use these PLCs?  
  
### Mobile - IoT
1.	What are some dynamic and static reverse engineering tools for Android applications?
2.	What are some dynamic and static reverse engineering tools for iPhone applications?
3.	Identify and discuss two cyber-attacks / exploits deployed to mobile devices.  How could they have been mitigated?
4.	 Use Shodan to find three Internet of Thing (IoT) devices (security cameras, baby cameras, etc.)
5.	What are the different use cases for IoT devices?
6.	If someone asks you to assess an application to find out if it is malicious, what are the tools/methods you could use?
7.	What are some anti-reverse engineering methods developers have in place to protect their application and the data it processes?
8.	What are some third-party libraries available to store mobile application data? 
9.	Why do most home routers have a built-in web server for administration?  Why might that be a security concern? 
10.	How many IP addresses does a mobile phone have, which protocols use them, and how do you find those addresses? 
11.	How many MAC addresses does a mobile phone have, which protocols use them, and how do you find those addresses? 
12.	What are the ways that mobile applications can send and receive data between other applications?  For example, you can launch the camera from a messaging application (e.g., Whatsapp) on an Android device.  
13.	How does inter-process communication differ from Android to iPhone devices? 
14.	How might a threat actor install an unwanted application on a mobile phone?
