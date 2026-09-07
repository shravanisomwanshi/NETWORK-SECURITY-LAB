# LAB — Port Security Configuration

## Overview

This Cisco Packet Tracer lab demonstrates **Switch Port Security** using different security settings on access ports.

The topology contains one Cisco switch, multiple PCs, and a separate Hacker-PC scenario. Port Security is configured on different switch interfaces with different maximum MAC-address limits, MAC learning methods, and violation actions.

The lab demonstrates three Port Security violation modes:

- `shutdown`
- `restrict`
- `protect`

It also demonstrates **sticky MAC address learning** and **manual static MAC address configuration**.

---

## Objectives

- Configure switch interfaces as access ports.
- Enable Port Security on selected interfaces.
- Limit the number of MAC addresses allowed on a port.
- Use sticky MAC learning.
- Configure a static secure MAC address.
- Understand Port Security violation modes.
- Verify Port Security and the MAC address table.
- Test connectivity between hosts.

---

## Topology

The topology uses one Cisco switch connected to the following PCs:

| Device | IP Address | Switch Port | Port Security Configuration |
|---|---|---|---|
| PC0 | `192.168.1.1` | Fa0/1 | Maximum 1, Sticky, Shutdown |
| PC1 | `192.168.1.2` | Fa0/2 | Maximum 1, Sticky, Shutdown |
| PC2 | `192.168.1.3` | Fa0/3 | Maximum 2, Sticky, Restrict |
| PC3 | `192.168.1.4` | Fa0/4 | Maximum 2, Sticky, Restrict |
| PC4 | `192.168.1.5` | Fa0/5 | Maximum 1, Static MAC, Protect |
| Hacker-PC | — | Not connected | Used as the unauthorized-device scenario |

> The port mapping above follows the interface labels and configuration shown in the provided Packet Tracer topology.

---

## Port Security Configuration

### 1. Fa0/1 and Fa0/2 — Shutdown Violation

Interfaces `Fa0/1` and `Fa0/2` are configured as access ports with Port Security.

Configuration characteristics:

- Port mode: Access
- Port Security: Enabled
- Maximum secure MAC addresses: `1`
- MAC learning: Sticky
- Violation mode: `shutdown`

### Why?

Only one device/MAC address is allowed on each port. If an unauthorized MAC address is detected, the port is placed into a shutdown/err-disabled state.

This provides strict protection for ports where only one authorized endpoint should be connected.

---

### 2. Fa0/3 and Fa0/4 — Restrict Violation

Interfaces `Fa0/3` and `Fa0/4` are configured as access ports with Port Security.

Configuration characteristics:

- Port mode: Access
- Port Security: Enabled
- Maximum secure MAC addresses: `2`
- MAC learning: Sticky
- Violation mode: `restrict`

### Why?

These ports allow up to two secure MAC addresses. If an unauthorized MAC address violates the configured limit, the violating traffic is restricted while the interface remains operational.

This is less disruptive than the shutdown violation mode.

---

### 3. Fa0/5 — Protect Violation

Interface `Fa0/5` is configured as an access port with Port Security.

Configuration characteristics:

- Port mode: Access
- Port Security: Enabled
- Maximum secure MAC addresses: `1`
- Secure MAC address: Manually configured
- Violation mode: `protect`

The topology specifies the secure MAC address as:

`0007.EC50.B6BC`

### Why?

The port is restricted to one specific authorized MAC address. With `protect` mode, traffic from unauthorized MAC addresses is dropped without shutting down the interface.

---

## Port Security Violation Modes

| Mode | Behaviour |
|---|---|
| `shutdown` | Port is placed into a shutdown/err-disabled state after a security violation. |
| `restrict` | Unauthorized traffic is restricted while the interface remains operational. |
| `protect` | Unauthorized traffic is dropped without shutting down the interface. |

---

## Sticky MAC Address Learning

Sticky learning is configured on Fa0/1 through Fa0/4.

Sticky learning allows the switch to dynamically learn the connected device's MAC address and associate it with the secure MAC-address configuration.

This reduces the need to manually enter every endpoint MAC address.

---

## Static Secure MAC Address

Fa0/5 uses a manually configured secure MAC address:

`0007.EC50.B6BC`

This means the port is configured to accept the specified secure MAC address while applying the configured Port Security violation policy to unauthorized devices.

---

## Verification

The topology includes connectivity verification using:

- Ping from PC4 to PC0 (`192.168.1.1`)
- `show port-security`
- `show mac-address-table`

These commands are used to verify connectivity, Port Security status, and learned MAC addresses.

---

## Expected Outcome

After successful configuration:

- Fa0/1 and Fa0/2 allow one secure MAC address and use `shutdown` violation mode.
- Fa0/3 and Fa0/4 allow two secure MAC addresses and use `restrict` violation mode.
- Fa0/5 allows one manually specified secure MAC address and uses `protect` violation mode.
- Sticky MAC addresses are learned on the specified ports.
- Port Security status and the MAC address table can be verified from the switch CLI.

---

## Key Concepts Learned

- Layer 2 switch security
- Port Security
- Secure MAC addresses
- Sticky MAC learning
- Maximum MAC address limits
- Port Security violation modes
- Access-port security
- MAC address table verification
- Unauthorized device protection

---

## Tool Used

**Cisco Packet Tracer**

## Project Files

- `README.md` — Lab documentation and configuration explanation
- `commands.txt` — Complete step-by-step Cisco IOS commands
- `.pkt` — Cisco Packet Tracer topology file
