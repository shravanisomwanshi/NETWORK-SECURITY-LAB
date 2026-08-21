# Trunk Allowed / Denied VLANs Configuration Using Cisco Packet Tracer

## 📌 Lab Overview

This lab demonstrates how to configure **allowed and denied VLANs on trunk interfaces** using Cisco Packet Tracer.

The topology consists of two Cisco 2960 switches connected through trunk links.

Five VLANs are configured:

* VLAN 10 → IT
* VLAN 20 → HR
* VLAN 30 → FIN
* VLAN 40 → HACKER1
* VLAN 50 → HACKER2

The lab demonstrates how specific VLANs can be prevented from passing through a trunk link using the `switchport trunk allowed vlan` command.

---

## 🎯 Objectives

The objectives of this lab are:

* Create VLANs on Cisco switches.
* Assign names to VLANs.
* Configure access ports.
* Configure trunk ports.
* Allow specific VLANs on trunk links.
* Deny a specific VLAN from a trunk link.
* Verify allowed VLANs using `show interfaces trunk`.
* Understand the effect of VLAN filtering on trunk communication.

---

# 🖥️ Topology

The topology contains:

* 2 × Cisco 2960 switches
* 6 × PCs
* 5 VLANs
* 2 trunk links between Switch1 and Switch2

```text
                         TRUNK LINKS
                 Fa0/1 ================= Fa0/2
                 Fa0/2 ================= Fa0/1

              +------------+       +------------+
              |  Switch1   |       |  Switch2   |
              +------------+       +------------+
               /    |    \          /    |    \
              /     |     \        /     |     \
          VLAN 10 VLAN 20 VLAN 30 VLAN 20 VLAN 30 VLAN 10
```

---

# 🌐 VLAN Information

| VLAN ID | VLAN Name | Network              |
| ------: | --------- | -------------------- |
|      10 | IT        | 192.168.10.0/24      |
|      20 | HR        | 192.168.20.0/24      |
|      30 | FIN       | 192.168.30.0/24      |
|      40 | HACKER1   | Not assigned to a PC |
|      50 | HACKER2   | Not assigned to a PC |

---

# 💻 PC Configuration

## Switch1

### VLAN 10 — IT

PC0:

```text
192.168.10.10/24
```

### VLAN 20 — HR

PC1:

```text
192.168.20.10/24
```

### VLAN 30 — FIN

PC2:

```text
192.168.30.10/24
```

---

## Switch2

### VLAN 20 — HR

PC3:

```text
192.168.20.20/24
```

### VLAN 30 — FIN

PC4:

```text
192.168.30.20/24
```

### VLAN 10 — IT

PC5:

```text
192.168.10.20/24
```

> Note: The screenshot shows the same `192.168.10.10` label for PC0 and PC5. The lab focuses on VLAN/trunk configuration rather than routed IP communication, so the IP labels are documented as shown in the topology.

---

# ⚙️ Switch1 Configuration

## Step 1 — Create VLANs

### VLAN 10

```text
vlan 10
name IT
exit
```

### VLAN 20

```text
vlan 20
name HR
exit
```

### VLAN 30

```text
vlan 30
name FIN
exit
```

### VLAN 40

```text
vlan 40
name HACKER1
exit
```

### VLAN 50

```text
vlan 50
name HACKER2
exit
```

---

## Step 2 — Configure Access Ports

### VLAN 10 — Fa0/3

```text
interface fa0/3
switchport mode access
switchport access vlan 10
exit
```

### VLAN 20 — Fa0/4

```text
interface fa0/4
switchport mode access
switchport access vlan 20
exit
```

### VLAN 30 — Fa0/5

```text
interface fa0/5
switchport mode access
switchport access vlan 30
exit
```

---

## Step 3 — Configure Trunk Ports

The two links between Switch1 and Switch2 use Fa0/1 and Fa0/2.

```text
interface range fa0/1 - 2
switchport mode trunk
exit
```

---

## Step 4 — Verify Trunk

```text
show interfaces trunk
```

---

## Step 5 — Deny VLAN 50 on Switch1 Trunk

According to the lab configuration, VLAN 50 is excluded from the trunk.

```text
interface range fa0/1 - 2
switchport trunk allowed vlan except 50
exit
```

Verify:

```text
do show interfaces trunk
```

---

# ⚙️ Switch2 Configuration

## Step 1 — Create VLANs

### VLAN 10

```text
vlan 10
name IT
exit
```

### VLAN 20

```text
vlan 20
name HR
exit
```

### VLAN 30

```text
vlan 30
name FIN
exit
```

### VLAN 40

```text
vlan 40
name HACKER1
exit
```

### VLAN 50

```text
vlan 50
name HACKER2
exit
```

---

## Step 2 — Configure Access Ports

### VLAN 10 — Fa0/3

```text
interface fa0/3
switchport mode access
switchport access vlan 10
exit
```

### VLAN 20 — Fa0/4

```text
interface fa0/4
switchport mode access
switchport access vlan 20
exit
```

### VLAN 30 — Fa0/5

```text
interface fa0/5
switchport mode access
switchport access vlan 30
exit
```

---

## Step 3 — Configure Trunk Ports

```text
interface range fa0/1 - 2
switchport mode trunk
exit
```

---

## Step 4 — Verify Trunk

```text
show interfaces trunk
```

---

## Step 5 — Deny VLAN 10 on Switch2 Trunk

According to the topology configuration, VLAN 10 is excluded from the trunk on Switch2.

```text
interface range Fa0/2-1
switchport trunk allowed vlan except 10
exit
```

Verify:

```text
do show interfaces trunk
```

---

# 🔐 Allowed / Denied VLAN Configuration

The important configuration in this lab is:

### Switch1

```text
switchport trunk allowed vlan except 50
```

This means VLAN 50 is excluded from the allowed VLAN list on the trunk.

### Switch2

```text
switchport trunk allowed vlan except 10
```

This means VLAN 10 is excluded from the allowed VLAN list on the trunk.

---

# 🔍 Verification Commands

## Check VLANs

```text
show vlan brief
```

This displays VLAN IDs, VLAN names, status, and assigned access ports.

---

## Check Trunk Configuration

```text
show interfaces trunk
```

This is the most important command for this lab.

It displays:

* Trunk ports
* Trunk status
* Encapsulation
* Native VLAN
* Allowed VLANs
* Active VLANs
* VLANs forwarding through STP

---

## Check Running Configuration

```text
show running-config
```

---

# 🧪 Connectivity Testing

The purpose of this lab is to understand how allowed and denied VLANs affect trunk traffic.

### VLAN 20

PC1 and PC3 belong to VLAN 20.

```text
PC1 → PC3
```

VLAN 20 is allowed through the trunk, so VLAN 20 traffic can cross the trunk.

### VLAN 30

PC2 and PC4 belong to VLAN 30.

```text
PC2 → PC4
```

VLAN 30 is allowed through the trunk, so VLAN 30 traffic can cross the trunk.

### VLAN 10

PC0 and PC5 belong to VLAN 10.

However, VLAN 10 is denied on the Switch2 trunk:

```text
switchport trunk allowed vlan except 10
```

Therefore, VLAN 10 traffic is prevented from crossing that trunk configuration.

---

# 🧠 Important Concepts

## Access Port

An access port carries traffic for a single VLAN.

Example:

```text
switchport mode access
switchport access vlan 10
```

---

## Trunk Port

A trunk port can carry traffic belonging to multiple VLANs.

Example:

```text
switchport mode trunk
```

---

## Allowed VLAN

The `switchport trunk allowed vlan` command controls which VLANs are permitted to travel through a trunk.

---

## VLAN Exception

The following command excludes a VLAN:

```text
switchport trunk allowed vlan except 50
```

It means VLAN 50 is not permitted on that trunk.

---

# 📊 Configuration Summary

| Switch  | Port    | Type   | VLAN             |
| ------- | ------- | ------ | ---------------- |
| Switch1 | Fa0/3   | Access | VLAN 10          |
| Switch1 | Fa0/4   | Access | VLAN 20          |
| Switch1 | Fa0/5   | Access | VLAN 30          |
| Switch1 | Fa0/1-2 | Trunk  | VLAN 50 excluded |
| Switch2 | Fa0/3   | Access | VLAN 10          |
| Switch2 | Fa0/4   | Access | VLAN 20          |
| Switch2 | Fa0/5   | Access | VLAN 30          |
| Switch2 | Fa0/2-1 | Trunk  | VLAN 10 excluded |

---

# ✅ Result

The trunk allowed/denied VLAN configuration was successfully implemented using Cisco Packet Tracer.

The lab demonstrates:

* VLAN creation
* VLAN naming
* Access port configuration
* Trunk configuration
* VLAN filtering on trunk links
* Allowed VLAN verification
* Denied VLAN configuration
* Trunk verification

---

## 🛠️ Tool Used

**Cisco Packet Tracer**

## 📚 Lab Type

**Trunk Allowed / Denied VLAN Configuration**
