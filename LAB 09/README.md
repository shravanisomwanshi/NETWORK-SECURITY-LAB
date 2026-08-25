# 🔗 EtherChannel Configuration Using PAgP

## 📌 Overview

This Cisco Packet Tracer lab demonstrates the configuration of
**EtherChannel using PAgP (Port Aggregation Protocol)**.

EtherChannel combines multiple physical links into a single logical
link called a **Port-Channel**. This provides increased bandwidth
and link redundancy between network switches.

---

## 🎯 Objectives

- Configure EtherChannel using PAgP.
- Create two PAgP channel groups.
- Configure PAgP negotiation modes.
- Configure Port-Channel interfaces as trunk ports.
- Verify EtherChannel status.
- Understand `desirable` and `auto` PAgP modes.

---

## 🖥️ Topology

```text
                         MLS1
                    ┌─────────────┐
                    │  Layer 3    │
                    │   Switch    │
                    └──────┬──────┘
                           │
                ┌──────────┴──────────┐
                │                     │
          PAgP Channel 1        PAgP Channel 2
          GI0/1 - GI0/3         GI1/0/4 - GI1/0/6
                │                     │
          ┌─────┴─────┐         ┌─────┴─────┐
          │  Switch2  │         │  Switch1  │
          └───────────┘         └───────────┘



🔧 EtherChannel Configuration
Channel Group 1

MLS1:

Interfaces: Gi0/1 - Gi0/3
PAgP Mode: auto
Port-Channel: Port-Channel 1

Switch2:

Interfaces: Fa0/1 - Fa0/3
PAgP Mode: desirable
Port-Channel: Port-Channel 1
Channel Group 2

MLS1:

Interfaces: Gi1/0/4 - Gi1/0/6
PAgP Mode: auto
Port-Channel: Port-Channel 2

Switch1:

Interfaces: Fa0/1 - Fa0/3
PAgP Mode: desirable
Port-Channel: Port-Channel 2          