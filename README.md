 <h1>Detection Engineering Homelab</h1>
 - [Creating,Validating,Deploying and Monitoring Threat Detection Rules]

<h2>Description</h2>
In this lab, we will focus on the core principles of detection engineering by designing, validating, and monitoring threat detection rules to identify and mitigate potential cybersecurity threats. The lab environment includes configuring a Kali Linux,Windows 11, Ubuntu(Zeek) virtual machine, Nmap,Nikto,Elastic Siem and Atomic Red Team to simulate malicious activity, ingesting log data, and analyzing system behavior to create actionable detection rules.
<br />

<h2>Tools Used</h2>

- <b>Elastic SIEM</b> 
- <b>Kali Linux (Attacker)</b> 
- <b>Ubuntu (Zeek) VM</b> 
- <b>Atomic Red Team</b>
- <b>Nmap</b>
- <b>Nikto</b>



<h2>Environments Used </h2>

- <b>Windows 11 VM</b>
  

<h2>Lab walk-through:</h2>

<p align="center">
Installing ThunderBirdEmail Client on Windows 10 Host: Click Next<br/>
<img src="https://i.postimg.cc/qR84jBzL/Screenshot-2024-12-11-200416.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/Zn1JY9B6/Screenshot-2024-12-13-231314.png"/>
<br />
<br />
Click Next to Allow Standard Setup<br/>
<img src="https://i.postimg.cc/VNQh4qMx/Screenshot-2024-12-11-152317.png"/>
<br />
<br />
Click install<br/>
<img src="https://i.postimg.cc/MTZdrdGF/Screenshot-2024-12-13-234149.png" />
<br />
<br />
Setup Installing<br/>
<img src="https://i.postimg.cc/pX3cXf0m/Screenshot-2024-12-11-152424.png" />
<br />
<br />
Installation Complete: Click finish<br/>
<img src="https://i.postimg.cc/BQvtQD8f/Screenshot-2024-12-11-152445.png" />
<br />
<br />
ThunderBird is launch. Create an email account, just as I have done and fowarded some suspicious email into the inbox.<br/>
<img src="https://i.postimg.cc/7ZFLVWKq/Screenshot-2024-12-11-152553.png" />
<br />
<br />
Below is  the main body email: Attackes always request a quick responds for their phish emails(ugency).In this email,it is timed to make the victim responds as quickly as posible. Also looking at the graphics of the email, grammatical errors indicates suspicious emails<br/>
<img src="https://i.postimg.cc/BQtQG0yq/Screenshot-2024-12-11-153357.png" /> 
<br />
<br />
Below image is the raw source of the Email Header: We will analyze with Message header analyzer to get a better view<br/>
<img src="https://i.postimg.cc/nL1tDR5R/Screenshot-2024-12-11-153837.png" />
<br />
<br />
Below is the raw source of the body of the email.We will use Url Extractor to extract all the links in the body<br/>
<img src="https://i.postimg.cc/qRCSG1ZH/Screenshot-2024-12-11-190957.png" />
<br />
<br />
Below is a better view of the Email Header using Message Header Analyzer: I will use VirusTotal to learn more about the host name 'sonic.gate.mail.ne1.yahoo.com'I will also use ipinfo.io to learn about the Ip address 98.137.66.83 associated with hostname sonic321-20.consmr.mail.gq1.yahoo.com<br/>
<img src="https://i.postimg.cc/28HGV42Q/Screenshot-2024-12-11-192543.png" />
<br />
<br />
Below is a result of the domain sonic.gate.mail.ne1.yahoo.com: It looks clean but there are files embeded in the domain. We will dig down to identify any suspicious or malicious activities<br/> 
<img src="https://i.postimg.cc/pTYYx8mn/Screenshot-2024-12-11-193851.png" />
<br />
<br />
Below is a result and information about the IP Adress 98.137.66.83 using ipinfo.io: Showing the city,region. country and location of the IP<br/>
<img src="https://i.postimg.cc/4NK7QVXb/Screenshot-2024-12-11-194031.png" />
<br />
<br />
More information about the IP Address: I am interested in the domain oath.com associated with IP address. I will use VirusTotal to learn more about it<br/> 
<img src="https://i.postimg.cc/5NZH7y0c/Screenshot-2024-12-11-194405.png"/>
<br />
<br />
Below is the result and more information about oath.com using VirusTotal: We can see this domain has been flagged as malicious. The IP address 98.136.103.23 highlighted in blue has 4 malicious activiies. I will run the IP in VirusTotal to learn about the malicious activities<br/> 
<img src="https://i.postimg.cc/C5R1JppL/Screenshot-2024-12-12-111637.png"/>
<br />
<br />
Below is a result of the IP 98.136.103.23 using VirusTotal: We can see there is a Malware and a Phishing activity associated with the IP Address.This IP was associated with the domain oath.com. Oath.com was also associated with the IP 98.137.66.83 which has the domain sonic321-20.consmr.mail.gq1.yahoo.com that send the original email<br/>
<img src="https://i.postimg.cc/nzzccfzY/Screenshot-2024-12-12-112010.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/3NnYpLcC/Screenshot-2024-12-12-150440.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/9Q2YzLjN/Screenshot-2024-12-12-151024.png" />
<br />
<br />
I use Url Extractor to extract the Email body for any links or urls. Below shows the urls in the email body. We will use UrlScan.io to learn more about the url giovascuss.com<br/>
<img src="https://i.postimg.cc/1R8wJLHq/Screenshot-2024-12-12-114339.png" />
<br />
<br />
Below is the result of UrlScan of giovascuss.com. We can see its IP Address, located in Vietnam and also flag as malicious
<img src="https://i.postimg.cc/ZnN94z7s/Screenshot-2024-12-12-114804.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/wMYq5y2F/Screenshot-2024-12-12-130920.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/85SkMft4/Screenshot-2024-12-12-130947.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/N0XZ6Nnq/Screenshot-2024-12-12-131233.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/52bm7sjW/Screenshot-2024-12-12-133636.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/4yyD9Jkw/Screenshot-2024-12-12-133900.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/8zp0JpRv/Screenshot-2024-12-13-015514.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/Y9Z5Y5rH/Screenshot-2024-12-12-135111.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/kXcjd00g/Screenshot-2024-12-12-135355.png" />
<br />
<br />
Note<br/>
<img src="https://i.postimg.cc/P5V2CmrG/Screenshot-2024-12-12-135845.png" />
<br />
<br />
Note<br/>
<img src="" />
<br />
<br />
Note<br/>
<img src="" />
<br />
<br />
Note<br/>
<img src="" />
<br />
<br />
Note<br/>
<img src="" />
<br />
<br />
Note<br/>
<img src="" />
<br />
<br />
Note<br/>
<img src="" />
<br />
<br />

<h1>In Conclusion</h2>
As a Security Analysis,when you receive a ticket of Phishing Email from employees, it is always important to use various available tools necessary to drill down the email and identify all the suspicious or malicious activites. You can also use malware sandbboxes to analyze attachments if any to identify the behaviour of a malware

</p>

