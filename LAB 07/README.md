# Remote Access Using Telnet – Cisco Packet Tracer

## 📌 Overview

This Cisco Packet Tracer lab demonstrates how to configure **remote device
management using Telnet**.

In this topology, a Cisco Router connects two different IP networks.
The Router provides connectivity between the Admin PC network and the
Remote Management network.

A Cisco 2960 switch is configured with a management IP address and
Telnet access so that the switch can be remotely accessed from a PC.

---

## 🎯 Objectives

The main objectives of this lab are:

- Configure Router interfaces with IPv4 addresses.
- Configure a Layer 2 switch management IP address.
- Configure the switch default gateway.
- Configure hostname and domain name.
- Create a local username and password.
- Enable Telnet access on VTY lines.
- Configure local authentication for Telnet.
- Configure an enable password.
- Verify Telnet connectivity from a remote PC.

---

## 🖥️ Network Topology

```text
                         Cisco Router
                            2911
                       ┌─────────────┐
                       │             │
          G0/0         │             │         G0/1
     192.168.1.1       │   Router    │      192.168.2.1
           ────────────┤             ├────────────
                       │             │
                       └─────────────┘
                              |
                              |
                         192.168.2.0/24
                              |
                       ┌─────────────┐
                       │   Switch    │
                       │     S1      │
                       │ 192.168.2.254
                       └─────────────┘
                         /           \
                        /             \
                     PC USER-1      PC USER-2
                  192.168.2.10    192.168.2.20


Admin Network:

        ┌────────────────────┐
        │      ADMIN-PC      │
        │   192.168.1.10     │
        │    /24             │
        └─────────┬──────────┘
                  │
                  │
             G0/0 Router
             192.168.1.1