# 🔐 Remote Access Using SSH – Cisco Packet Tracer

## 📌 Project Overview

This lab demonstrates how to configure **Secure Shell (SSH) remote access**
on a Cisco switch using Cisco Packet Tracer.

The router provides connectivity between the Admin PC network and the
remote switch management network. SSH is configured on the switch so that
the administrator can securely manage the switch remotely.

---

## 🎯 Objectives

- Configure router interfaces with IP addresses.
- Configure Switch Management VLAN.
- Configure Switch Default Gateway.
- Configure hostname and domain name.
- Create a local SSH user.
- Generate RSA cryptographic keys.
- Enable SSH Version 2.
- Configure VTY lines for SSH access.
- Verify remote SSH connectivity.

---

## 🖥️ Network Topology

```text
                    ROUTER
                  ┌─────────┐
                  │ 2911    │
                  └────┬────┘
                       │
              G0/0     │     G0/1
        192.168.1.1/24 │ 192.168.2.1/24
                       │
              ┌────────┴────────┐
              │                 │
          ADMIN-PC           SWITCH S1
       192.168.1.10       192.168.2.254
                              │
                         ┌────┴────┐
                         │         │
                      USER-1    USER-2
                    .10         .20