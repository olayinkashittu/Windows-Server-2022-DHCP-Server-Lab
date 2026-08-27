# 🖥️ Windows Server 2022 DHCP Server Lab

## 📋 Overview

This project demonstrates the deployment, configuration, testing, and troubleshooting of a **DHCP Server on Windows Server 2022** using a virtualized lab environment.

The lab demonstrates how a Windows Server DHCP service automatically assigns IP addresses to client machines and maintains DHCP leases.

## 🎯 Project Objectives

- Deploy Windows Server 2022 as a DHCP Server
- Configure a static IP address for the DHCP Server
- Install the DHCP Server role
- Create and configure a DHCP IPv4 scope
- Configure DHCP scope options
- Connect a Windows Server client to the DHCP network
- Verify automatic IP address assignment
- Verify DHCP leases
- Test network connectivity
- Troubleshoot DHCP connectivity issues
- Document the complete deployment process

---

## 🏗️ Lab Architecture

```bash
                         VirtualBox
                            │
                      Internal Network
                         DHCP-LAB
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
     DHCP-Server-2022                   DC01
       Windows Server 2022          Windows Server 2022
       DHCP Server                  DHCP Client
       192.168.10.10               192.168.10.100
              │                           │
              └────────── DHCP ───────────┘

```

## 🖥️ Lab Environment

| Component | Configuration |
|---|---|
| **Virtualization Platform** | `VirtualBox` |
| **Virtual Network** | `DHCP-LAB` |
| **DHCP Server** | `DHCP-Server-2022` |
| **DHCP Server IP** | `192.168.10.10` |
| **DHCP Client** | `DC01` |
| **DHCP Client IP** | `192.168.10.100` |
| **Network** | `192.168.10.0/24` |
| **Subnet Mask** | `255.255.255.0` |


## 📊 Lab Status

| Component | Status |
|---|---|
| **DHCP Server** | `192.168.10.10` ✅ |
| **DC01** | `192.168.10.100` ✅ |
| **Network** | `192.168.10.0/24` ✅ |
| **Virtual Network** | `DHCP-LAB` ✅ |
| **DHCP Lease** | Confirmed ✅ |
| **Connectivity** | `0% packet loss` ✅ |
| **Documentation** | Complete ✅ |

### 🎯 Lab Objectives
Configure a static IP address on Windows Server 2022
Install the DHCP Server role
Configure a DHCP scope
Configure DHCP options
Assign IP addresses automatically to clients
Verify DHCP leases and client connectivity
Troubleshoot common DHCP issues
Document the complete deployment process

## 🖥️ Lab Environment

| Component | Configuration |
|---|---|
| **Virtualization Platform** | `VirtualBox` |
| **Virtual Network** | `DHCP-LAB` |
| **DHCP Server** | `DHCP-Server-2022` |
| **DHCP Server IP** | `192.168.10.10` |
| **DHCP Client** | `DC01` |
| **DHCP Client IP** | `192.168.10.100` |
| **Network** | `192.168.10.0/24` |
| **Subnet Mask** | `255.255.255.0` |


### 🌐 Network Architecture

```bash
                    WINDOWS SERVER 2022
                    DHCP-Server-2022
                    192.168.10.10
                           │
                           │ DHCP
                           │
                    ┌──────┴──────┐
                    │             │
               DHCP SCOPE     DHCP OPTIONS
              192.168.10.x    Gateway / DNS
                    │
              ┌─────┴─────┐
              │           │
           CLIENT 1    CLIENT 2
             DHCP        DHCP
              │           │
        Dynamic IP    Dynamic IP

```

### Project Structure

```bash

Windows-Server-2022-DHCP-Server-Lab/
│
├── README.md
│
├── images/
│   ├── server-manager.png
│   ├── dhcp-server-installation.png
│   ├── dhcp-scope.png
│   ├── dhcp-options.png
│   ├── dhcp-lease.png
│   └── client-ip-configuration.png
│
├── docs/
│   ├── 01-server-setup.md
│   ├── 02-static-ip-configuration.md
│   ├── 03-dhcp-server-installation.md
│   ├── 04-dhcp-scope-configuration.md
│   ├── 05-dhcp-client-testing.md
│   └── 06-troubleshooting.md
│
└── LICENSE

```

### 🔧 Project Configuration

1. Static IP Configuration
The DHCP server is configured with a static IP address:

IP Address:     192.168.10.10
Subnet Mask:    255.255.255.0
Network:        192.168.10.0/24
A static IP ensures that the DHCP server remains consistently reachable on the network.

2. DHCP Server Installation
   
The DHCP Server role is installed using:

```bash

Server Manager
    ↓
Manage
    ↓
Add Roles and Features
    ↓
Role-based or feature-based installation
    ↓
DHCP Server

```

3. DHCP Scope Configuration
A DHCP scope will define the range of IP addresses that can be dynamically assigned to client devices.

Example:

Network:       192.168.10.0/24
DHCP Range:    192.168.10.100 - 192.168.10.200
Subnet Mask:   255.255.255.0
The final scope values will be documented after configuration in the lab.

4. DHCP Options
The lab will configure appropriate DHCP options, such as:

Default Gateway
DNS Server
DNS Domain Name
These options allow DHCP clients to receive the network configuration they need automatically.

### 🧪 Client Testing
After configuring the DHCP server, a client machine will be configured to obtain an IP address automatically.

The following command can be used to verify the assigned configuration:

```bash
ipconfig /all
```

To test connectivity:

```bash
ping 192.168.10.10
```
The client should receive an IP address from the configured DHCP scope.

### 🔍 Verification
The following items will be verified:

DHCP Server role installation
DHCP service status
DHCP scope configuration
Available IP address range
Active DHCP leases
Client IP assignment
Default gateway
DNS configuration
Network connectivity

### 🛠️ Troubleshooting

Common DHCP troubleshooting checks include:

```bash
ipconfig /release
ipconfig /renew
ipconfig /all
```

Additional checks include:

Confirming the DHCP service is running
Checking the DHCP scope
Checking available addresses
Verifying DHCP client configuration
Checking network connectivity
Reviewing DHCP leases

### 📸 Screenshots
Screenshots documenting the lab will be added as the configuration progresses.

Planned screenshots:

DHCP Server installation
DHCP Server Manager
DHCP scope configuration
DHCP options
DHCP lease
Client IP configuration
Connectivity verification

### 📚 Documentation
Detailed documentation will be organized in the docs/ directory:

```bash
docs/
├── 01-server-setup.md
├── 02-static-ip-configuration.md
├── 03-dhcp-server-installation.md
├── 04-dhcp-scope-configuration.md
├── 05-dhcp-client-testing.md
└── 06-troubleshooting.md
```

### 💡 Key Skills Demonstrated

Windows Server 2022 Administration
DHCP Server Deployment
IPv4 Networking
IP Address Management
DHCP Scope Management
Network Troubleshooting
Client Network Configuration
PowerShell
Technical Documentation

### 🚀 Project Highlights

Deployed a Windows Server 2022 DHCP server
Configured a static server IP
Installed and configured the DHCP Server role
Created and managed DHCP address scopes
Configured DHCP network options
Tested automatic client IP assignment
Verified DHCP leases and network connectivity
Documented the complete hands-on lab

### 👨‍💻 Author
Olayinka Shittu

This project is part of my hands on IT infrastructure, Windows Server, networking, and troubleshooting portfolio.

### 📄 License
This project is licensed under the MIT License.
