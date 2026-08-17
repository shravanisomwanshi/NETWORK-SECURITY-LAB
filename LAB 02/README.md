# Basic Router Configuration Using Cisco Packet Tracer

## 📌 Lab Overview

This lab demonstrates the **basic configuration of a Cisco 2911 router using Cisco Packet Tracer**.

The configuration covers essential router security and management settings such as hostname, MOTD banner, console access, VTY access, password configuration, domain configuration, local user creation, password encryption, login blocking, clock configuration, and configuration verification.

---

## 🎯 Objectives

The objectives of this lab are:

* Configure a Cisco 2911 router using CLI.
* Configure the router hostname.
* Configure a MOTD banner.
* Secure console access using a password.
* Configure VTY lines for remote access.
* Configure an enable password.
* Configure a local username and password.
* Disable DNS lookup.
* Configure a domain name.
* Enable password encryption.
* Configure login blocking for failed authentication attempts.
* Configure the router clock.
* Verify running and startup configurations.
* Save the router configuration.

---

## 🖥️ Topology

### Devices Used

| Device | Model      | Name     |
| ------ | ---------- | -------- |
| Router | Cisco 2911 | R1-gtech |
| PC     | PC-PT      | PC1      |

### Topology Connection

```text
PC1
 |
 |
Cisco 2911 Router
R1-gtech
```

The topology contains one PC connected directly to one Cisco 2911 router.

---

## ⚙️ Router Configuration

### 1. Enter Privileged EXEC Mode

```text
enable
```

### 2. Enter Global Configuration Mode

```text
configure terminal
```

### 3. Configure Router Hostname

```text
hostname R1-gtech
```

The hostname identifies the router in the CLI.

---

### 4. Configure MOTD Banner

```text
banner motd #THIS IS TEST ROUTER#
```

The MOTD banner displays a message when a user accesses the router.

---

### 5. Configure Enable Password

```text
enable password cisco
```

This configures a password for privileged EXEC mode.

---

### 6. Configure Console Line

```text
line console 0
password cisco
login
exec-timeout 4 0
logging synchronous
exit
```

This configuration secures console access and automatically terminates an inactive console session after 4 minutes.

---

### 7. Configure VTY Lines

```text
line vty 0 15
password cisco
login
exec-timeout 2 30
logging synchronous
exit
```

VTY lines are used for remote terminal access to the router.

---

### 8. Disable DNS Lookup

```text
no ip domain-lookup
```

This prevents the router from attempting DNS resolution when an incorrect command is entered.

---

### 9. Configure Domain Name

```text
ip domain-name cisco.com
```

The domain name is configured as:

```text
cisco.com
```

---

### 10. Create Local User

```text
username password cisco
```

This creates a local user configuration according to the lab instructions.

---

### 11. Verify Running Configuration

```text
do show run
```

This displays the currently active configuration.

---

### 12. Enable Password Encryption

```text
service password-encryption
```

This encrypts plaintext passwords stored in the configuration.

---

### 13. Verify Configuration Again

```text
do show run
```

This allows the password-encryption configuration to be verified.

---

### 14. Exit Configuration Mode

```text
exit
```

---

### 15. Configure Router Clock

```text
clock set 17:30:45 mar 01 2023
```

This configures the router's system clock.

---

### 16. Enter Global Configuration Mode

```text
configure terminal
```

---

### 17. Configure Login Blocking

```text
login block-for 180 attempts 3 within 50
```

This provides protection against repeated failed login attempts.

Meaning:

* **180 seconds** → Login is blocked for 180 seconds.
* **3 attempts** → Maximum 3 failed attempts.
* **within 50 seconds** → The 3 failed attempts must occur within 50 seconds.

---

### 18. Verify Running Configuration

```text
do show run
```

---

### 19. Verify Startup Configuration

```text
do show start
```

This displays the configuration saved in NVRAM.

---

### 20. Save Configuration

```text
do wr
```

This saves the current configuration so it can be restored after a router restart.

---

## 🔍 Important Verification Commands

### Check Running Configuration

```text
show running-config
```

### Check Startup Configuration

```text
show startup-config
```

### Check Interfaces

```text
show ip interface brief
```

### Check Router Clock

```text
show clock
```

### Check Login Blocking Configuration

```text
show login
```

---

## 🧠 Key Concepts

### Enable Password

Used to protect access to privileged EXEC mode.

### Console Line

Provides local CLI access through the router's console connection.

### VTY Lines

Provide remote terminal access to the router.

### MOTD Banner

Displays an informational or security message when users access the device.

### DNS Lookup

The `no ip domain-lookup` command prevents unwanted DNS lookup attempts.

### Password Encryption

The `service password-encryption` command encrypts passwords stored in the configuration.

### Login Blocking

The `login block-for` command helps protect the router against repeated failed login attempts.

### Running Configuration

The currently active configuration stored in RAM.

### Startup Configuration

The saved configuration stored in NVRAM and loaded when the router boots.

---

## ✅ Result

The Cisco 2911 router was configured successfully with basic management and security settings including:

* Hostname
* MOTD banner
* Enable password
* Console password
* VTY password
* Console and VTY timeout
* DNS lookup disabled
* Domain name
* Local user configuration
* Password encryption
* Login blocking
* System clock
* Configuration verification
* Configuration saving

---

## 🛠️ Tool Used

**Cisco Packet Tracer**

## 📚 Lab Type

**Basic Cisco Router Configuration**
