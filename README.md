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

<img src="https://i.imgur.com/T104SFS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

In short, the red highlighted records are all ad responses that are being directed to my browser's view of the website when the ad request returns a successful response.

<b>My Target DNS Query Response</b>


Highlighted is the DNS response record we are going to focus in on. You can already tell that without any protection, the response from my router shows the DNS record and from there will appear on the website when I am browsing. That is a successful ad request and response. If I click on the ad, I will get linked to the ad website. To quickly touch the surface level risks of ads, simply by clicking an ad can put your computer at risk. You may be taken to an "ad" site that can use different phising tactics that can inevitably install malware onto your system.

<img src="https://i.imgur.com/InzXEOS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<b>Target DNS Query Response - Answer</b>

Wireshark also grants the capability of looking at the response in depth. Take note of how response answers appear.

<img src="https://i.imgur.com/S5SMN2h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Wireshark: Reviewing DNS Requests After My DNS Server Is Active</h2>

<b>My Target DNS Query Responses</b>

Notice that many of the DNS Query Response Records have a new "irregular" address of 0.0.0.0. That is because the DNS server is responding to the requests with what many would call a DNS sinkhole address. We essentially respond with the address of 0.0.0.0 and send the ads there instead of my PC's address essentially blocking the ads from ever reaching my computer.

<img src="https://i.imgur.com/wup6m61.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<b>Target DNS Query Response - Answer</b>

Here are the details (answer) of the query response. 

<img src="https://i.imgur.com/mD9L0JS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Resources and Supplies Used</h2>

- <b>Raspberry Pi 5</b>
- <b>Mini SD Card</b>
- <b>Mini SD Card Reader</b>
- <b>Computer</b>
- <b>All-in-One Modem</b> - Would recommend buying third party equipment so you dont run into roadblocks like I did.

<h2>DNS Server Setup</h2>

<b>I will avoidi showing how I set up my Raspberry Pi as there are many tutorials that anyone can watch on Youtube. Just make sure you use the following command to get your Raspberry Pi updated with the latest updates/patches!</b>

- sudo apt update




<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
