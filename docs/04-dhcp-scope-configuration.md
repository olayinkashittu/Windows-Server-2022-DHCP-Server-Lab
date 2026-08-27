# DHCP Scope Configuration

## Overview

This section documents the configuration of a DHCP scope on Windows Server 2022.

A DHCP scope defines the range of IPv4 addresses that the DHCP server can automatically assign to client devices on the network.

## Network Information

| Setting | Configuration |
|---|---|
| DHCP Server | `DHCP-Server-2022` |
| Server IP Address | `192.168.10.10` |
| Network | `192.168.10.0/24` |
| Subnet Mask | `255.255.255.0` |
| DHCP Scope | `192.168.10.0/24` |
| DHCP Client | `DC01` |
| Virtual Network | `DHCP-LAB` |

## Create a New DHCP Scope

### Step 1 — Open the DHCP Management Console

On **DHCP-Server-2022**:

1. Open **Server Manager**.
2. Select **Tools**.
3. Click **DHCP**.

The DHCP Management Console will open.

### Step 2 — Expand IPv4

In the DHCP Management Console:

1. Expand the DHCP server.
2. Expand **IPv4**.
3. Right-click **IPv4**.
4. Select **New Scope**.

The **New Scope Wizard** will open.

---

### Step 3 — Configure the Scope Name

Enter:

```bash
DHCP-LAB-Scope
```

Add the following description:

```bash
IPv4 DHCP Scope for the DHCP-LAB network
```

Click **Next** to continue.

### Step 4 — Configure the IP Address Range

Configure the DHCP address range according to the lab network.

| Setting | Configuration |
|---|---|
| **Start IP Address** | `192.168.10.100` |
| **End IP Address** | `192.168.10.200` |
| **Subnet Mask** | `255.255.255.0` |
| **Prefix Length** | `/24` |

Click **Next** to continue.

### Step 5 — Configure Exclusions and Delay

No exclusions are required for this lab.

Click **Next** to continue.

### Step 6 — Configure Lease Duration

Use the default DHCP lease duration.

Click **Next** to continue.

### Step 7 — Configure DHCP Options

Select:

```bash
Yes, I want to configure these options now
```

Click **Next** to continue.

### Step 8 — Configure Default Gateway

If a gateway is required for the lab network, enter:

```bash
192.168.10.1
```

If the isolated DHCP-LAB network does not use a gateway, leave this option blank.

Click **Next** to continue.

### Step 9 — Configure DNS

Configure the DNS settings according to the lab environment.

For an Active Directory environment, use the domain controller/DNS server IP address as the preferred DNS server.

Example:

```bash
DNS Server: 192.168.10.10
```

Click **Next** to continue.

### Step 10 — Configure WINS

No WINS configuration is required for this lab.

Click **Next** to continue.

### Step 11 — Activate the DHCP Scope

Select:

```bash
Yes, I want to activate this scope now
```

Click **Next** to continue.

Click Finish to complete the DHCP Scope Wizard.

### Verify DHCP Scope

After completing the wizard:

1. Open DHCP Management Console.
2. Expand IPv4.
3. Expand the newly created scope.
4. Verify the scope configuration.
   
The scope should contain the configured address range:

```bash
192.168.10.100 - 192.168.10.200
```

### Expected Result

The DHCP scope is successfully created and activated.

#Verify DHCP Scope Using PowerShell

Open PowerShell as Administrator and run:

```bash
Get-DhcpServerv4Scope
```

Verify that the scope for the network appears:

```bash
192.168.10.0
```

You can also verify the scope details using:


```bash
Get-DhcpServerv4Scope -ScopeId 192.168.10.0
```

### 📊 DHCP Scope Configuration Summary

| Setting | Value |
|---|---|
| **Scope Name** | `DHCP-LAB-Scope` |
| **Network** | `192.168.10.0/24` |
| **Start IP** | `192.168.10.100` |
| **End IP** | `192.168.10.200` |
| **Subnet Mask** | `255.255.255.0` |
| **DHCP Server** | `192.168.10.10` |
| **Status** | **Active** ✅ |

### ✅ Verification Checklist

- [x] DHCP Management Console opened
- [x] IPv4 scope created
- [x] DHCP address range configured
- [x] Subnet mask configured
- [x] DHCP scope activated
- [x] DHCP scope verified
- [x] Scope network confirmed as `192.168.10.0/24`


### Conclusion

The DHCP IPv4 scope was successfully created and activated on DHCP-Server-2022.
The scope provides IP addresses within the 192.168.10.0/24 network and allows DHCP clients on the DHCP-LAB network to obtain IP addresses automatically.
