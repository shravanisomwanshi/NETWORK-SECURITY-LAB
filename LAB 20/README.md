LAB 20 — Layer 3 EtherChannel Using LACP, PAgP & ON Modes

Overview

This Cisco Packet Tracer lab demonstrates the configuration of Layer 3 EtherChannel across three Cisco 3650 Multilayer Switches.

The lab combines three EtherChannel negotiation approaches:

LACP — Group 1

PAgP — Group 2

Static EtherChannel (ON mode) — Group 3

The physical links participating in each EtherChannel are converted into Layer 3 routed interfaces. Each resulting Port-Channel is then assigned an IPv4 address, creating logical Layer 3 links between the multilayer switches.

This lab provides practical experience with link aggregation, EtherChannel negotiation, routed interfaces, and Layer 3 addressing.

Objectives

Enable Layer 3 routing on multilayer switches.

Convert physical GigabitEthernet interfaces into routed interfaces.

Configure multiple physical links as EtherChannel members.

Demonstrate EtherChannel using LACP, PAgP, and static ON mode.

Create logical Port-Channel interfaces.

Assign IPv4 addresses to Layer 3 Port-Channels.

Understand active/passive and desirable/auto negotiation behavior.

Verify EtherChannel operation and Layer 3 connectivity.

Topology

The topology contains three Cisco 3650-24PS Multilayer Switches:

Multilayer Switch0

Multilayer Switch1

Multilayer Switch2

Each switch uses multiple GigabitEthernet links to form aggregated EtherChannel connections with neighboring switches.

EtherChannel Groups

EtherChannel Group

Technology

Switch Relationship

Network

Group 1

LACP

Switch0 ↔ Switch1

192.168.1.0/24

Group 2

PAgP

Switch0 ↔ Switch2

192.168.2.0/24

Group 3

ON Mode

Switch1 ↔ Switch2

192.168.3.0/24

Configuration Summary

Multilayer Switch0

Multilayer Switch0 acts as one endpoint for two Layer 3 EtherChannels.

Layer 3 Preparation

IP routing is enabled.

GigabitEthernet interfaces Gi1/0/1–6 are converted from Layer 2 switchports to Layer 3 routed interfaces.

EtherChannel Group 1 — LACP

Interfaces Gi1/0/1–3 participate in EtherChannel Group 1.

LACP active negotiation is used.

The resulting logical interface is Port-Channel 1.

Port-Channel 1 is assigned the Layer 3 address 192.168.1.1/24.

EtherChannel Group 2 — PAgP

Interfaces Gi1/0/4–6 participate in EtherChannel Group 2.

PAgP negotiation is used for the connection to Multilayer Switch2.

The resulting logical interface is Port-Channel 2.

Port-Channel 2 is assigned the Layer 3 address 192.168.2.1/24.

Multilayer Switch1

Multilayer Switch1 participates in two Layer 3 EtherChannels.

Layer 3 Preparation

IP routing is enabled.

GigabitEthernet interfaces Gi1/0/1–6 are converted to routed interfaces.

EtherChannel Group 1 — LACP

Interfaces Gi1/0/1–3 form EtherChannel Group 1.

LACP passive negotiation is used.

The logical interface is Port-Channel 1.

Port-Channel 1 uses 192.168.1.2/24.

The active/passive combination between Switch0 and Switch1 allows LACP to negotiate the EtherChannel.

EtherChannel Group 3 — Static ON

Interfaces Gi1/0/4–6 form EtherChannel Group 3.

Static ON mode is used.

The logical interface is Port-Channel 3.

Port-Channel 3 uses 192.168.3.1/24.

Multilayer Switch2

Multilayer Switch2 participates in the PAgP and static EtherChannel connections.

Layer 3 Preparation

IP routing is enabled.

GigabitEthernet interfaces Gi1/0/1–6 are converted to routed interfaces.

EtherChannel Group 2 — PAgP

Interfaces Gi1/0/1–3 form EtherChannel Group 2.

PAgP auto mode is used.

The logical interface is Port-Channel 2.

Port-Channel 2 uses 192.168.2.2/24.

The PAgP desirable/auto relationship provides negotiation for the EtherChannel connection.

EtherChannel Group 3 — Static ON

Interfaces Gi1/0/4–6 form EtherChannel Group 3.

Static ON mode is used.

The logical interface is Port-Channel 3.

Port-Channel 3 uses 192.168.3.2/24.

IP Addressing

Device

Port-Channel

IP Address

Network

Multilayer Switch0

Port-Channel 1

192.168.1.1/24

192.168.1.0/24

Multilayer Switch1

Port-Channel 1

192.168.1.2/24

192.168.1.0/24

Multilayer Switch0

Port-Channel 2

192.168.2.1/24

192.168.2.0/24

Multilayer Switch2

Port-Channel 2

192.168.2.2/24

192.168.2.0/24

Multilayer Switch1

Port-Channel 3

192.168.3.1/24

192.168.3.0/24

Multilayer Switch2

Port-Channel 3

192.168.3.2/24

192.168.3.0/24

EtherChannel Technologies

LACP — Link Aggregation Control Protocol

LACP is an IEEE-standard EtherChannel negotiation protocol.

In this lab:

Switch0 uses LACP Active.

Switch1 uses LACP Passive.

The active side initiates negotiation, while the passive side responds to LACP negotiation.

PAgP — Port Aggregation Protocol

PAgP is a Cisco proprietary EtherChannel negotiation protocol.

The lab demonstrates a desirable/auto PAgP relationship between the relevant switches.

Desirable actively participates in negotiation.

Auto waits for negotiation from the other side.

Static ON Mode

ON mode creates an EtherChannel without using LACP or PAgP negotiation.

Both sides must be configured consistently because there is no negotiation protocol to verify compatibility.

Layer 3 EtherChannel

Unlike a traditional Layer 2 EtherChannel, this lab uses the EtherChannel as a routed Layer 3 interface.

The physical member interfaces are converted to Layer 3 interfaces, and IP addressing is applied to the Port-Channel interfaces.

This creates a logical routed connection while combining multiple physical links into one logical interface.

Verification

The lab includes EtherChannel verification using Cisco IOS operational checks.

The configuration can be verified by checking:

Port-Channel status

EtherChannel member interfaces

LACP/PAgP negotiation state

Layer 3 interface status

IP addressing

Routing information

Connectivity between the configured Port-Channel endpoints

The topology also provides connectivity testing between the Layer 3 EtherChannel endpoints.

Benefits of EtherChannel

EtherChannel provides several important networking benefits:

Increased bandwidth by combining multiple physical links.

Redundancy if one member link fails.

Load distribution across aggregated links.

Simplified management because multiple physical links operate as one logical interface.

Improved network availability in environments requiring resilient connectivity.

Key Concepts Demonstrated

Layer 3 Multilayer Switching

IP Routing

Routed Interfaces

EtherChannel

LACP

PAgP

Static EtherChannel

Port-Channel Interfaces

IPv4 Addressing

Link Aggregation

Network Redundancy

Link Negotiation

Expected Result

After the configuration is correctly completed:

All intended physical links should participate in their respective EtherChannel groups.

The Port-Channels should operate as logical Layer 3 interfaces.

LACP Group 1 should establish using active/passive negotiation.

PAgP Group 2 should establish using desirable/auto negotiation.

Group 3 should operate as a static ON-mode EtherChannel.

The configured Port-Channel IP addresses should provide Layer 3 connectivity between the connected switches.

Tools & Technologies

Cisco Packet Tracer

Cisco 3650-24PS Multilayer Switch

Cisco IOS

IPv4

Layer 3 Routing

EtherChannel

LACP

PAgP

Project Files

LAB-20-Layer-3-EtherChannel.pkt
LAB-20-README.md
LAB-20-commands.txt

Conclusion

This lab provides a practical demonstration of Layer 3 EtherChannel configuration using three different approaches: LACP, PAgP, and static ON mode.

By converting the physical interfaces to routed interfaces and assigning IP addresses to Port-Channels, the lab demonstrates how multiple physical links can be combined into logical Layer 3 connections while improving bandwidth utilization and network resiliency.

Lab: 20
Topic: Layer 3 EtherChannel — LACP, PAgP & ON Modes
Platform: Cisco Packet Tracer
Focus: Link Aggregation, Layer 3 Switching & Network Redundancy