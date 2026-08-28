# Logical Topology

## VLAN 10 — Management

- VLAN ID: 10
- Network: 172.30.94.0/26
- Gateway: 172.30.94.1
- Core Switch SVI: 172.30.94.2
- Purpose: Network-device management, administrative access and CR9 management functionality.

## VLAN 20 — Customer Records

- VLAN ID: 20
- Network: 172.30.94.64/26
- Gateway: 172.30.94.65
- Customer DB Server: 172.30.94.70
- Purpose: Confidential customer records.
- Access will be controlled using ACLs.

## VLAN 30 — Tech / Staff

- VLAN ID: 30
- Network: 172.30.94.128/25
- Gateway: 172.30.94.129
- Staff PC 1: 172.30.94.130
- Staff PC 2: 172.30.94.131
- Purpose: Staff and technical workstations.

## VLAN 40 — Internal Services

- VLAN ID: 40
- Network: 172.30.95.0/26
- Gateway: 172.30.95.1
- Internal Server: 172.30.95.10
- Purpose: DNS, internal web applications and other internal services.

## Inter-VLAN Routing

The Botlhale Edge Router will provide inter-VLAN routing using router subinterfaces:

- G0/0/1.10 → VLAN 10 → 172.30.94.1
- G0/0/1.20 → VLAN 20 → 172.30.94.65
- G0/0/1.30 → VLAN 30 → 172.30.94.129
- G0/0/1.40 → VLAN 40 → 172.30.95.1

The connection between the Edge Router and Core Switch will use an 802.1Q trunk.

## Security

VLAN 20 contains the confidential Customer DB Server. ACLs will restrict unauthorised access, particularly from general staff devices.

## NAT

The Edge Router will perform NAT between the internal networks and the external WAN.

- NAT Inside: 172.30.94.0/23
- NAT Outside: 203.0.113.0/30

## CR9 — Secure Remote Management

The off-site administrator is:

- IP Address: 198.51.100.10
- Gateway: 198.51.100.1

The administrator will use secure SSH access to manage the network according to CR9.
