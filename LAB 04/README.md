# VLAN Trunking Protocol (VTP) Configuration Step-by-Step

## 📌 Lab Overview

This lab demonstrates the configuration of **VLAN Trunking Protocol (VTP)** using Cisco Packet Tracer.

VTP is used to centrally manage VLAN information across multiple Cisco switches.

In this topology:

* **Switch2** is configured as the VTP Server.
* **Switch1** is configured as a VTP Client.
* **Switch3** is configured as a VTP Client.
* **Switch4** is configured as a VTP Client.
* **Switch5** is configured as a VTP Client.

The switches are connected using trunk links so that VTP advertisements can travel between the switches.

---

## 🎯 Objectives

The objectives of this lab are:

* Understand the purpose of VTP.
* Configure a VTP Server.
* Configure VTP Clients.
* Configure VTP domain.
* Configure VTP password.
* Configure VTP version 2.
* Configure trunk links between switches.
* Create VLANs on the VTP Server.
* Verify VLAN propagation to VTP Clients.
* Verify trunk configuration.
* Save the switch configurations.

---

# 🖥️ Topology

The topology contains:

* 5 × Cisco 2960-24TT switches
* 2 × PCs
* 1 × VTP Server
* 4 × VTP Clients

### Switch Roles

| Switch  | VTP Role   |
| ------- | ---------- |
| Switch1 | VTP Client |
| Switch2 | VTP Server |
| Switch3 | VTP Client |
| Switch4 | VTP Client |
| Switch5 | VTP Client |

---

## 🔗 Topology Connections

```text
                         Switch1
                       VTP Client
                       Fa0/1-2
                          / \
                         /   \
                        /     \
                       /       \
                      /         \
               Switch2           Switch3
             VTP Server        VTP Client
             Fa0/1-2           Fa0/1-2
                 \               /
                  \             /
                   \           /
                    \         /
                     Switch4
                    VTP Client
                    Fa0/1-3
                        |
                        |
                     Switch5
                    VTP Client
                    Fa0/1
```

The exact physical topology follows the Packet Tracer lab shown in the screenshot.

---

# 🟡 VTP Server — Switch2

Switch2 acts as the central VTP Server.

The following VTP settings are configured:

| Parameter    | Value     |
| ------------ | --------- |
| VTP Mode     | Server    |
| VTP Domain   | cisco.com |
| VTP Password | cisco     |
| VTP Version  | 2         |

---

# 🏷️ VLANs Created on VTP Server

The following VLANs are created on Switch2:

| VLAN ID | VLAN Name |
| ------: | --------- |
|      10 | IT        |
|      20 | HR        |
|      30 | FIN       |
|      40 | AD        |
|      50 | PRO       |

Because Switch2 is the VTP Server, these VLAN definitions can be advertised to the VTP Clients through the trunk links.

---

# 🔗 Trunk Configuration

Trunking is required between the switches so that VTP advertisements and VLAN traffic can travel between them.

### Switch2 — VTP Server

```text
interface range fa0/1 - 2
switchport mode trunk
```

### Switch1 — VTP Client

```text
interface range fa0/1 - 2
switchport mode trunk
```

### Switch3 — VTP Client

```text
interface range fa0/1 - 2
switchport mode trunk
```

### Switch4 — VTP Client

```text
interface range fa0/1 - 3
switchport mode trunk
```

### Switch5 — VTP Client

```text
interface range fa0/1 
switchport mode trunk
```

---

# ⚙️ VTP Server Configuration

Switch2 is configured as the VTP Server.

### VTP Settings

```text
vtp mode server
vtp domain cisco.com
vtp password cisco
vtp version 2
```

---

# 🏷️ VLAN Configuration on VTP Server

The VLANs are created only on the VTP Server:

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
name AD
exit
```

### VLAN 50

```text
vlan 50
name PRO
exit
```

---

# 🔵 VTP Client Configuration

The following switches are configured as VTP Clients:

* Switch1
* Switch3
* Switch4
* Switch5

Each client uses the same:

```text
VTP Domain: cisco.com
VTP Password: cisco
VTP Version: 2
```

### Client configuration

```text
vtp mode client
vtp domain cisco.com
vtp password cisco
vtp version 2
```

---

# 🔍 Verification

## 1. Verify VLANs

Use:

```text
show vlan brief
```

On the VTP Server, the following VLANs should appear:

```text
10  IT
20  HR
30  FIN
40  AD
50  PRO
```

After successful VTP propagation, the same VLANs should also appear on the VTP Client switches.

---

## 2. Verify VTP Status

Use:

```text
show vtp status
```

This command displays:

* VTP operating mode
* VTP domain name
* VTP version
* Configuration revision
* Number of existing VLANs
* VTP server/client status

---

## 3. Verify VTP Password

The configured VTP password can be checked through the VTP configuration/status information.

---

## 4. Verify Trunk Links

Use:

```text
show interfaces trunk
```

The trunk interfaces should display:

```text
Status: trunking
```

---

# 🧪 Expected Result

After configuring VTP:

```text
Switch2
   |
   | VTP Server
   |
   +---- VLAN 10 IT
   +---- VLAN 20 HR
   +---- VLAN 30 FIN
   +---- VLAN 40 AD
   +---- VLAN 50 PRO
             |
             | VTP Advertisements
             ↓
      VTP Client Switches
```

The VLAN information created on the VTP Server should propagate to the VTP Client switches through the trunk links.

---

# 🧠 Important Concepts

## What is VTP?

**VLAN Trunking Protocol (VTP)** is a Cisco proprietary protocol used to distribute VLAN information between switches in the same VTP domain.

## VTP Server

The VTP Server is responsible for creating, modifying, and deleting VLAN information in a VTP domain.

## VTP Client

A VTP Client receives VLAN information from the VTP Server.

## VTP Domain

All participating switches must use the same VTP domain.

In this lab:

```text
cisco.com
```

## VTP Password

The switches use the same password:

```text
cisco
```

## VTP Version

This lab uses:

```text
VTP Version 2
```

## Trunk

A trunk link carries traffic belonging to multiple VLANs between switches.

---

# ⚠️ Important Note

VTP requires proper trunk connectivity between participating switches.

Therefore, always verify the trunk links before troubleshooting VTP:

```text
show interfaces trunk
```

Then verify VTP:

```text
show vtp status
```

Finally verify VLAN propagation:

```text
show vlan brief
```

---

# ✅ Result

The VTP network was successfully configured with:

* 1 VTP Server
* 4 VTP Clients
* VTP Domain: `cisco.com`
* VTP Password: `cisco`
* VTP Version: 2
* VLAN 10 — IT
* VLAN 20 — HR
* VLAN 30 — FIN
* VLAN 40 — AD
* VLAN 50 — PRO
* Trunk links between switches

The VLAN information can be centrally managed from the VTP Server and propagated to the VTP Client switches.

---

## 🛠️ Tool Used

**Cisco Packet Tracer**

## 📚 Lab Type

**VLAN Trunking Protocol (VTP) and Trunk Configuration**
