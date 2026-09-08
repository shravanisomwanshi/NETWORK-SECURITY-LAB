LAB 18 — ACL for VTY Interfaces

📌 Overview

This Cisco Packet Tracer lab demonstrates how to secure remote SSH management of a Cisco switch using a Standard Access Control List (ACL) applied to VTY interfaces.

The switch is configured for SSH-based remote administration with local user authentication. A standard ACL is then applied to the VTY lines to ensure that only the authorized System Administrator PC (192.168.1.5) can initiate a remote management session.

This configuration adds an additional access-control layer to SSH by restricting which source IP address is permitted to access the switch's VTY lines.

🎯 Objectives

The main objectives of this lab are:

Configure a management IP address on the switch.

Configure the switch default gateway.

Configure SSH for secure remote management.

Create a local user for SSH authentication.

Enable SSH Version 2.

Configure VTY lines for SSH access.

Create a Standard IPv4 ACL.

Permit SSH access only from the authorized System Administrator PC.

Apply the ACL to the VTY interfaces using access-class.

🖥️ Network Topology

The topology consists of:

1 × Cisco Router — Router0

1 × Cisco Switch — TEST-SSH

1 × System Administrator PC — SysADMIN-PC

4 × Sales Department PCs — PC1, PC2, PC3, PC4

Network Structure

The topology contains two IP networks:

IT Department Network: 192.168.1.0/24

Sales Department Network: 192.168.2.0/24

The router provides communication between these two networks, while the switch is managed through its VLAN 1 interface.

🌐 IP Addressing

Device

Interface / Role

IP Address

Router0

G0/1

192.168.1.1/24

Router0

G0/0

192.168.2.1/24

TEST-SSH Switch

VLAN 1

192.168.2.254/24

SysADMIN-PC

IT Department

192.168.1.5/24

PC1

Sales Department

192.168.2.8/24

PC2

Sales Department

192.168.2.7/24

PC3

Sales Department

192.168.2.6/24

PC4

Sales Department

192.168.2.5/24

🔐 Configuration Performed

1. Switch Management Configuration

The switch management interface is configured on VLAN 1 with:

IP address: 192.168.2.254

Subnet mask: 255.255.255.0

Default gateway: 192.168.2.1

This provides Layer 3 reachability for remote management of the switch.

2. SSH Configuration

SSH is configured on the switch for secure remote administration.

The configuration includes:

Hostname: TEST-SSH

Enable password: CISCO

Domain name: CISCO.COM

Local username: CISCO

Local password: CISCO

RSA key generation

SSH Version 2

The VTY lines are configured to:

Use local authentication.

Accept SSH connections.

3. Standard ACL Configuration

A Standard ACL numbered 10 is configured to control access to the VTY lines.

The ACL permits:

192.168.1.5

and denies other source IP addresses.

4. ACL Applied to VTY Interfaces

ACL 10 is applied inbound to VTY lines 0–15 using:

access-class 10 in

This means the switch checks the source IP address before allowing a remote VTY session.

🛡️ Security Policy

The access policy implemented in this lab is:

Source Device

Source IP

VTY/SSH Access

SysADMIN-PC

192.168.1.5

✅ Allowed

Other source IPs

Any other address

❌ Denied

Therefore, the switch's SSH management access is restricted to the authorized System Administrator PC.

🔄 SSH Access Flow

SysADMIN-PC
192.168.1.5
     │
     │ SSH
     ▼
 Router0
     │
     ▼
 TEST-SSH Switch
192.168.2.254
     │
     ▼
 VTY ACL 10
     │
     ├── 192.168.1.5 → PERMIT
     │
     └── Other IPs → DENY

🧪 Verification

The following commands can be used to verify the configuration:

show ip interface brief
show ip ssh
show access-lists
show running-config

Connectivity Verification

The switch configuration includes connectivity testing toward:

ping 192.168.2.1
ping 192.168.1.5

SSH Verification

From the authorized System Administrator PC:

ssh -l CISCO 192.168.2.254

The expected result is that the authorized PC can establish an SSH session with the switch.

📚 Key Concepts Demonstrated

SSH

Provides secure remote management of network devices.

VTY Interfaces

Virtual terminal lines used for remote management sessions such as SSH.

Standard ACL

Controls traffic based on the source IPv4 address.

access-class

Applies an ACL specifically to VTY lines to control remote management access.

Local Authentication

Uses a username and password configured locally on the switch.

SSH Version 2

The switch is configured to use SSH Version 2 for remote management.

✅ Expected Result

After completing the configuration:

The switch should be reachable through its management IP 192.168.2.254.

SSH should be enabled on the switch.

The System Administrator PC (192.168.1.5) should be permitted to access the VTY lines.

Other source IP addresses should be denied by ACL 10.

Remote switch administration is therefore restricted to the authorized source.

🛠️ Tools & Technologies

Cisco Packet Tracer

Cisco IOS CLI

SSH

IPv4 Standard ACL

VTY Access Control

Local User Authentication

📂 Project Files

LAB-18-ACL-for-VTY-Interfaces.pkt
LAB-18-ACL-for-VTY-Interfaces-README.md
LAB-18-ACL-for-VTY-Interfaces-commands.txt

📝 Conclusion

This lab demonstrates a practical method for securing Cisco switch remote management by combining SSH, local authentication, VTY configuration, and a Standard ACL.

By applying ACL 10 to the VTY interfaces, SSH access is limited to the authorized System Administrator PC (192.168.1.5). This helps reduce unauthorized remote management access and demonstrates an important network security practice for Cisco infrastructure.

Lab: 18
Topic: ACL for VTY Interfaces
Platform: Cisco Packet Tracer
Focus: Secure Remote Management