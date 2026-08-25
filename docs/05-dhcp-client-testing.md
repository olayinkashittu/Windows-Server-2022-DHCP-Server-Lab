# DHCP Client Testing

## Overview

This section documents the verification and testing of the DHCP client configuration on Windows Server 2022.

The DHCP client is configured to automatically obtain an IPv4 address from the DHCP server.

## Network Information

| Setting | Configuration |
|---|---|
| DHCP Server | `DHCP-Server-2022` |
| Server IP Address | `192.168.10.10` |
| Network | `192.168.10.0/24` |
| Subnet Mask | `255.255.255.0` |
| DHCP Client | `DC01` |
| Assigned IP Address | `192.168.10.100` |
| Virtual Network | `DHCP-LAB` |

## Verify DHCP Client Configuration

### Step 1 — Open Command Prompt

On **DC01**, open **Command Prompt** as Administrator.

Run:

```cmd
ipconfig /all
