# DHCP Troubleshooting

## Overview

This section documents the troubleshooting process performed during the Windows Server 2022 DHCP deployment.

The issue occurred when DC01 failed to obtain an IPv4 address from the DHCP server and automatically assigned itself an APIPA address.

## Problem Description

DC01 initially received the following IPv4 address on **Ethernet 2**:

```bash
IPv4 Address    : 169.254.17.130
Subnet Mask     : 255.255.0.0
DHCP Enabled    : Yes
DHCP Server     : Not available
```
The 169.254.x.x address indicated that DC01 was unable to obtain an IPv4 address from the DHCP server.

## Troubleshooting Steps

### Step 1 — Verify Network Adapter Status

On DC01, the following command was used:

```bash
Get-NetAdapter
```

Result:

Ethernet 2 was reported as:

```bash
Status: Up
```

This confirmed that the network adapter was connected.

### Step 2 — Verify DHCP Server IP Address

On DHCP-Server-2022, the server IP address was verified.

```bash
IP Address: 192.168.10.10
```

The DHCP server was correctly configured with a static IP address.

### Step 3 — Verify DHCP Scope

The DHCP scope was checked using:

```bash
Get-DhcpServerv4Scope
```

The configured DHCP network was:

```bash
192.168.10.0/24
```

The DHCP scope was successfully configured.

### Step 4 — Verify DHCP Server Binding

The DHCP server binding was checked using:

```bash
Get-DhcpServerv4Binding
```
The result confirmed:

```bash
InterfaceAlias    IPAddress       BindingState
--------------    ---------       ------------
Ethernet          192.168.10.10   True
```

This confirmed that DHCP was correctly bound to the server's network interface.

### Step 5 — Verify VirtualBox Network

The VirtualBox network configuration was checked on both virtual machines.

DHCP-Server-2022

```bash
Attached to: Internal Network
Network Name: DHCP-LAB
Cable Connected: Yes
```
DC01

```bash
Attached to: Internal Network
Network Name: DHCP-LAB
Cable Connected: Yes
```
Both virtual machines were connected to the same DHCP-LAB Internal Network.

### Step 6 — Verify Network Adapter Type

Both virtual machines were configured with:

```bash
Intel PRO/1000 MT Desktop (82540EM)
```

This confirmed that the network adapter type was consistent between the two virtual machines.

### Step 7 — Verify Windows Firewall

Windows Defender Firewall with Advanced Security was checked on the DHCP server.

The following inbound rule was found:

```bash
File and Printer Sharing (Echo Request - ICMPv4-In)
```
The rule was enabled to allow ICMP connectivity testing.

### Step 8 — Renew the DHCP Address

On DC01, the DHCP address was renewed using:

```bash
ipconfig /release
```

Then:

```bash
ipconfig /renew
```
After the network configuration was corrected, DC01 successfully obtained an IPv4 address from the DHCP server.

### Step 9 — Verify DHCP Client Address

The final configuration on DC01 was:

```bash
IPv4 Address    : 192.168.10.100
Subnet Mask     : 255.255.255.0
DHCP Enabled    : Yes
DHCP Server     : 192.168.10.10
```

This confirmed that DC01 successfully received its IP address from the DHCP server.

### Step 10 — Test Connectivity

Connectivity between DC01 and the DHCP server was tested using:

```bash
ping 192.168.10.10
```

The test completed successfully with:

```bash
0% packet loss
```

This confirmed successful network communication between the DHCP client and DHCP server.

### Step 11 — Verify DHCP Lease

The DHCP lease was verified on DHCP-Server-2022 using:

```bash
Get-DhcpServerv4Lease -ScopeId 192.168.10.0
```

The DHCP lease table contained:

```bash
192.168.10.100
```
This confirmed that the DHCP server successfully issued and recorded the lease for DC01.

## 🛠️ Troubleshooting Summary

| # | Problem | Solution |
|---|---|---|
| 1️⃣ | **DC01 received `169.254.x.x`** | ✅ Verified DHCP and network configuration |
| 2️⃣ | **DHCP renewal failed** | ✅ Verified VirtualBox network connectivity |
| 3️⃣ | **DC01 could not initially reach DHCP server** | ✅ Verified `DHCP-LAB` Internal Network |
| 4️⃣ | **DHCP scope verification** | ✅ Confirmed `192.168.10.0/24` scope |
| 5️⃣ | **DHCP binding** | ✅ Confirmed binding state was `True` |
| 6️⃣ | **Firewall verification** | ✅ Enabled ICMPv4 inbound rule for testing |
| 7️⃣ | **DHCP address assignment** | ✅ DC01 received `192.168.10.100` |
| 8️⃣ | **Connectivity test** | ✅ Confirmed `0% packet loss` |
| 9️⃣ | **DHCP lease verification** | ✅ Lease `192.168.10.100` confirmed |

---

## 🎯 Final Result

The DHCP connectivity issue was successfully resolved.

DC01 initially received an APIPA address:

```bash
169.254.17.130
```

After troubleshooting the network and DHCP configuration, DC01 successfully received:

```bash
IPv4 Address    : 192.168.10.100
Subnet Mask     : 255.255.255.0
DHCP Enabled    : Yes
DHCP Server     : 192.168.10.10
```

## ✅ Final Verification


```bash
DHCP Server     → 192.168.10.10
DHCP Client     → 192.168.10.100
Network         → 192.168.10.0/24
Virtual Network → DHCP-LAB
Connectivity    → 0% packet loss
DHCP Lease      → Confirmed
Status          → Operational

```

## 🚀 Deployment Status
DHCP deployment successfully completed and verified. ✅

- [x] DHCP Server configured
- [x] DHCP Scope configured
- [x] DHCP Client configured
- [x] DHCP Lease confirmed
- [x] Network connectivity verified
- [x] Troubleshooting completed
- [x] 0% packet loss confirmed

