LAB 19 — Layer 3 Multilayer Switch Configuration

Overview

This Cisco Packet Tracer lab demonstrates the basic configuration of Layer 3 functionality on Cisco Multilayer Switches.

Two Cisco 3650-24PS Multilayer Switches are configured with routed GigabitEthernet interfaces by disabling Layer 2 switchport functionality using no switchport and assigning IPv4 addresses directly to the interfaces.

The topology uses two separate IPv4 networks:

192.168.1.0/24

192.168.2.0/24

A Cisco 1941 router connects the two networks.

Objectives

Enable IP routing on the Multilayer Switches.

Convert a physical GigabitEthernet interface from Layer 2 switchport mode to a Layer 3 routed interface.

Assign IPv4 addresses to routed interfaces.

Bring the interfaces up using no shutdown.

Verify Layer 3 connectivity using ICMP ping.

Topology

Devices

Cisco 3650-24PS Multilayer Switch0

Cisco 3650-24PS Multilayer Switch1

Cisco 1941 Router

Network Layout

192.168.1.0/24                         192.168.2.0/24

Multilayer Switch0                    Multilayer Switch1
G1/0/1                                G1/0/1
192.168.1.2                            192.168.2.2
       \                              //
        \                            //
             Cisco 1941 Router

The topology labels show the router-side networks as 192.168.1.0/24 and 192.168.2.0/24.

IP Addressing

Device

Interface

IP Address

Subnet Mask

Multilayer Switch0

Gi1/0/1

192.168.1.2

255.255.255.0

Multilayer Switch1

Gi1/0/1

192.168.2.2

255.255.255.0

The screenshot shows the router connecting the two networks, but the router's exact interface IP configuration is not included in the visible switch command notes. This README therefore does not invent additional router commands.

Configuration Performed

Multilayer Switch0

The following Layer 3 configuration is performed on GigabitEthernet1/0/1:

IP routing is enabled.

The interface is changed from a Layer 2 switchport to a routed Layer 3 interface.

IP address 192.168.1.2/24 is assigned.

The interface is enabled.

Multilayer Switch1

The same Layer 3 configuration approach is used on GigabitEthernet1/0/1:

IP routing is enabled.

The interface is converted to a routed interface.

IP address 192.168.2.2/24 is assigned.

The interface is enabled.

Key Configuration Concepts

ip routing

Enables Layer 3 routing capability on a multilayer switch.

no switchport

Converts a physical Ethernet interface from a Layer 2 switchport into a Layer 3 routed interface.

This allows an IP address to be configured directly on the physical interface.

ip address

Assigns an IPv4 address and subnet mask to the routed interface.

no shutdown

Administratively enables the interface.

Verification

The lab includes connectivity verification between the two Multilayer Switches.

From Multilayer Switch0:

ping 192.168.2.2

From Multilayer Switch1:

ping 192.168.1.2

Successful replies confirm Layer 3 connectivity between the configured switch interfaces, provided the intermediate router and required routing are configured correctly.

Additional useful verification commands are:

show ip interface brief
show ip route

Expected Result

After the complete topology is correctly configured:

Multilayer Switch0 should have 192.168.1.2/24 on Gi1/0/1.

Multilayer Switch1 should have 192.168.2.2/24 on Gi1/0/1.

The routed interfaces should be operational.

The two networks should be able to communicate through the router when the required router and routing configuration is present.

The configured ping tests should succeed.

Security / Networking Relevance

Layer 3 switching allows a multilayer switch to perform routing functions in addition to traditional Layer 2 switching. Routed physical interfaces are useful when connecting different IP networks and designing enterprise networks with Layer 3 boundaries.

Tools & Technologies

Cisco Packet Tracer

Cisco IOS CLI

Cisco 3650-24PS Multilayer Switch

Cisco 1941 Router

IPv4

Layer 3 Routing

ICMP

Project Files

LAB-19-Layer-3-Switch-Configuration.pkt
LAB-19-README.md
LAB-19-commands.txt

Conclusion

This lab demonstrates the fundamental process of configuring Cisco Multilayer Switch interfaces for Layer 3 operation. By enabling ip routing, using no switchport, and assigning IP addresses to physical interfaces, the switches can participate in routed network communication.

The lab provides a practical foundation for understanding Layer 3 switching, routed ports, IP addressing, and inter-network connectivity.