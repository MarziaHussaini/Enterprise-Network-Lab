<h1>Enterprise-Network-Lab</h1>

<h2>Description</h2>


🔹 VLANs (Virtual Local Area Networks) is a logically segments a switch into multiple isolated networks. This enhances security, reduces broadcast traffic, and simplifies network management. For example, departments like HR (VLAN 10), Finance (VLAN 20), and Sales (VLAN 30) can share the same physical switch but operate on separate virtual networks, preventing direct communication between them by default.

🔹DTP (Dynamic Trunking Protocol) is a Cisco proprietary protocol that automatically negotiates trunk links between switches, allowing them to carry traffic from multiple VLANs.
For example, when two Cisco switches are connected, DTP can automatically establish a trunk link without manual configuration. However, in real-world networks, DTP is often disabled to prevent unauthorized or accidental trunking, which can lead to security vulnerabilities.

🔹 HSRP (Hot Standby Router Protocol) provides a virtual gateway by designating one router as active and another as standby, ensuring network redundancy and high availability. For example, If the active router fails, the standby router automatically takes over with no disruption to users or network connectivity.

🔹 OSPF (Open Shortest Path First) is a link-state routing protocol that dynamically calculates the shortest and most efficient path for data to travel across large and complex networks. For example, A company with offices in multiple cities uses OSPF on its routers to ensure automatic route updates. If a link between two sites fails, OSPF quickly recalculates and selects an alternate path, maintaining high availability and network scalabilit.

🔹 NAT (Network Address Translation) translates private IP addresses to a public IP for Internet access, hiding internal devices. For example, A company with 100 devices can access the Internet using just one public IP address.

🔹 VPN (Virtual Private Network) creates a secure, encrypted connection over the Internet so remote users can safely connect to the company's internal systems. For example, An employee connects from home to the office network securely using a VPN.
<br />

<h2>Tools and Utilities Used</h2>

- <b>VLANs</b> 
- <b>DTP</b>
- <b>HSRP</b>
- <b>OSPF</b>
- <b>NAT</b>
- <b> Command Prompt (CMD)</b>

<h2>Environments Used </h2>

- <b>Windows 11</b> 
- <b>Cisco Packet Tracer </b>

<h2>Network diagram</h2>

![Project Diagram](https://github.com/user-attachments/assets/f88fe7e5-24d9-44e8-be84-46c382ddc9d3)


<h2>Program walk-through:</h2>

<b>Open Cisco Packet Tracer </b>

<b> Devices Used <b>

- <b> 6 PCs (End-user devices)<b>
- <b> 3 Layer 2 Switches (Access Layer)<b>
- <b> 2 Layer 3 Swiches (HSRP and routing)<b>
- <b> Core & Branch Router (GRE tunnel shown between core router an branch)<b>
- <b> Branch Router (Remote office with servers)<b>
- <b> 1 Internet Cloud (Simulated WAN)<b>
- <b> Various Service Devices (HTTP, TFTP, FTP servers)<b>
- <b> Crossover and straight-through cables were used to connect the devices<b>

<b> End Devices (PCs) and VLANs<b>

<b> Each group of PCs is isolated logically using VLANs to segment traffic and improve security/performance <b>

🟦 VLAN 10 
 - <b> Connected Devices: PC1, PC2<b>
 - <b> VLAN ID: 10<b>
 - <b> Subnet: 192.168.10.0/24<b>
 - <b> Default Gateway: 192.168.10.100 (HSRP virtual IP))<b>
 
🟪 VLAN 20 
 - <b> Connected Devices: PC1, PC2<b>
 - <b> VLAN ID: 10<b>
 - <b> Subnet: 192.168.10.0/24<b>
 - <b> Default Gateway: 192.168.10.100 (HSRP virtual IP))<b>
 
🟩 VLAN 30 
 -  <b> Connected Devices: PC5, PC6<b>
 - <b> VLAN ID: 30<b>
 - <b> Subnet: 192.168.30.0/24<b>
 - <b> Default Gateway: 192.168.30.100 (HSRP virtual IP))<b>

<b> Layer 2 Switches (Access Switches)<b>

 - <b> Three switches, each handling a single VLAN<b>
 - <b> Switch 1 handles VLAN 10 (PC1, PC2)<b>
 - <b> Switch 2 handles VLAN 20 (PC3, PC4)<b>
 - <b>Switch 3 handles VLAN 30 (PC5, PC6))<b>
 
<b>End Devices (PCs) and VLANs diagram<b>

 
![Project Diagram](https://github.com/user-attachments/assets/f01c3c70-cf1b-474a-9f35-d01e02f16da4)

 <b>Switches/Routers with HSRP (Active/Standby)<b>
 
🔹 Router/Switch 1 (left): Active-Interface IPs

 - <b> 192.168.10.1<b>
 - <b> 192.168.10.1<b>
 - <b> 192.168.10.1<b>
 - <b> Participates in HSRP group for each VLAN<b>
 - <b> Handles default gateway duties under normal operation<b>

🔹 Router/Switch 2 ( Right): Standby-Interface IPs

 - <b> 192.168.10.2<b>
 - <b> 192.168.10.2<b>
 - <b> 192.168.10.2<b>
 - <b> Participates in HSRP group for each VLAN<b>
 - <b> Becomes active if Router/Switch 1 fails<b>

🔹 Virtual IPs via HSRP

 - <b> VLAN 10 Gateway: 192.168.10.100<b>
 - <b> VLAN 20 Gateway: 192.168.20.100<b>
 - <b> VLAN 30 Gateway: 192.168.30.100<b>
 
 <b>Purpose: Provides redundancy. If the Active router fails, the Standby takes over seamlessly for all VLANs<b>
                                                                                                           
<b>Note: Used trunking technology to connect three Layer 2 switches with two Layer 3 switches/routers, enabling the transmission of traffic from multiple VLANs over single physical links between devices. This approach optimized network efficiency and preserved VLAN segmentation throughout the infrastructure<b>

<b>Switches/Routers with HSRP (Active/Standby) Diagram<b>


<img width="567" alt="2 Switches" src="https://github.com/user-attachments/assets/c308e03d-64a1-4f67-8319-76327665ecc4" />





<b>GRE Tunnel & WAN Connectivity<b>

<b>A GRE Tunnel is configured between the core router and the branch router to simulate secure inter-site communication. This tunnel allows VLAN hosts to:<b>

 - <b>Reach the Branch Network 10.1.1.0/24<b>
 - <b>Access remote services (HTTP, FTP, TFTP)<b>
 
 🔹 GRE Tunnel

  GRE Tunnel Interface:

 - <b>From Core Router → Branch Router<b>
 - <b>GRE Tunnel IPs:<b>
 - <b>Core side: 172.16.1.1<b>
 - <b>Branch side: 172.16.1.2<b>
 - <b>Tunnel passes over:<b>
 - <b>Serial link: Se0/0/0 from Core → Se0/0/0 on Internet (8.8.8.8) → to Branch<b>
	
<b>Purpose: Allows internal traffic from VLAN PCs to reach the remote branch securely as if on the same internal network<b>

 🔹Internet Simulation
 
 - <b>A generic “Internet” device connects:<b>
 - <b>Core router (Se0/0/0: 100.1.1.1)<b>
 - <b>Branch router (Se0/0/1: 101.1.1.2)<b>
 - <b>Simulates WAN communication between main site and branch<b>

🔹Branch Office

  Branch Router:

 - <b>External IP: 101.1.1.1<b>
 - <b>Internal Interface: Gig0/1<b>
 - <b>LAN Subnet: 10.1.1.0/24<b>

<b>GRE Tunnel & WAN Diagram<b>

<img width="804" alt="Routers" src="https://github.com/user-attachments/assets/8943e299-d88f-43b6-94bb-b3b36acd17d6" />



<b>Branch Switch<b>

 - <b>HTTP Server: 10.1.1.30<b>
 - <b>TFTP Server: 10.1.1.20<b>
 - <b>FTP Server: 10.1.1.10<b>
 
<b>Branch Switch Diagram<b>


<img width="333" alt="Servers" src="https://github.com/user-attachments/assets/465c065f-9ef2-40ff-8fbf-8c013c8fdd9c" />





<b>Core Router – Network Configuration Verification Screenshots<b>



- <b>The core router performs server ping and IP route verification<b>



<img width="569" alt="coure router 2" src="https://github.com/user-attachments/assets/f740b94b-3294-4b4c-b8e9-063c784b2ef1" />



- <b>Core Router – Tunnel Interface and VLAN Connectivity Verification<b>


<img width="595" alt="show ip core router" src="https://github.com/user-attachments/assets/84e2ae9b-968d-404c-996a-bf1102717fcb" />




<img width="963" alt="tunnel111" src="https://github.com/user-attachments/assets/73779190-2719-4c63-8285-51b6dcf4f9ca" />




- <b>Verify the core router's configuration using the show running-config command<b>


<img width="1033" alt="corerouter config1 " src="https://github.com/user-attachments/assets/bd5c4fee-8d32-4002-8a45-9393ee5c881f" />




<img width="583" alt="show runnign config core router" src="https://github.com/user-attachments/assets/9331cec3-17c3-47bb-bf73-5715da2ec268" />




<b>Branch Router – Network Configuration Verification Screenshots<b>



- <b>Branch Router – Running-Config, IP Route, and Interface Verification<B>




<img width="631" alt="branch 1" src="https://github.com/user-attachments/assets/d6b1dfee-c752-4819-80fa-4616ce328d45" />




<img width="649" alt="branch router 2" src="https://github.com/user-attachments/assets/9b980693-d294-452a-81f1-1f45272fce5a" />




<img width="640" alt="branch router 3" src="https://github.com/user-attachments/assets/dc973978-025a-436c-bafe-534ddf766ccf" />




-<b>Branch Router – Verification of Running-Config, IP Routes, Interfaces, Pings, and Tunnel<b>




<img width="466" alt="branch1 ts" src="https://github.com/user-attachments/assets/fead170b-a85c-4584-b47b-7134c7efc064" />





<img width="1014" alt="ping brouter" src="https://github.com/user-attachments/assets/79ed4908-108c-4d80-89e4-c50d0eb8ae8c" />















