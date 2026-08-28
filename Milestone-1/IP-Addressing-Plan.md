# IP Addressing Plan

## 4.1 VLSM Allocation

| Network Purpose | VLAN | Network Address | CIDR | Subnet Mask | Usable Host Range | Gateway |
|---|---:|---|---|---|---|---|
| Management & Remote Administration | 10 | 172.30.94.0 | /26 | 255.255.255.192 | 172.30.94.1 – 172.30.94.62 | 172.30.94.1 |
| Customer Records | 20 | 172.30.94.64 | /26 | 255.255.255.192 | 172.30.94.65 – 172.30.94.126 | 172.30.94.65 |
| Tech & Staff | 30 | 172.30.94.128 | /25 | 255.255.255.128 | 172.30.94.129 – 172.30.94.254 | 172.30.94.129 |
| Internal Services | 40 | 172.30.95.0 | /26 | 255.255.255.192 | 172.30.95.1 – 172.30.95.62 | 172.30.95.1 |
| Future Expansion | — | 172.30.95.64 | /25 | 255.255.255.128 | 172.30.95.65 – 172.30.95.190 | N/A |

## 4.2 Device IP Addressing

| Device | Interface / Subinterface | IP Address | Subnet Mask | Default Gateway | Purpose |
|---|---|---|---|---|---|
| Botlhale Edge Router | G0/0/0 WAN | 203.0.113.2 | 255.255.255.252 | 203.0.113.1 | NAT Outside / ISP Link |
| Botlhale Edge Router | G0/0/1.10 | 172.30.94.1 | 255.255.255.192 | N/A | VLAN 10 Management Gateway |
| Botlhale Edge Router | G0/0/1.20 | 172.30.94.65 | 255.255.255.192 | N/A | VLAN 20 Customer Records Gateway |
| Botlhale Edge Router | G0/0/1.30 | 172.30.94.129 | 255.255.255.128 | N/A | VLAN 30 Staff Gateway |
| Botlhale Edge Router | G0/0/1.40 | 172.30.95.1 | 255.255.255.192 | N/A | VLAN 40 Internal Services Gateway |
| Botlhale Core Switch | SVI VLAN 10 | 172.30.94.2 | 255.255.255.192 | 172.30.94.1 | Switch Management |
| Admin Workstation | NIC | 172.30.94.10 | 255.255.255.192 | 172.30.94.1 | On-Site Admin / VLAN 10 |
| Customer DB Server | NIC | 172.30.94.70 | 255.255.255.192 | 172.30.94.65 | Confidential Customer Records / VLAN 20 |
| Staff PC 1 | NIC | 172.30.94.130 | 255.255.255.128 | 172.30.94.129 | General Staff / VLAN 30 |
| Staff PC 2 | NIC | 172.30.94.131 | 255.255.255.128 | 172.30.94.129 | General Staff / VLAN 30 |
| Internal Server | NIC | 172.30.95.10 | 255.255.255.192 | 172.30.95.1 | DNS / Web Applications / VLAN 40 |
| ISP Router | G0/0/0 WAN | 203.0.113.1 | 255.255.255.252 | N/A | Point-to-Point WAN Gateway |
| ISP Router | G0/0/1 Remote LAN | 198.51.100.1 | 255.255.255.0 | N/A | Remote Administrator Gateway |
| Off-Site Admin PC | NIC | 198.51.100.10 | 255.255.255.0 | 198.51.100.1 | Simulated Remote Endpoint / CR9 |
