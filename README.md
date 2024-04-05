<h1>Home Lab: Personal DNS Server</h1>


<h2>Why I Created My Own DNS Server</h2>
For this home lab project, I will be utilizing Adguard Home to create my very own DNS Server. This will provide my network with a few benefits that will increase security on my private network. Some of those benefits include:
Ad Blocking
Privacy protection
Parental controls and filtering
Protection against trackers and phishing
This is a great way to implement rules of safety on the internet especially if multiple people who are on my personal network are not privy to the dangers of the web. 
Adguard Home specifically provides an easy way for users to create a home server without needing an actual rack system or expensive gear to incorporate a DNS server. You can host the DNS server on a cloud provider or follow my path in which I have a Raspberry Pi 5 set up to provide the DNS functionality.

Creating my own DNS server will allow me to control my network's domain name resolution process. To dive deeper, having my own DNS server grants me the capabilities of performance and security. Some of the benefits of having my own DNS server are as follows:
- 

<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
