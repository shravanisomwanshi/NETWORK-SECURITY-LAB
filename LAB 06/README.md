# 802.1Q Trunk Native VLAN Configuration Using Cisco Packet Tracer

## 📌 Lab Overview

This lab demonstrates the configuration of an **802.1Q trunk link with a Native VLAN** using Cisco Packet Tracer.

In this topology, two Cisco 2960 switches are connected using two trunk links. VLAN 99 is configured as the **Native VLAN** on the trunk interfaces.

The lab also demonstrates the creation of VLAN 10, VLAN 20, and VLAN 99.

---

## 🎯 Objectives

The objectives of this lab are:

- Understand 802.1Q trunking.
- Create VLANs on Cisco switches.
- Configure trunk ports.
- Configure VLAN 99 as the Native VLAN.
- Verify trunk configuration.
- Understand the purpose of a Native VLAN.
- Use `show interfaces trunk` for verification.

---

## 🖥️ Topology

The topology contains:

- 2 × Cisco 2960 switches
- 2 × PCs
- 2 × trunk links between the switches

### Topology Structure

```text
                    802.1Q TRUNK
              Fa0/1 ================= Fa0/1
              Fa0/2 ================= Fa0/2

             +------------+       +------------+
             |  Switch1   |       |  Switch2   |
             +------------+       +------------+
                   |                    |
                 Fa0/3                Fa0/3
                   |                    |
                  PC0                  PC1