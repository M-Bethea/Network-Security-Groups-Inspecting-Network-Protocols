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

- Observe ICMP
- Observe SSH
- Observe DHCP
- Observe DNS
- Observe RDP

<h2>Actions and Observations</h2>

<p>
(Create your Resources)
A. Create a Resource Group <br>
i. Create a Windows 10 Pro Virtual Machine (VM), Version 22H - x64 Gen2: Virtual Machine -> Create -> Azure Virtual Machine <br>
ii. While creating the VM, select the Resource Group you just created and the same Region. Size: 2 VPU's, 16GIB Memory <br>
iii. While creating the VM, it will create a new Virtual Network (Vnet) and Subnet in the Network tab. Checkmark licensing  <br>
B. Create a Linux (Ubuntu) 20.04 LTS x64 Gen2 VM. Under Administrator Account -> Authentication Type-> Password -> Create Username and Password <br>
i. While create the VM, select the same Resource Group and Vnet as your Windows VM <br>
ii. Observe the Virtual Network within Network Watcher
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/29dcf385-0740-478d-8ca1-462d3e204013" height="70%" width="70%" alt="VM Setup"/>
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/4a137f0f-cdae-4657-b4c3-2b2810dc48e9" height="70%" width="70%" alt="VM Setup"/>
</p>
<br />

<p>
(Observe ICMP Traffic) <br>
A. Use Remote Desktop to connect to your Windows 10 Virtual Machine <br>
i. Within your Windows 10 Virtual Machine, Install Wireshark by using the browser and searchin "Wireshark download" <br>
ii. Open Wireshark and filter for ICMP traffic only. Under file button:-> "Start Capturing Packets" -> type ICMP into search box -> Enter <br>
B. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM suing CMD: ping (private IP address) <br>
i. Observe ping requests and replies within WireShark <br>
ii. From The Windows 10 VM, open command line (CMD) or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark <br>
C. Initiate a non-stop ping from your Windows 10 VM to your Ubuntu VM <br>
i. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic: Ubuntu VM -> Network -> Add Inbound Port Rule -> ICMP -> Deny -> Add  <br>
ii. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity by pinging Ubuntu VM again <br>
iii. Re-enable/Update ICMP traffic for the Network Security Group your Ubuntu VM is using <br>
iv. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working) <br>
V. Stop the ping activity
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/ca7e1b8c-fcef-41e5-89c8-63705bd70a26" height="70%" width="70%" alt="Observing ICMP Traffic"/>
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/94cf9728-9c36-458d-83c1-a310f6d2f7d7" height="70%" width="70%" alt="Observing ICMP Traffic"/>
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/ee3c6b20-2fbb-4cf6-b08a-7930a500ce91" height="70%" width="70%" alt="Observing ICMP Traffic"/>
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/aa99536a-0b4f-4f54-ac45-cdcb2b20beba" height="70%" width="70%" alt="Observing ICMP Traffic"/>
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/1e81aeb7-2603-46a0-a50c-38a900fe6f71" height="70%" width="70%" alt="Observing ICMP Traffic"/>
</p>
<p>
<br />

<p>
(Observe SSH Traffic) <br>
Back in Wireshark, filter for SSH traffic only: Type "SSH" into search box -> enter -> start capturing packets <br>
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address): ssh username@privateIPAddress -> yes (if prompted) -> enter -> password <br>
Type commands (rmdir, mkdir, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark <br>
Exit the SSH connection by typing ‘exit’ and pressing [Enter]
</p>
<p>
<img src="https://github.com/M-Bethea/azure-network-protocols/assets/139162550/6a7858a1-636d-4933-8de5-40b0f3cb6e9b" height="70%" width="70%" alt="Observe SSH Traffic"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<br />
