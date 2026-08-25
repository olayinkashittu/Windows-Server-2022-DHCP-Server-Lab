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

```bash
ipconfig /all
```

### Step 2 — Verify the DHCP Configuration

Locate Ethernet 2 and verify the following:

```bash 
IPv4 Address    : 192.168.10.100
Subnet Mask     : 255.255.255.0
DHCP Enabled    : Yes
DHCP Server     : 192.168.10.10
```
### Expected Result

DC01 should automatically receive an IPv4 address from the DHCP server.

##Test DHCP Server Connectivity

### Step 3 — Ping the DHCP Server

From DC01, run:

```bash
ping 192.168.10.10
```

### Expected Result

The DHCP server should respond successfully.

Example:

```bash
Reply from 192.168.10.10: bytes=32 time<1ms TTL=128
```
The connectivity test should show:

```bash
0% packet loss
```

This confirms that DC01 can communicate with the DHCP server.

## Verify DHCP Lease

### Step 4 — Open PowerShell on DHCP-Server-2022

On DHCP-Server-2022, open PowerShell as Administrator.

Run:

```bash
Get-DhcpServerv4Lease -ScopeId 192.168.10.0
```

### Step 5 — Verify the Client Lease

The DHCP lease table should contain:

```bash
192.168.10.100
```

This confirms that the DHCP server successfully issued an IP address to DC01.

## DHCP Client Verification

The following items have been successfully verified:

• [x] DC01 connected to DHCP-LAB
• [x] DHCP client enabled
• [x] IPv4 address assigned automatically
• [x] IP address: 192.168.10.100
• [x] Subnet mask: 255.255.255.0
• [x] DHCP server: 192.168.10.10
• [x] DHCP lease confirmed
• [x] DHCP server connectivity confirmed
• [x] 0% packet loss

## Verification Summary

The DHCP client on DC01 successfully obtained the IP address 192.168.10.100 from DHCP-Server-2022.

The DHCP lease was confirmed on the DHCP server, and network connectivity was verified with a successful ping test.

The DHCP deployment is operating correctly.
