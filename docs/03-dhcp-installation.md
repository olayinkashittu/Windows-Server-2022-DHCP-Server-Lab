# DHCP Server Installation

## Overview

This section documents the installation of the DHCP Server role on the Windows Server 2022 virtual machine.

The DHCP Server role allows the Windows Server to automatically provide IP address configuration to client devices on the network.

## Server Information

| Setting | Configuration |
|---|---|
| Server Name | `DHCP-Server-2022` |
| Operating System | Windows Server 2022 |
| Server Role | DHCP Server |
| Server IP Address | `192.168.10.10` |
| Network | `192.168.10.0/24` |

## Installation Steps

### Step 1 — Open Server Manager

1. Log in to the `DHCP-Server-2022` server.
2. Open **Server Manager**.
3. Click **Manage** in the top-right corner.
4. Select **Add Roles and Features**.

### Step 2 — Before You Begin

The **Add Roles and Features Wizard** will open.

1. Review the information on the **Before You Begin** page.
2. Click **Next**.

### Step 3 — Select Installation Type

On the **Installation Type** page:

1. Select:

```bash
Role-based or feature-based installation
```
2. Click **Next**.
   
### Step 4 — Select Destination Server

On the Server Selection page:

1. Select:

```bash
DHCP-Server-2022
```

2. Click **Next**.
   
### Step 5 — Select DHCP Server Role

On the Server Roles page:

1. Locate DHCP Server.

2. Select the checkbox:

```bash
DHCP Server
```

3. When the Add Roles and Features window appears, click Add Features.
4. Confirm that DHCP Server is selected.
5. Click **Next**.

### Step 6 — Select Features

On the Features page:

1. Leave the default settings unchanged.
2. Click **Next**.

### Step 7 — DHCP Server Information

On the DHCP Server information page:

1. Review the information.
2. Leave the default settings unchanged.
3. Click **Next**.
   
### Step 8 — Confirm Installation

On the Confirmation page:

1. Verify that DHCP Server is listed.
2. Verify that the destination server is:

```bash
DHCP-Server-2022
```
3. Click Install.
   
### Installation Progress

Wait while Windows Server installs the DHCP Server role.

The installation should eventually show that the DHCP Server role was successfully installed.

### Verification

After installation:

1. Return to Server Manager.
2. Verify that the DHCP Server role is installed.
3. Open the DHCP management console if required.
4. Confirm that the DHCP Server service is available.

PowerShell can also be used to verify the DHCP Server service:

```bash
Get-Service DHCPServer
```

The service should be available on the server.

### Screenshot

Add the DHCP Server installation screenshot here:

### Result

The DHCP Server role has been successfully installed on DHCP-Server-2022.

The server is now ready for DHCP scope configuration.
