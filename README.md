Setting Up Routing on Cisco Routers: A Step-by-Step Guide
In this post, I'll walk you through how I configured routing on a simple network topology involving two routers and two PCs. The network is divided into three subnets: 192.168.1.0/24, 192.168.2.0/24, and 192.168.3.0/24. Let's dive into the details.

Network Topology Overview
The topology consists of two routers (R1 and R2), a switch, and two PCs (PC1 and PC2). Here's the addressing plan we used:

Device	Interface	IP Address	Subnet Mask	Default Gateway
R1	Fa0/0	192.168.1.1	255.255.255.0	N/A
R1	S0/0/0	192.168.2.1	255.255.255.0	N/A
R2	Fa0/0	192.168.3.1	255.255.255.0	N/A
R2	S0/0/0	192.168.2.2	255.255.255.0	N/A
PC1	N/A	192.168.1.10	255.255.255.0	192.168.1.1
PC2	N/A	192.168.3.10	255.255.255.0	192.168.3.1
Configuring Router R1
I started by configuring R1. I connected to the router and set the IP addresses for the FastEthernet0/0 and Serial0/0/0 interfaces. The FastEthernet interface connects to the switch and ultimately to PC1, while the Serial interface connects to R2.

Configuring FastEthernet0/0 on R1:

I set the IP address to 192.168.1.1 with a subnet mask of 255.255.255.0.
Enabled the interface with the no shutdown command.
Configuring Serial0/0/0 on R1:

I assigned the IP address 192.168.2.1 with a subnet mask of 255.255.255.0.
Since this is a DCE interface, I set the clock rate to 64000.
Enabled the interface with the no shutdown command.
Configuring Router R2
Next, I moved on to R2, configuring the FastEthernet0/0 and Serial0/0/0 interfaces. The FastEthernet interface connects to the switch and PC2, and the Serial interface connects back to R1.

Configuring FastEthernet0/0 on R2:

I set the IP address to 192.168.3.1 with a subnet mask of 255.255.255.0.
Enabled the interface with the no shutdown command.
Configuring Serial0/0/0 on R2:

I assigned the IP address 192.168.2.2 with a subnet mask of 255.255.255.0.
Enabled the interface with the no shutdown command.
Configuring PCs
With the routers set up, I configured the IP settings on the PCs to ensure they could communicate with the routers and each other.

Configuring PC1:

I assigned the IP address 192.168.1.10 with a subnet mask of 255.255.255.0.
Set the default gateway to 192.168.1.1 (R1's FastEthernet0/0 interface).
Configuring PC2:

I assigned the IP address 192.168.3.10 with a subnet mask of 255.255.255.0.
Set the default gateway to 192.168.3.1 (R2's FastEthernet0/0 interface).


