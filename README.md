<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create our Resources
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic
<h2>Actions and Observations</h2>
Steps to Monitor Network Traffic with Wireshark on Azure VMs
</P>1. Create a Resource Group in Azure
Log into the Azure Portal.
Navigate to "Resource groups".
Click "Create" and fill in the required details.
<img width="302" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/96700a57-3e67-4625-ab39-4fba34e6598f">
<P>2. Create a Windows VM and a Ubuntu VM
In the Azure Portal, navigate to "Virtual machines".
Create a Windows VM.
<p><img width="283" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/47bf571b-ede2-4647-964a-a1bd61ace044"></p>  
Create a Ubuntu VM in the same resource group.
</P><img width="280" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/4ed3800a-64ed-40b8-85ef-598d329d2b27">


</P>3. Use Remote Desktop to Connect to Windows VM
Obtain the public IP address of the Windows VM.
Use Remote Desktop to connect to the Windows VM using the obtained IP address.
</P>4. Install Wireshark in Windows VM
Download Wireshark from Wireshark's official website.
Install Wireshark on the Windows VM.
</P>5. Filter by ICMP Traffic in Wireshark
Open Wireshark.
In the filter bar, type ICMP and apply the filter.
</P>6. Ping the Private IP Address of Ubuntu VM from Windows VM
Find the private IP address of the Ubuntu VM.
Open Command Prompt in the Windows VM.
Ping the ubuntu VM: ping <Linux_VM_Private_IP>.
</P>7. Open PowerShell in Windows VM, Ping a Public Address, and Observe Traffic in Wireshark
Open PowerShell in the Windows VM.
Ping a public address: ping google.com.
Observe the traffic in Wireshark.
</P>8. Initiate Non-Stop Ping from Windows VM to Ubuntu VM
In the Command Prompt of the Windows VM, run a continuous ping: ping -t <Linux_VM_Private_IP>.
</P>9. Disable ICMP Traffic in Network Security Group of Ubuntu VM
In the Azure Portal, navigate to the Network Security Group (NSG) associated with the Ubuntu VM.
Add an inbound security rule to deny ICMP traffic.
</P>10. Observe ICMP Traffic in Wireshark
Check Wireshark on the Windows VM to see the effect of disabling ICMP traffic.
</P>11. Re-enable ICMP Traffic
In the Azure Portal, revert the inbound security rule to allow ICMP traffic.
</P>12. Observe ICMP Traffic in Wireshark Again
Check Wireshark on the Windows VM to see the restored ICMP traffic.
</P>13. Filter for SSH Traffic in Wireshark
In Wireshark, set the filter to ssh.
</P>14. Type Commands into Ubuntu VM and Observe SSH Traffic in Wireshark
Use an SSH client (like PuTTY) to connect to the Ubuntu VM from the Windows VM.
Observe the SSH traffic in Wireshark while typing commands in the Ubuntu VM.
</P>15. Filter for DHCP Traffic in Wireshark
In Wireshark, set the filter to DHCP.
</P>16. Issue a New IP Address in Windows VM from the Command Line
Open Command Prompt in the Windows VM.
Release the current IP: ipconfig /release.
Renew the IP: ipconfig /renew.
</P>17. Observe DHCP Traffic in Wireshark
Check Wireshark for DHCP traffic.
</P>18. Filter for DNS Traffic in Wireshark
In Wireshark, set the filter to DNS.
</P>19. Use nslookup to Find IP Addresses of Public Websites
Open Command Prompt in the Windows VM.
Use nslookup to query a few public websites: nslookup google.com.
</P>20. Observe DNS Traffic in Wireshark
Check Wireshark for DNS traffic.
</P>21. Filter for RDP Traffic in Wireshark
In Wireshark, set the filter to rdp.
</P>22. Observe the Non-Stop Spam of Traffic
Observe the constant RDP traffic in Wireshark.
</P>23. Close the Remote Desktop and Delete the Resource Groups/VMs
Disconnect from the Windows VM.

Follow these steps to successfully monitor and analyze network traffic using Wireshark on Azure VMs.
