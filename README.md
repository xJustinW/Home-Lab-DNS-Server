<h1>Home Lab: Personal DNS Server</h1>
In this lab, I am documenting the steps I take in order to install Adguard Home on a Raspberry Pi to create my own personal DNS Server. The DNS server's main role is to increase privacy and security for any device that is on my network.

<h2>Why I Created My Own DNS Server</h2>
Creating my own DNS server will allow me to control my network's domain name resolution process. To dive deeper, having my own DNS server grants me with the capabilities of privacy and security. There are even very small instances of performance boosts that can be observed. Some of the benefits of having my own DNS server are as follows:

- AD Blocking
- Reduced Risk of Malware/Phishing
- Safe Search
- Parental Controls
- DNS Rewrites
- Very Slight Performance Boost
- Much More!

As mentioned earlier, this serves as an effective method to reduce the uncertainty associated with avoiding ads, trackers, and the unregulated expanse of the internet. Through enforced rules, filters, and blocklists, certain security practices are automated by this project. Moreover, it offers a sleek dashboard reminiscent of a SIEM tool, providing the ability to monitor both incoming and outgoing traffic. However, while the DNS server will intervene upon command, it's essential to recognize that users accessing the network and internet still bear significant responsibility. Everyone on my network must adhere to safe practices. Next, I'll demonstrate the difference between a standard ad query response and how my DNS server handles an ad query with specific features enabled.
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

<img src="https://i.imgur.com/OII2Z0K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<b>Target DNS Query Response - Answer</b>

Wireshark also grants the capability of looking at the response in depth. Take note of how response answers appear.

<img src="https://i.imgur.com/M2Vf6PV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

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

<b>I will avoid showing how I set up my Raspberry Pi as there are many tutorials that anyone can watch on Youtube. You will have to SSH into the deivce in order to complete the DNS server setup. Just make sure you use the following command to get your Raspberry Pi updated with the latest updates/patches!</b>

- sudo apt update

Once you have SSH'ed into the Pi and updated it, run the following command:

- curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v

<img src="https://i.imgur.com/GpA8lcp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Note: This screenshot is not from my personal Pi as I already have it installed and do not want to wipe my settings to get an accurate picture of the CLI at point of the installment.

<b> </b>

This will essentially send a request to the URL that is in the command to grab and download Adguard Home onto the PI. Once the download was finished, the CLI prompted me with an address for me to navigate to to complete setup of Adguard Home on the PI. The address led me to a login page where I had to update my password. Then, there was a setup page I had to follow in order to get my devices to connect to the DNS server that I just created. Since my ISP does not allow me to update the DNS settings of the provided all-in-one modem, I had to manually input the given DNS server addresses on my devices. Essentially, I went to my network settings on each device and navigated to the DNS Configuration settings. Here, I switched from automatic DNS to manual and addded every DNS address to each device. When I buy my own router, I will be able to setup the DNS addresses at the router level to avoid having to add the addresses on every new device. This has not become annoying yet as I do not have much people over for me to be connecting new devices but that time will come.

<b> </b>

<img src="https://i.imgur.com/dFzwNoC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Configuring My DNS Server</h2>

<b>Adguard Home provides my DNS server with a variety of configuration settings so that I  am able to fine tune my server how I want it. I will quickly go over these settings. A simple Google search will provide much more information if it is needed.</b>

<b>Dashboard</b>


<img src="https://i.imgur.com/iwyg691.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<b>Settings</b>
- General Settings - There are settings for log and statistic configuration. There are also quick activate options for safe searching and parental controlling.
<img src="https://i.imgur.com/lhjZkeT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


- DNS Settings - I can define various different upstream DNS servers and load-balance across the address. Adguard will use the fastest address most often for performance boosts. I can also define Fallback DNS servers and Bootstrap DNS servers. I can even define a private reverse DNS server. Lastly, there are cache and server configurations I can mess with to fine-tune my DNS sever.
<img src="https://i.imgur.com/CCT3JOR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


- Encryption Settings - Here, I can set up security features like DOH and DNSSEC. THere are other features such as SSL certificate chains andd private key paths.
<img src="https://i.imgur.com/uyeed5p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


- Client Settings - This page will show me my current persisten clients and runtime clients. I would need to set up persistant clients but there is the autmoated runtime clients section that shows current addresses that are using my DNS server.
<img src="https://i.imgur.com/i18AhQU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


- DHCP Settings - If my router for whatever reason does not utilize DCHP, I can use my DNS server to provide DHCP configuration if activated. I can also provide static leases if the DHCP server is set up.
<img src="https://i.imgur.com/SIeXn7Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>




<b>Filters</b>

- DNS Blocklists - I can block individual DNS addresses or choose some of the provided lists that are curated for filtering out commonly known phishing sites.
- DNS Allowlists - I can allow certain DNS addresses if I am running tighter security on my network.
- DNS Rewrites - I can assign custom DNS responses for specific domain names.
- Blocked Services - I can block prominent sites and services with the flip of a toggle. This makes it easy to block out services like gaming launchers so I can limit what games are played over the network.

<img src="https://i.imgur.com/BFazqc3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Custom Filtering Rules - I have the option to add specific rules for filtering.


<b>Query Logs</b>


Last but not least, I have a page where I can actively monitor the logs of each request and response that goes through my DNS server.

<img src="https://i.imgur.com/aqSK7XS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<b>All in all, I had a great time learning about creating my own servers and how to protect them. There are many 3rd party applications that bundle some of these features up and make it easy for anyone to set up and learn. I am constantly learning something new everyday and there will be more to come!!!</b>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
