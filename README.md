<h1>Home Lab: Personal DNS Server</h1>
In this lab, I am documenting the steps I take in order to install Adguard Home on my Raspberry Pi to create my own personal DNS Server. The DNS server's main role on my network is to increase privacy and security for any device that is on my network.

<h2>Why I Created My Own DNS Server</h2>
Creating my own DNS server will allow me to control my network's domain name resolution process. To dive deeper, having my own DNS server grants me with the capabilities of privacy and security. There are even very small instances of performance boosts that can be observed. Some of the benefits of having my own DNS server are as follows:

- AD Blocking
- DNS Request Blocking
- Reduced Risk of Malware/Phishing
- Safe Search
- Parental Controls
- DNS Rewrites
- Very Slight Performance Boost
- Much More!

Like stated before, this is a great way to take out some of the guesswork of avoiding ads, trackers, and the wild west of what we call the internet. The imposed rules, filters, and blocklists will automate some security practices. This project also has a sleek dashboard similar to that of a SIEM tool that I can use to monitor incoming and outgoing traffic. Although the DNS server will intervene when told to do so, this does not take away all the responsibility from the user who is accessing the network and internet. Anyone on my network must still practice safe measures. Coming up, I will show what a natural ad query response looks like without enabling the Adguard festures and how my computer responds to an ad query response with our DNS server in place and active. 
<br />
<h2>Wireshark: Reviewing DNS Requests Before My DNS Server Is Active</h2>
Wireshark is a packet analyzer. I can select the type of network traffic I want to monitor, in my case I am viewing my ethernet connection and all the packets that are coming through it. For this project, I will be reviewing the DNS responses to demonstrate a proof of concept. That having your own DNS server can provide better privacy and security. 

<b> </b>

<b>Full View of My Wireshark Instance</b>

Here is an open instance of Wireshark capturing network traffic for what is passing through my ethernet connection. At the top, I have typed "DNS" to filter for the DNS protocol records. To be more specific, we will be looking at ad responses. Whenever I navigate to a website, the initial request for me to reach the site will also come with plenty of ads that are requesting to reach me as well.

<img src="https://i.imgur.com/dBf0JP4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

In short, the red highlighted records are all ad responses that are being directed to my browser's view of the website when the ad request returns a successful response.

<b>My Target DNS Query Response</b>


Highlighted is the DNS response record we are going to focus in on. You can already tell that without any protection, the response from my router shows the DNS record and from there will appear on the website when I am browsing. That is a successful ad request and response. If I click on the ad, I will get linked to the ad website. To quickly touch the surface level risks of ads, simply by clicking an ad can put your computer at risk. You may be taken to an "ad" site that can use different phising tactics that can inevitably install malware onto your system.

<img src="https://i.imgur.com/Vs7f9CF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<b>DNS Query Response Answer</b>
<img src="https://i.imgur.com/XyZwxTe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Wireshark: Reviewing DNS Requests After My DNS Server Is Set Up</h2>


<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/k3jtb6N.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
