# Windows-Server-2022-DHCP-Server-Lab
Hands on Windows Server 2022 DHCP Server lab covering configuration, scope management, client IP assignment, testing, and troubleshooting.
Windows Server 2022 DHCP Server Lab

### 📌 Project Overview
This project demonstrates the deployment and configuration of a DHCP Server on Windows Server 2022 in a hands-on virtual lab environment.

The lab covers the installation of the DHCP Server role, static IP configuration, DHCP scope creation, DHCP options, automatic client IP assignment, verification, and troubleshooting.

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

### 🖥️ Lab Environment
Component	Configuration
Operating System	Windows Server 2022
Server Name	DHCP-Server-2022
Server Role	DHCP Server
Server IP	192.168.10.10
Subnet Mask	255.255.255.0
Network	192.168.10.0/24
DHCP Service	Windows Server DHCP

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
