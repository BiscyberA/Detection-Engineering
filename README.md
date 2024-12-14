 <h1>Detection Engineering Homelab</h1>
 - [Analyzing SMTP Headers and Email Body ]

<h2>Description</h2>
In this lab we will cover Phishing Email, a social engineering technique constantly used by attackers to trick victims to click on links in other to steal their information and penetrate networks and computers.We will Install Thunderbird email client on a Window 10 virtual machine. We will view the raw source of an email,analyze the SMPT headers and Email Body to identify malicious links,IPs and urls using various tools.
<br />

<h2>Tool Used</h2>

- <b>Message Header Analyzer</b> 
- <b>IPinfo.io</b> 
- <b>urlscan.io</b> 
- <b>VirusTotal</b> 
- <b>Url Extractor</b> 


<h2>Environments Used </h2>

- <b>Thunderbird Email Client</b>
- <b>Windows 10</b> (21H2)

<h2>Lab walk-through:</h2>

<p align="center">
Installing ThunderBirdEmail Client on Windows 10 Host: Click Next<br/>
<img src="https://imgur.com/6exFdvr.png" height="80%" width="80%"/>
<br />
<br />
Click Next to Allow Standard Setup<br/>
<img src="https://imgur.com/mQ7nPyw.png" height="80%" width="80%"<br/>
<br />
<br />
Click install<br/>
<img src="https://imgur.com/YeUs5PT.png" height="80%" width="80%" 
<br />
<br />
Setup Installing<br/>
<img src="https://imgur.com/GiwJdMT.png" height="80%" width="80%" <br/>
<br />
<br />
Installation Complete: Click finish<br/>
<img src="https://imgur.com/sYhcXWr.png" height="80%" width="80%"<br/>
<br />
<br />
ThunderBird is launch. Create an email account, just as I have done and fowarded some suspicious email into the inbox.<br/>
<img src="https://imgur.com/eOWXhff.png" height="80%" width="80%" />
<br />
<br />
Below is  the main body email: Attackes always request a quick responds for their phish emails(ugency).In this email,it is timed to make the victim responds as quickly as posible. Also looking at the graphics of the email, grammatical errors indicates suspicious emails<br/>
<img src="https://imgur.com/2dGzRen.png" height="80%" width="80%" /> 
<br />
<br />
Below image is the raw source of the Email Header: We will analyze with Message header analyzer to get a better view<br/>
<img src="https://imgur.com/VOpNwF9.png" height="80%" width="80%" />
<br />
<br />
Below is the raw source of the body of the email.We will use Url Extractor to extract all the links in the body<br/>
<img src="https://imgur.com/JcQz4Ms.png" height="80%" width="80%" />
<br />
<br />
Below is a better view of the Email Header using Message Header Analyzer: I will use VirusTotal to learn more about the host name 'sonic.gate.mail.ne1.yahoo.com'I will also use ipinfo.io to learn about the Ip address 98.137.66.83 associated with hostname sonic321-20.consmr.mail.gq1.yahoo.com<br/>
<img src="https://imgur.com/wEJT5uO.png" height="80%" width="80%" />
<br />
<br />
Below is a result of the domain sonic.gate.mail.ne1.yahoo.com: It looks clean but there are files embeded in the domain. We will dig down to identify any suspicious or malicious activities<br/> 
<img src="https://imgur.com/jjGrRlQ.png" height="80%" width="80%" />
<br />
<br />
Below is a result and information about the IP Adress 98.137.66.83 using ipinfo.io: Showing the city,region. country and location of the IP<br/>
<img src="https://imgur.com/vDWkXWv.png" height="80%" width="80%" />
<br />
<br />
More information about the IP Address: I am interested in the domain oath.com associated with IP address. I will use VirusTotal to learn more about it<br/> 
<img src="https://imgur.com/nVjCIIF.png" height="80%" width="80%" />
<br />
<br />
Below is the result and more information about oath.com using VirusTotal: We can see this domain has been flagged as malicious. The IP address 98.136.103.23 highlighted in blue has 4 malicious activiies. I will run the IP in VirusTotal to learn about the malicious activities<br/> 
<img src="https://imgur.com/qjYtqta.png" height="80%" width="80%" />
<br />
<br />
Below is a result of the IP 98.136.103.23 using VirusTotal: We can see there is a Malware and a Phishing activity associated with the IP Address.This IP was associated with the domain oath.com. Oath.com was also associated with the IP 98.137.66.83 which has the domain sonic321-20.consmr.mail.gq1.yahoo.com that send the original email<br/>
<img src="https://imgur.com/HEjQHLG.png" height="80%" width="80%" />
<br />
<br />
I use Url Extractor to extract the Email body for any links or urls. Below shows the urls in the email body. We will use UrlScan.io to learn more about the url giovascuss.com<br/>
<img src="https://imgur.com/LlG60ov.png" height="80%" width="80%" />
<br />
<br />
Below is the result of UrlScan of giovascuss.com. We can see its IP Address, located in Vietnam and also flag as malicious
<img src="https://imgur.com/Qhfhq5m.png" height="80%" width="80%" />
<br />
<br />

<h1>In Conclusion</h2>
As a Security Analysis,when you receive a ticket of Phishing Email from employees, it is always important to use various available tools necessary to drill down the email and identify all the suspicious or malicious activites. You can also use malware sandbboxes to analyze attachments if any to identify the behaviour of a malware

</p>

