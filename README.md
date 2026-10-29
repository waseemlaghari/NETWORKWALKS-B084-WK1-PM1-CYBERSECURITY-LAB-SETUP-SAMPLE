# NETWORKWALKS-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP-SAMPLE

**Cybersecurity Lab Environment Setup**

------------------------------------------------


Building an isolated virtual lab for penetration testing and ethical hacking practice

In this project we will focuse on setting up a virtual machine for  cybersecurity and penetration-testing using VirtualBox and Kali Linux.


The lab establishes a secure, isolated virtual environment to safely conduct and replicate cybersecurity testing, such as network scanning and vulnerability assessments. By utilizing a private network, the setup ensures scalability, allowing administrators to easily add new target machines for future authorized testing.

The primary objective of this environment is to provide a safe, repeatable space for authorized security testing.
• Isolation: Configured on a private virtual network to prevent external exposure during reconnaissance, scanning, and vulnerability assessments.
• Scalability: Designed to easily integrate additional virtual machines as future testing targets.

------------------------------------------------

**Objectives**
------------------
The primary objectives of this project are to:
• Establish the Virtualization Platform: Install and configure Oracle VM VirtualBox.
• Deploy the Testing Environment: Import and set up Kali Linux as the primary virtual machine.
• Isolate the Network: Construct a private NAT network to secure all lab activities.
• Provision IP Routing: Configure network connectivity and assign a static IP address to the Kali VM.
• Validate Environment Stability: Verify network communication, DNS resolution, and capture a clean snapshot for disaster recovery.
• Ensure Future Scalability: Document the deployment process to establish a baseline for subsequent security testing.

----------------------

**Purpose of the Lab**
---------------------------

This lab establishes an isolated, controlled environment optimized for cybersecurity education and authorized security assessments.
The infrastructure supports a wide range of hands-on technical activities, including:
• Reconnaissance & Footprinting: Network discovery and targeted port scanning.
• Vulnerability Analysis: Assessing system weaknesses and analyzing packet data.
• Application & Exploit Testing: Web security evaluations and practical exploitation exercises.
• Tool Validation: Safe experimentation with diverse security frameworks.

⚠️ Ethical Compliance Directive: This environment must be used exclusively on systems you own or have explicit written authorization to evaluate. Utilizing these tools or infrastructure against unauthorized targets is strictly prohibited.

------------------------------------

**Lab Configuration**
-----------------------------------

🧩 Component	⚙️ Configuration
🖥️ Host OS	Windows 10
🧠 Host RAM	16 GB
⚡ Processor	Intel Core i7-8650U
🧰 Hypervisor	VirtualBox 7.2.4
🐉 Security OS	Kali Linux 2026.3
🧠 Kali RAM	6615 MB
🌐 Virtual Network	NAT Network
📡 Network Address	10.0.0.0/24
🐧 Kali IP Address	10.0.0.2/24
🚪 Default Gateway	10.0.0.1
🌍 DNS Server	8.8.8.8
🔮 Future VM Range	10.0.0.3–10.0.0.99

----------------------------------------

**🪜 Lab Setup Procedure**
----------------------------------

Step 1. Install 7-Zip
--------------------------
7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive.

Tool: 7-Zip

-----------------------

Step 2. Install VirtualBox
------------------------------
VirtualBox was installed as the hypervisor.

----------------------------

Step 3. Create the NAT Network
--------------------------
NAT Network was created in VirtualBox.

Configuration: Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled

<img width="728" height="490" alt="virtualbox_Network" src="https://github.com/user-attachments/assets/030fe0eb-a3f0-40d1-8471-5e3dfc083495" />

A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

---------------------------------

Step 4. Import Kali Linux
-------------------------------
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1
Attached to: NAT Network
Network:     cyberintern

The VM was allocated:

>RAM: 6615 MB

---------------------------------

<img width="1122" height="716" alt="kali_ready" src="https://github.com/user-attachments/assets/f2d85343-fe59-443b-8649-642f2b1f60f2" />
A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

-------------------------------------

Step 5. Configure the Kali Linux Network
-------------------------------

Example configuration:
>IP Address: 10.0.0.2
>Subnet Mask: 255.255.255.0
>Gateway: 10.0.0.1
>DNS: 8.8.8.8

<img width="637" height="683" alt="kali_network_setting" src="https://github.com/user-attachments/assets/2af46872-2a62-4d5e-8331-854378be9093" />

Internet is also working inside Kali Linux

<img width="1279" height="674" alt="internet_working" src="https://github.com/user-attachments/assets/aeb4d949-3db0-433e-9f5f-d86ed89c4bcd" />


--------------------------------------

Step 6. Create a Clean VM Snapshot
------------------

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

>FirstKali

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

------------------------

Lab Verification
---------------------

✅ Test	🧾 Command	🎯 Expected Result
🌐 Check IP address	ip a	Correct Kali IP displayed
📡 Test gateway	ping 10.0.0.1	Successful replies
🌍 Test Internet connectivity	ping 8.8.8.8	Successful replies
🔎 Test DNS resolution	nslookup networkwalks.com	Domain resolves
🧰 Verify Nmap	nmap --version	Nmap version displayed
🔄 Verify snapshot	Restore snapshot and run ip a	Baseline configuration restored

Results
>IP Address:
>10.0.0.2/24

>Gateway:
>10.0.0.1

>DNS:
>8.8.8.8

----------------------------

🐞 Problems Encountered & Solutions
--------------------------

 Internet Connectivity After Static IP Configuration
 ----------------

 There was problem with the ip as we assign it static so we run this command to overcome this
 >sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0


---------------------------

💡 What I Learned
------------------

Through this project, I built and configured an isolated virtual environment for cybersecurity practice, gaining hands-on experience with hypervisors, network segmentation, and system recovery.

1. NAT vs NAT Network
While both configurations provide external internet access, they serve different structural purposes:
Standard NAT: Isolates individual VMs from the host and each other.
NAT Network: Creates a shared internal network where multiple VMs can communicate with each other, making it the ideal foundation for a multi-machine cybersecurity lab.

2. Virtual Machine Networking
I gained practical experience configuring VirtualBox network adapters to control VM connectivity and network isolation.

3. Static IP Configuration
I gained hands-on proficiency in network configuration by manually setting up and verifying IPv4 parameters within Kali Linux. This included configuring static IP addresses, subnet masks, default gateways, and DNS settings to ensure proper network alignment and connectivity.

4. VM Snapshots
I integrated virtual machine snapshot strategies to safeguard the laboratory environment

5. Documentation
I realized that maintaining clear records of commands, settings, screenshots, issues encountered, and troubleshooting steps is a key part of professional cybersecurity work.


--------------------------------


Tools & Resources
--------------------

>7-Zip: https://7-zip.org/download.html <br />
>VirtualBox: https://virtualbox.org/wiki/Downloads <br />
>Kali Linux: https://kali.org/get-kali

----------------------------------

👤 Author
-------------
Waseem Laghari
Cybersecurity Professional B084

LinkedIn: https://www.linkedin.com/in/waseemlaghari/

----------------------

📌 Project Information
-----------

Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
