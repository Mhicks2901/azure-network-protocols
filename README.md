<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


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

- Create our Resource Group
- Create 2 Virtual Machines (Windows 10 and Ubuntu)
- Observing ICMP Traffic
- Observing SSH Traffic
- Observing DHCP Traffic
- Observing DNS Traffic
- Observing RDP Traffic

<h2>Actions and Observations</h2>

- Part 1 is creating our resource group
  - We will make one Virtual Machine run from Windows 10
    - When creating the VM select the previously named resource group and allow it to create a virtual network
  - The second will be a Ubuntu Virtual Machine
    - Select the previously named resource group and virtual network
- Part 2 Observing ICMP Traffic
   - Open up the remote desktop on your computer
   <img src="https://i.imgur.com/b5SkxdR.png"/>
   
   - Lets get the public IP address on the Windows 10 VM
  <img src="https://i.imgur.com/xeFLSTn.png"/>
  
   - Input that into our remote desktop app
   - While inside our Virtual machine we will install Wireshark
      - Click blue icon by search bar
 <img src="https://i.imgur.com/cosP8Cq.png"/>
 
   - Within Wireshark, lets filter for ICMP traffic only by typing ICMP in the search bar
 <img src="https://i.imgur.com/FG5sqf2.png"/>

   - Since ICMP is a protocol that is used to ping for internet connectivity to different hosts notice nothing is being displayed
   - Retrieve the private IP address of the Ubuntu VM and open up Powershell to ping it from within the Windows 10 VM
  <img src="https://i.imgur.com/LvqX1dI.png"/>
  <img src="https://i.imgur.com/Vvv1j8F.png"/>
  
   - From the Windows 10 VM, use PowerShell to ping a public website such as www.google.com
     - Observe ping requests and replies within WireShark
   <img src="https://i.imgur.com/9MstXjl.png"/>

   - Click the green button above the search bar to clear the search, and lets initiate a perpetual from your Windows 10 VM to your Ubuntu VM
     - Ping your private Ubuntu IP again an add a -t as this will continue to ping non stop
     <img src="https://i.imgur.com/KsDZ0Jc.png"/>
     
- Part 3 Observing SSH Traffic
  - Back in Wireshark filter for SSH traffic
  <img src="https://i.imgur.com/NIdDh1i.png"/>
  
  - From your Windows 10 VM, Lets use SSH for your Ubuntu VM by using your username and private IP address from that VM
    - After typing yes to continue to connect it will ask for your password which will not be shown typing
    <img src="https://i.imgur.com/gu0lGbQ.png"/>
    <img src="https://i.imgur.com/hANpoTD.png"/>
 
    - Green text will indicate if your logged into your Ubuntu VM, typing exit will close the connection.
    <img src="https://i.imgur.com/WVdKsJI.png"/>
      
- Part 4 Observing DHCP Traffic
   - Back in Wireshark, filter for DHCP traffic
     <img src="https://i.imgur.com/Imrf27V.png"/>
     <img src="https://i.imgur.com/hANpoTD.png"/>
     
   - From your Windows 10 VM, lets issue your VM a new IP address from the command line ipconfig /renew
     <img src="https://i.imgur.com/EqTTuL2.png"/>
     - This may or may not disconnect your remote deskptop session.
     <img src="https://i.imgur.com/7tmqE4g.png"/>
     
- Part 5 Observing DNS Traffic
   - Back in Wireshark, filter for DNS traffic
     <img src="https://i.imgur.com/4VwuSm6.png"/>
     
   - From your Windows 10 VM within a command line, use nslookup to see what google.com address is
    <img src="https://i.imgur.com/8PU63l3.png"/>
     
- Part 6 Observing RDP Traffic
   - Back in Wireshark, filter for RDP traffic
     <img src="https://i.imgur.com/Tycjl98.png"/>
     <img src="https://i.imgur.com/RiUo5Zc.png"/>
     
   - Observe the constant flow of traffic
     - RDP is a protocol that is constantly showing you a live feed from one computer to another.

