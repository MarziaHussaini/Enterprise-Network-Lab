<h1>Enterprise-Network-Lab</h1>

<h2>Description</h2>
🔹 VLANs (Virtual Local Area Networks)
VLANs are used to divide a physical network switch into multiple, logical networks. Each VLAN acts like a separate network, isolating traffic and reducing broadcast domains. This improves security, performance, and network manageability.

📌 Simple Example: Devices in the HR department can be placed in VLAN 10, while Finance uses VLAN 20—even though they’re connected to the same physical switch.

🔹 DTP (Dynamic Trunking Protocol)
DTP is a Cisco protocol that helps switches automatically decide if a connection should carry traffic for one VLAN (access) or multiple VLANs (trunk). While helpful in test environments, DTP is usually turned off in production for security reasons.

📌 Simple Example: When connecting two Cisco switches, DTP can automatically form a trunk port to allow VLAN traffic to pass between them.

🔹 HSRP (Hot Standby Router Protocol)
HSRP is a Cisco protocol that allows two or more routers to work together to provide a redundant gateway. One router is active, and another is on standby. If the active one fails, the standby takes over instantly—users won’t notice any interruption.

📌 Simple Example: If the main router goes down, HSRP ensures users can still reach the Internet via a backup router, without changing any settings.

🔹 OSPF (Open Shortest Path First)
OSPF is a dynamic routing protocol that helps routers share and learn routes automatically. It's fast, scalable, and uses a link-state model to find the shortest and most reliable path through the network.

📌 Simple Example: In a large enterprise with dozens of routers, OSPF ensures each one knows the best route to every other network—without manual configuration.

🔹 NAT (Network Address Translation)
NAT allows private IP addresses (used inside a company) to be translated into public IP addresses (used on the Internet). It hides internal network details and helps conserve global IPv4 addresses.

📌 Simple Example: A company with 100 computers can use one public IP address to access the Internet, with NAT translating requests behind the scenes.

🔹 VPN (Virtual Private Network)
A VPN creates a secure, encrypted tunnel over the Internet, allowing remote users or sites to safely access internal company resources. It protects data from being intercepted or tampered with.

📌 Simple Example: A remote employee uses a VPN to securely connect to their company’s internal systems from home or while traveling.
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

🟦 VLAN 10 (Light Blue box)
 - <b> Connected Devices: PC1, PC2<b>
 - <b> VLAN ID: 10<b>
 - <b> Subnet: 192.168.10.0/24<b>
 - <b> Default Gateway: 192.168.10.100 (HSRP virtual IP))<b>
 
🟪 VLAN 20 (Purple box)
 - <b> Connected Devices: PC1, PC2<b>
 - <b> VLAN ID: 10<b>
 - <b> Subnet: 192.168.10.0/24<b>
 - <b> Default Gateway: 192.168.10.100 (HSRP virtual IP))<b>
 
🟩 VLAN 30 (Green box)
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

 


