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
