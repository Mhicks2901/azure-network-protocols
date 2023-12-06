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
   - Use our remote deskptop to connect to our Windows 10 Virtual Machine
   - While inside our Virtual machine we will install Wireshark
   - Within Wireshark, lets filter for ICMP traffic only
   - Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM and observe ping requests and replies within WireShark
   - From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website such as www.google.com and observe the traffic in WireSharkObserve ping requests and replies within WireShark
   - Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
- Part 3 Observing SSH Traffic
  - Back in Wireshark filter for SSH traffic
  - From your Windows 10 VM, SSH into your Ubuntu Virtual Machine via its private IP address
- Part 4 Observing DHCP Traffic
   - Back in Wireshark, filter for DHCP traffic 
   - From your Windows 10 VM, attempt to issue your VM a new IP address from the command line ipconfig /renew 

- Part 5 Observing DNS Traffic
   - Back in Wireshark, filter for DNS traffic 
   - From your Windows 10 VM within a command line, use nslookup to see what google.com address is 

- Part 6 Observing RDP Traffic
   - Back in Wireshark, filter for RDP traffic
   - Observe the constant flow of spam traffic
     - Since the RDP is a protocol that is constantly showing you a live feed from one computer to another.

