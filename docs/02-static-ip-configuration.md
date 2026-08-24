# Static IP Configuration

## Overview

This section documents the configuration of a static IPv4 address on the Windows Server 2022 DHCP server.

A static IP address ensures that the DHCP server remains consistently reachable on the network.

## Network Configuration

| Setting | Configuration |
|---|---|
| Server Name | `DHCP-Server-2022` |
| IP Address | `192.168.10.10` |
| Subnet Mask | `255.255.255.0` |
| Network | `192.168.10.0/24` |

## Configuration Steps

1. Open **Network Connections** on the Windows Server 2022 machine.
2. Locate the active network adapter.
3. Right-click the adapter and select **Properties**.
4. Select **Internet Protocol Version 4 (TCP/IPv4)**.
5. Click **Properties**.
6. Select **Use the following IP address**.
7. Enter the following configuration:

```bash
IP Address:    192.168.10.10
Subnet Mask:   255.255.255.0
```

## Verification

Open PowerShell or Command Prompt and run:

```bash
ipconfig
```

For detailed network information, run:

```bash
ipconfig /all
```

Verify that the server displays:

```bash
IPv4 Address:    192.168.10.10
Subnet Mask:     255.255.255.0
```

## Screenshot

Add the static IP configuration screenshot here:

## Result

The Windows Server 2022 DHCP server has been configured with a static IPv4 address of 192.168.10.10 and is ready for DHCP Server role installation.
