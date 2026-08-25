DHCP Client Testing
Overview
This section documents the verification and testing of the DHCP client configuration on the Windows Server 2022 client machine.

The client successfully received an IPv4 address from the Windows Server 2022 DHCP server.

Lab Environment
Component	Configuration
DHCP Server	DHCP-Server-2022
DHCP Server IP	192.168.10.10
DHCP Network	192.168.10.0/24
DHCP Client	DC01
DHCP Client IP	192.168.10.100
Subnet Mask	255.255.255.0
Virtual Network	DHCP-LAB
1. Verify DHCP Client Configuration
On DC01, open Command Prompt and run:

ipconfig /all
Verify the following values:

IPv4 Address    : 192.168.10.100
Subnet Mask     : 255.255.255.0
DHCP Enabled    : Yes
DHCP Server     : 192.168.10.10
Expected Result
DC01 successfully receives an IP address from the DHCP server.

Client IP Configuration

2. Test Connectivity to DHCP Server
From DC01, run:

ping 192.168.10.10
Expected Result
The DHCP server should respond successfully.

Example:

Reply from 192.168.10.10: bytes=32 time<1ms TTL=128
The test completed with:

0% packet loss
This confirms network connectivity between DC01 and DHCP-Server-2022.

3. Verify DHCP Lease
On DHCP-Server-2022, open PowerShell as Administrator and run:

Get-DhcpServerv4Lease -ScopeId 192.168.10.0
The DHCP lease table should contain the client address:

192.168.10.100
Expected Result
The DHCP server successfully issued and recorded a lease for DC01.

DHCP Lease

4. DHCP Client Verification Checklist
[x] DC01 connected to DHCP-LAB
[x] DHCP client enabled
[x] IPv4 address assigned automatically
[x] IP address received: 192.168.10.100
[x] Subnet mask: 255.255.255.0
[x] DHCP server: 192.168.10.10
[x] DHCP lease visible on DHCP server
[x] Connectivity test successful
[x] Packet loss: 0%
Conclusion
The DHCP client configuration was successfully tested and verified.

DC01 automatically received the IP address 192.168.10.100 from DHCP-Server-2022 (192.168.10.10) over the DHCP-LAB virtual network.

Successful ping connectivity and DHCP lease verification confirm that the DHCP deployment is operational.


