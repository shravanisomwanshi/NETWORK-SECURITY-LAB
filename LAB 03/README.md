# VLAN Configuration Step-by-Step Using Cisco Packet Tracer

## 📌 Lab Overview

This lab demonstrates how to create and configure multiple VLANs on two Cisco 2960 switches using Cisco Packet Tracer.

Three VLANs are configured:

* VLAN 10 → IT
* VLAN 20 → HR
* VLAN 30 → FIN

The two switches are connected through a **trunk link**, allowing multiple VLANs to pass between the switches.

---

## 🎯 Objectives

The objectives of this lab are:

* Create VLANs on Cisco switches.
* Assign names to VLANs.
* Assign switch ports to specific VLANs.
* Configure access ports.
* Configure a trunk port between two switches.
* Verify VLAN configuration.
* Verify the VLANs on both switches.
* Save the switch configuration.

---

## 🖥️ Topology

The topology contains:

* 2 × Cisco 2960 switches
* 12 × PCs
* 3 VLANs
* 1 trunk connection between the switches

```text
                         TRUNK LINK
                  Fa0/1  =========  Fa0/1
                 +--------+       +--------+
                 | Switch1|       | Switch2|
                 +--------+       +--------+
                  /   |   \         /  |  \
                 /    |    \       /   |   \
              VLAN10 VLAN20 VLAN30 VLAN10 VLAN20 VLAN30
```

---

## 🌐 VLAN and Network Information

| VLAN | Name | Network         |
| ---- | ---- | --------------- |
| 10   | IT   | 192.168.10.0/24 |
| 20   | HR   | 192.168.20.0/24 |
| 30   | FIN  | 192.168.30.0/24 |

---

## 💻 PC Addressing

### VLAN 10 — IT

| PC  | IP Address   |
| --- | ------------ |
| PC0 | 192.168.10.1 |
| PC1 | 192.168.10.2 |
| PC8 | 192.168.10.3 |
| PC9 | 192.168.10.4 |

### VLAN 20 — HR

| PC  | IP Address   |
| --- | ------------ |
| PC2 | 192.168.20.1 |
| PC3 | 192.168.20.2 |
| PC6 | 192.168.20.3 |
| PC7 | 192.168.20.4 |

### VLAN 30 — FIN

| PC   | IP Address   |
| ---- | ------------ |
| PC4  | 192.168.30.1 |
| PC5  | 192.168.30.2 |
| PC10 | 192.168.30.3 |
| PC11 | 192.168.30.4 |

> Note: No default gateway is configured in this lab because the topology does not contain a router or Layer-3 switch. Therefore, communication is demonstrated within the same VLAN/subnet.

---

# ⚙️ Switch 1 Configuration

## VLAN Creation

### VLAN 10 — IT

```text
enable
configure terminal
vlan 10
name IT
exit
```

### VLAN 20 — HR

```text
vlan 20
name HR
exit
```

### VLAN 30 — FIN

```text
vlan 30
name FIN
exit
```

---

## Switch 1 Access Port Configuration

### VLAN 10 — Fa0/1 and Fa0/2

```text
interface range fa0/1 - 2
switchport mode access
switchport access vlan 10
exit
```

### VLAN 20 — Fa0/3 and Fa0/4

```text
interface range fa0/3 - 4
switchport mode access
switchport access vlan 20
exit
```

### VLAN 30 — Fa0/5 and Fa0/6

```text
interface range fa0/5 - 6
switchport mode access
switchport access vlan 30
exit
```

---

# ⚙️ Switch 2 Configuration

## VLAN Creation

```text
enable
configure terminal

vlan 10
name IT
exit

vlan 20
name HR
exit

vlan 30
name FIN
exit
```

## Switch 2 Access Port Configuration

### VLAN 10 — Fa0/4 and Fa0/5

```text
interface range fa0/4 - 5
switchport mode access
switchport access vlan 10
exit
```

### VLAN 20 — Fa0/2 and Fa0/3

```text
interface range fa0/2 - 3
switchport mode access
switchport access vlan 20
exit
```

### VLAN 30 — Fa0/6 and Fa0/7

```text
interface range fa0/6 - 7
switchport mode access
switchport access vlan 30
exit
```

---

# 🔗 Trunk Configuration

The connection between Switch 1 and Switch 2 is configured as a trunk.

### Switch 1

```text
interface fa0/7
switchport mode trunk
exit
```

### Switch 2

```text
interface fa0/1
switchport mode trunk
exit
```

The trunk allows VLAN 10, VLAN 20 and VLAN 30 traffic to travel between the two switches.

---

# 🔍 Verification

To display the VLAN configuration:

```text
show vlan brief
```

To verify trunking:

```text
show interfaces trunk
```

To check the status of interfaces:

```text
show ip interface brief
```

To check the running configuration:

```text
show running-config
```

---

# 🧪 Connectivity Testing

### Same VLAN Testing

For example:

```text
PC0 → PC1
```

Both PCs belong to VLAN 10.

They should be able to communicate because they are in the same VLAN and same subnet.

Similarly:

```text
PC2 → PC3
```

Both belong to VLAN 20.

And:

```text
PC4 → PC5
```

Both belong to VLAN 30.

The corresponding PCs connected to the second switch can also communicate through the trunk link.

---

# 🧠 Important Concepts

## Access Port

An access port normally carries traffic belonging to a single VLAN.

Example:

```text
switchport mode access
switchport access vlan 10
```

## Trunk Port

A trunk port carries traffic for multiple VLANs between network devices.

Example:

```text
switchport mode trunk
```

## VLAN

VLAN stands for **Virtual Local Area Network**.

It logically divides a physical switch network into separate broadcast domains.

### VLANs Used

```text
VLAN 10 → IT
VLAN 20 → HR
VLAN 30 → FIN
```

---

# ✅ Result

The VLAN configuration was successfully completed using Cisco Packet Tracer.

The lab includes:

* VLAN 10 — IT
* VLAN 20 — HR
* VLAN 30 — FIN
* Access port configuration
* Trunk configuration
* VLAN verification
* Connectivity testing

The trunk link between the two switches allows the configured VLANs to extend across both switches.

---

## 🛠️ Tool Used

**Cisco Packet Tracer**

## 📚 Lab Type

**VLAN Configuration and Trunking**
