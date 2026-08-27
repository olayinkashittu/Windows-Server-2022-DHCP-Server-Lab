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
├── 📁 docs/
│   ├── 01-server-setup.md
│   ├── 02-static-ip-configuration.md
│   ├── 03-dhcp-server-installation.md
│   ├── 04-dhcp-scope-configuration.md
│   ├── 05-dhcp-client-testing.md
│   └── 06-troubleshooting.md
│
├── 📁 images/
│   ├── server-manager.png
│   ├── dhcp-server-installation.png
│   ├── dhcp-scope.png
│   ├── dhcp-options.png
│   ├── dhcp-lease.png
│   └── client-ip-configuration.png
│
├── 📄 LICENSE
│
└── 📄 README.md

```

## 🚀 Deployment Process

### 01 — Server Setup

Initial Windows Server 2022 virtual machine setup and configuration.


### 02 — Static IP Configuration

Configured the DHCP Server with the following static IP address:

```bash
IP Address    : 192.168.10.10
Subnet Mask   : 255.255.255.0
```

### 03 — DHCP Server Installation

Installed the DHCP Server role using Windows Server Manager.

### 04 — DHCP Scope Configuration

Created and configured the IPv4 DHCP scope:

```bash
Network       : 192.168.10.0/24
Subnet Mask   : 255.255.255.0
```

### 05 — DHCP Client Testing

Configured DC01 as a DHCP client and verified automatic IP address assignment.

DC01 successfully received:

```bash
IPv4 Address  : 192.168.10.100
DHCP Server   : 192.168.10.10
```
### 06 — Troubleshooting

Documented DHCP troubleshooting procedures, including resolving an APIPA address and verifying network connectivity.


### 🔍 Verification
DHCP Client Configuration
DC01 successfully received an IP address automatically:

```bash
IPv4 Address    : 192.168.10.100
Subnet Mask     : 255.255.255.0
DHCP Enabled    : Yes
DHCP Server     : 192.168.10.10
```

### DHCP Lease Verification

The DHCP server successfully recorded the client lease:

```bash
192.168.10.100
```
### Network Connectivity

Connectivity between DC01 and the DHCP server was successfully verified:

```bash
ping 192.168.10.10
```

Result:

```bash
0% packet loss
```

### 🛠️ Troubleshooting Highlights

During testing, DC01 initially received an APIPA address:

```bash
169.254.17.130
```
The following areas were verified:

- [x] VirtualBox Internal Network
- [x] DHCP-LAB network configuration
- [x] Network adapter status
- [x] DHCP server IP configuration
- [x] DHCP scope
- [x] DHCP server binding
- [x] DHCP service
- [x] Windows Firewall
- [x] DHCP client configuration
      
After troubleshooting, DC01 successfully received:

```bash
192.168.10.100
```

The final connectivity test achieved:

```bash
0% packet loss
```

### 📸 Screenshots
Client IP Configuration

DHCP Server Installation
DHCP Scope
DHCP Options
DHCP Lease
Screenshots documenting the lab will be added as the configuration progresses.
Planned screenshots:
DHCP Server installation
DHCP Server Manager
DHCP scope configuration
DHCP options
DHCP lease
Client IP configuration
Connectivity verification

## 🛠️ Skills Demonstrated

**Windows Server 2022** • **DHCP** • **TCP/IP** • **IPv4** • **Network Configuration** • **VirtualBox** • **DHCP Scopes** • **DHCP Leases** • **IP Address Management** • **Network Troubleshooting** • **PowerShell** • **Command Prompt** • **Technical Documentation**

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
