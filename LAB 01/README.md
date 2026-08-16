# Basic Switch Configuration Using Cisco Packet Tracer

## 📌 Lab Overview

This lab demonstrates the **basic configuration of a Cisco 2960-24TT switch using Cisco Packet Tracer**.

The configuration includes hostname setup, console and VTY password configuration, login security, domain configuration, local user creation, password encryption, VLAN 1 management IP configuration, default gateway configuration, clock configuration, and saving the configuration.

---

## 🎯 Objectives

The main objectives of this lab are:

* Configure a Cisco switch using CLI.
* Set the hostname of the switch.
* Configure console access.
* Configure VTY remote access.
* Configure enable password.
* Configure a login banner.
* Configure a domain name.
* Create a local username and password.
* Enable password encryption.
* Configure the management IP address.
* Configure the default gateway.
* Verify the running and startup configurations.
* Save the switch configuration.

---

## 🖥️ Topology

### Devices Used

| Device | Model           | Name     |
| ------ | --------------- | -------- |
| Switch | Cisco 2960-24TT | S1-gtech |
| PC     | PC-PT           | PC1      |

### Network Configuration

| Parameter                   | Value          |
| --------------------------- | -------------- |
| Switch Management Interface | VLAN 1         |
| IP Address                  | 192.168.10.254 |
| Subnet Mask                 | 255.255.255.0  |
| Default Gateway             | 192.168.10.1   |
| Domain Name                 | cisco.com      |
| Username                    | cisco          |
| Password                    | cisco          |

---

## ⚙️ Configuration Performed

### 1. Enter Privileged EXEC Mode

```text
enable
```

### 2. Enter Global Configuration Mode

```text
configure terminal
```

### 3. Configure Hostname

```text
hostname S1-gtech
```

### 4. Configure Login Banner

```text
banner motd #his test switch#
```

### 5. Configure Enable Password

```text
enable password cisco
```

### 6. Configure Console Line

```text
line console 0
password cisco
exec-timeout 3 0
logging synchronous
exit
```

### 7. Configure VTY Lines

```text
line vty 0 15
password cisco
login
exec-timeout 3 0
logging synchronous
exit
```

### 8. Disable DNS Lookup

```text
no ip domain lookup
```

This prevents the switch from trying to resolve mistyped commands as domain names.

### 9. Configure Domain Name

```text
ip domain name cisco.com
```

### 10. Create Local User

```text
username cisco password cisco
```

### 11. Enable Password Encryption

```text
service password-encryption
```

### 12. Configure Management IP

The management IP is configured on **VLAN 1**:

```text
configure terminal
interface vlan 1
no shutdown
ip address 192.168.10.254 255.255.255.0
exit
```

### 13. Configure Default Gateway

```text
ip default-gateway 192.168.10.1
```

### 14. Configure Clock

```text
clock set 13:21:30 june 20 2023
```

### 15. Verify Configuration

```text
do show run
do show start
```

### 16. Save Configuration

```text
do write
```

---

## 🔍 Verification

The following commands can be used to verify the configuration:

```text
show running-config
show startup-config
```

The management interface can also be checked using:

```text
show ip interface brief
```

The VLAN 1 interface should show the configured IP address:

```text
192.168.10.254
```

---

## 🧠 Important Concepts

### VLAN 1

VLAN 1 is used here as the **management VLAN** for the switch.

### Default Gateway

```text
192.168.10.1
```

The default gateway is used when the switch needs to communicate with devices outside its local network.

### Running Configuration

The running configuration is the configuration currently active in RAM.

### Startup Configuration

The startup configuration is stored in NVRAM and is loaded when the switch starts.

### `do write`

This saves the current configuration so that it is retained after a reboot.

---

## ✅ Result

The Cisco 2960-24TT switch was successfully configured with:

* Hostname
* MOTD banner
* Enable password
* Console password
* VTY password
* Domain name
* Local username
* Password encryption
* VLAN 1 management IP
* Default gateway
* Clock
* Saved configuration

**Management IP:** `192.168.10.254/24`

**Default Gateway:** `192.168.10.1`

---

## 🛠️ Tool Used

**Cisco Packet Tracer**

## 📚 Lab Type

**Basic Cisco Switch Configuration**
