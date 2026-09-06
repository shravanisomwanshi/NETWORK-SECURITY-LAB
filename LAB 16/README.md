# LAB 16 — IPSG + DAI + DHCP Snooping Configuration

## 📌 Overview

This Cisco Packet Tracer lab demonstrates three important Layer 2 security mechanisms:

- **DHCP Snooping**
- **Dynamic ARP Inspection (DAI)**
- **IP Source Guard (IPSG)**

The topology contains a router, one switch, client PCs, a legitimate DHCP server, and a fake/rogue DHCP server. The switch is configured to trust the required interfaces and apply DHCP Snooping, ARP Inspection, and IP Source Guard controls as shown in the Packet Tracer topology.

## 🎯 Objectives

- Configure DHCP Snooping on the switch.
- Define trusted interfaces for legitimate DHCP traffic.
- Enable DHCP Snooping for VLAN 1.
- Configure Dynamic ARP Inspection for VLAN 1.
- Configure ARP inspection trust on the specified interfaces.
- Enable IP Source Guard using `ip verify source`.
- Verify the security configurations.
- Save the switch configuration.

## 🖥️ Topology Components

| Device | Role |
|---|---|
| Router R0 | Network gateway |
| Switch | Layer 2 security enforcement |
| PC0, PC1, PC2 | Network clients |
| Legitimate DHCP Server | Authorized DHCP service |
| Fake DHCP Server | Rogue/unauthorized DHCP server |

## 🌐 Addressing / DHCP Information

### Legitimate DHCP Server
- IP Address: `192.168.1.100`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- DHCP Pool: `TESTPOOL`
- DHCP Default: `192.168.1.1`
- DHCP IP: `192.168.1.10`

### Fake DHCP Server
- IP Address: `192.168.1.100`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`

### VLAN
- VLAN ID: `1`

## 🔐 Configuration Implemented

### 1. DHCP Snooping — Switch

DHCP Snooping is enabled on the switch to control DHCP traffic and distinguish trusted DHCP paths from untrusted paths.

**Configured on:**
- Switch
- VLAN 1
- Interfaces `Fa0/1`–`Fa0/2` are configured as DHCP Snooping trusted interfaces.

**Why:**
The topology contains both a legitimate DHCP server and a fake DHCP server. DHCP Snooping is used to help prevent unauthorized DHCP responses from being accepted by the network.

### 2. Dynamic ARP Inspection (DAI) — Switch

Dynamic ARP Inspection is enabled for **VLAN 1**.

**Configured on:**
- Switch
- VLAN 1
- Interfaces `Fa0/1`–`Fa0/2` are configured for ARP inspection trust.

**Why:**
DAI is used to inspect ARP traffic and provide protection against malicious or invalid ARP information.

### 3. IP Source Guard (IPSG) — Switch

IP Source Guard is configured using:

`ip verify source`

**Configured on:**
- Switch
- Interfaces `Fa0/1`–`Fa0/2`

**Why:**
IP Source Guard helps restrict IP traffic to the permitted source information associated with the interface.

> **Note:** The interfaces and configuration documented here follow the configuration shown in the provided Packet Tracer topology.

## 🔎 Verification

The lab includes verification of:

- VLAN configuration
- DHCP Snooping configuration
- DHCP Snooping status for VLAN 1
- Startup configuration
- ARP Inspection configuration
- ARP Inspection interface status
- IP Source Guard configuration

## 🧠 Security Concepts Learned

This lab provides practical exposure to Layer 2 security controls:

**DHCP Snooping → DAI → IP Source Guard**

DHCP Snooping establishes trusted DHCP information, while DAI and IP Source Guard use security information associated with the network to help control malicious or unauthorized traffic.

## 🛠️ Tool Used

- Cisco Packet Tracer

## ✅ Learning  Outcome

The switch should have DHCP Snooping enabled for VLAN 1, the specified interfaces configured as trusted for DHCP Snooping and ARP Inspection, and IP Source Guard enabled on the specified interfaces. The final configuration is saved using the appropriate write command.
