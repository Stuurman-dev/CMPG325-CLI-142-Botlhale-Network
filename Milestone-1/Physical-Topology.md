# Physical Topology

## Physical Devices

The topology contains:

- ISP Router
- Botlhale Edge Router
- Botlhale Core Switch
- SW-1 — Admin / Customer Records
- SW-2 — Tech / Staff
- SW-3 — Management / Internal Services
- Admin Workstation
- Customer DB Server
- Staff PC 1
- Staff PC 2
- Internal Server
- Off-Site Administrator PC

## Physical Connections

- ISP Router G0/0/0 → Botlhale Edge Router G0/0/0
- Botlhale Edge Router G0/0/1 → Botlhale Core Switch
- Botlhale Core Switch → SW-1
- Botlhale Core Switch → SW-2
- Botlhale Core Switch → SW-3
- SW-1 → Customer DB Server
- SW-1 → Admin PC
- SW-2 → Staff PC 1
- SW-2 → Staff PC 2
- SW-3 → Internal Server
- ISP Router G0/0/1 → Off-Site Admin PC

## Router Connections

### WAN
- Edge Router G0/0/0: 203.0.113.2/30
- ISP Router G0/0/0: 203.0.113.1/30

### Internal
- Edge Router G0/0/1 → Core Switch
- Internal connection will use an 802.1Q trunk.
