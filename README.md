<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Building intuition for DNS</h2>
<p>
</p>
<p>
In this task, we'll be examining DNS A-Records on server DC-1. A-Records map hostnames to IP addresses. Our goal is to create an A record for "mainframe" and have it point to DC-1's private IP address.

Without setting the DNS record, attempting to ping "mainframe" will fail. 
<br />When we do ping "mainframe", Client-1 will first check its DNS cache, then its local host file, and finally the DNS server.
<p>
<img src="https://i.imgur.com/fU5qTCv.png" height="50%" width="65%" alt="Disk Sanitization Steps"/>
</p>
<p>

Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
<p>
<img src="https://i.imgur.com/VndZBu0.png" height="60%" width="75%" alt="Disk Sanitization Steps"/>
</p>
<p>
To create the A-record, follow these steps: go to Server Manager-> Tools-> DNS-> DC-1-> Forward lookup zones-> mydomain.com-> right click and create a new A record. Give it the title "mainframe". Set same IP address as your machines Private IP address. 
<p>
<img src="https://i.imgur.com/9V0J0Bp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, if we return to the client machine and ping "mainframe", we should receive a reply.


<h4>Flush DNS Cache</h4>
<p>
<img src="https://i.imgur.com/xKePr4k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/yAlrhZw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
Now we will change the record address of "mainframe" to 8.8.8.8 if we go back to the client machine it will still ping the old adress even though we changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />
<img src="https://i.imgur.com/KYNmZMz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/80ARdZu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly we will configure a CNAME record that points the host "search" to "www.google.com" If we ping "search" ping will not be able to find the host. we have to go back into the DNS tool on DC-1 and create the CNAME record "search". Once we create the CNAME record is created and we ping "search" it will resolve to www.google.com.
</p>
<br />
<p>
<img src="https://i.imgur.com/LgomfqN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/NovtDrd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
