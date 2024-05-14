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
<P><img width="598" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/d974e2f3-58b8-46eb-9542-dfe23df5d699">

</P>4. Install Wireshark in Windows VM
Download Wireshark from Wireshark's official website.
Install Wireshark on the Windows VM.
<p><img width="293" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/791cc5b4-642b-45dd-b388-fd63c24e71d9">

</P>5. Filter by ICMP Traffic in Wireshark
Open Wireshark.
In the filter bar, type ICMP and apply the filter.
<p><img width="668" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/946802a6-9d8e-42cf-a7f6-f4ba317b16b0">
</p>

</P>6. Ping the Private IP Address of Ubuntu VM from Windows VM
Find the private IP address of the Ubuntu VM.
<p></p><img width="595" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/61cb416d-192a-452e-9847-b523d74337da">

Open Powershell in the Windows VM.
Ping the ubuntu VM: ping <Linux_VM_Private_IP>.
<p><img width="364" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/a2e923f4-da42-4ce9-a734-b536093f54e2">
</p>

</P>7. Open PowerShell in Windows VM, Ping a Public Address, and Observe Traffic in Wireshark
Open PowerShell in the Windows VM.
Ping a public address: ping google.com.
Observe the traffic in Wireshark.
<p><img width="669" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/c34356f9-af1a-4ea2-86e8-3c88da82420b">
</p>

</P>8. Initiate Non-Stop Ping from Windows VM to Ubuntu VM
In the Command Prompt of the Windows VM, run a continuous ping: ping -t <Linux_VM_Private_IP>.
<p><img width="669" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/dbada762-b2e6-4af5-a360-1cbcfc4d620c">

</P>9. Disable ICMP Traffic in Network Security Group of Ubuntu VM
In the Azure Portal, navigate to the Network Security Group (NSG) associated with the Ubuntu VM.
Add an inbound security rule to deny ICMP traffic.
<p><img width="598" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/20174768-d5f5-4e43-a245-df594778e608">
</p>
</P>10. Observe ICMP Traffic in Wireshark
Check Wireshark on the Windows VM to see the effect of disabling ICMP traffic.
<P><img width="668" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/2095024a-65f5-43c5-8f07-26158e84b13b">
</P>
</P>11. Re-enable ICMP Traffic
In the Azure Portal, revert the inbound security rule to allow ICMP traffic.
</P><img width="598" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/9c172565-d6d4-4f0e-a940-86825d9a107e">

</P>12. Observe ICMP Traffic in Wireshark Again
Check Wireshark on the Windows VM to see the restored ICMP traffic.
</P><img width="668" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/38662f94-6cd9-490d-97d2-07c2a14024ea">

</P>13. Filter for SSH Traffic in Wireshark
In Wireshark, set the filter to ssh.
</P>
</P>14. Type Commands into Ubuntu VM and Observe SSH Traffic in Wireshark
Use an SSH client (like PuTTY) to connect to the Ubuntu VM from the Windows VM.
Observe the SSH traffic in Wireshark while typing commands in the Ubuntu VM.
</P><img width="670" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/a7c89341-929f-478b-8eb9-f5eea1d651e4">

</P>15. Filter for DHCP Traffic in Wireshark
In Wireshark, set the filter to DHCP.
</P><img width="310" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/e090c1e0-98a8-4de6-a5f8-e55ef9ddb7b0">

</P>16. Issue a New IP Address in Windows VM from the Command Line
Open Command Prompt in the Windows VM.
Renew the IP: ipconfig /renew.
Observe DHCP Traffic in Wireshark
Check Wireshark for DHCP traffic.
</P><img width="638" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/efd1e2ba-3924-4a1c-b6a5-6c27aa163fc5">

</P>18. Filter for DNS Traffic in Wireshark
In Wireshark, set the filter to DNS.
</P><img width="415" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/dda29edc-acbc-4da3-b411-1fae1a171e79">

</P>19. Use nslookup to Find IP Addresses of Public Websites
Open Command Prompt in the Windows VM.
Use nslookup to query a few public websites: nslookup google.com.
</P><img width="441" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/26d5dc99-2d11-4a06-a974-6df6918b9309">

</P>20. Observe DNS Traffic in Wireshark
Check Wireshark for DNS traffic.
<p><img width="413" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/32999b78-349b-4c94-abca-d0a361afd7c9">
</p>

</P>21. Filter for RDP Traffic in Wireshark
In Wireshark, set the filter to rdp or tcp.port == 3389
<p><img width="513" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/904486f4-33fb-401f-8102-7f040dfd579b">
</p>
</P>22. Observe the Non-Stop Spam of Traffic
Observe the constant RDP traffic in Wireshark.
<p><img width="514" alt="image" src="https://github.com/Angelplascencia007/azure-network-protocols/assets/168943120/fe026024-cc6a-4fcd-a251-566de5e27a37">
</p>
</P>23. Close the Remote Desktop and Delete the Resource Groups/VMs
Disconnect from the Windows VM.

Follow these steps to successfully monitor and analyze network traffic using Wireshark on Azure VMs.
