# 🔗 EtherChannel Configuration Using Manual "ON" Mode

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of **EtherChannel using the manual `ON` mode**.

EtherChannel combines multiple physical links between switches into a single logical **Port-Channel**, providing:

- Increased bandwidth
- Link redundancy
- Better network availability
- Simplified STP management

In this topology, three Cisco 2960 switches are interconnected using multiple physical links. These links are bundled into EtherChannel groups using the manual `ON` mode.

---

## 🎯 Objectives

- Understand the concept of EtherChannel.
- Configure EtherChannel using manual `ON` mode.
- Create multiple Port-Channels between switches.
- Configure the Port-Channels as trunk links.
- Verify EtherChannel status using Cisco IOS commands.

---

## 🖥️ Network Topology

The topology consists of **three Cisco 2960 switches** connected in a triangular arrangement.

```text
                         ┌───────────────┐
                         │      S1       │
                         │ Cisco 2960    │
                         └───────┬───────┘
                           ╱     │     ╲
                         ╱       │       ╲
                       ╱         │         ╲
                     ╱           │           ╲
             Port-Channel 1      │      Port-Channel 2
                   ╱              │
                 ╱                │
               ╱                  │
        ┌──────┴──────┐           │
        │     S3      │           │
        │ Cisco 2960  │           │
        └──────┬──────┘           │
               ╲                  ╱
                ╲                ╱
                 ╲              ╱
                  └────────────┘
                  Port-Channel 3

                         S2
                    Cisco 2960

### Devices Used

| Device | Quantity |
|--------|----------|
| Cisco 2960 Switch | 3 |
| Physical Links | Multiple |
| EtherChannel Groups | 3 |

### Switches

- **S1**
- **S2**
- **S3**

### EtherChannel Connections

| EtherChannel | Switches | Interfaces | Channel Group |
|-------------|----------|------------|---------------|
| Port-Channel 1 | S1 ↔ S2 | Fa0/1-2 | Group 1 |
| Port-Channel 2 | S1 ↔ S3 | Fa0/4-5 | Group 2 |
| Port-Channel 3 | S2 ↔ S3 | Fa0/4-6 | Group 3 |

> Note: Interface numbers should match the actual Packet Tracer topology.

---

# ⚙️ Configuration

## 🔵 S1 Configuration

### EtherChannel Group 1 — S1 ↔ S2

```bash
enable
configure terminal

interface range fa0/1-2
channel-group 1 mode on
exit

interface port-channel 1
switchport mode trunk
exit

do write
