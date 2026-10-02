Milestone 2: Client Implementation (CLI-142)

**Client:** Botlhale Technologies (Rustenburg), Technology industry
**Addressing block:** 172.30.94.0/23
**Assigned challenge:** NAT (inside/outside address translation)
**Design constraint:** Customer records are confidential, access is controlled
**Change request CR9:** Secure remote management for one off-site administrator

Topology
R1 (edge router) connects SW1 (inside) and an ISP router (outside). Inside hosts sit in VLAN 10 Staff, VLAN 20 Servers, VLAN 30 Guest and VLAN 99 Management. The off-site admin and an Internet server sit on the outside network.

### IP addressing
| VLAN | Purpose | Subnet | Gateway |
| 10 | Staff | 172.30.94.0/25 | 172.30.94.1 |
| 20 | Servers | 172.30.94.128/26 | 172.30.94.129 |
| 99 | Management | 172.30.94.192/27 | 172.30.94.193 |
| 30 | Guest | 172.30.95.0/25 | 172.30.95.1 |

Outside link: 203.0.113.0/29 (R1 .2, ISP .1). Off-site network: 198.51.100.0/24.

### NAT
- PAT (overload) on R1 g0/1 shares 203.0.113.2 among all inside hosts.
- Static NAT maps the web server 172.30.94.130 to 203.0.113.3.
- Verified with `show ip nat translations` and `show ip nat statistics`.

### Confidential records
An ACL (RECORDS-PROTECT) on R1 g0/0.20 allows only Staff and Management to reach the Records server. Guest and outside traffic is blocked. The Records server has no public address.

### CR9: Secure remote management
SSH version 2 only on the VTY lines of R1 and SW1. An access-class permits only the off-site admin PC (198.51.100.10) and the management subnet. Telnet is refused.

### Files
- `botlhale.pkt`: Packet Tracer file (open with Cisco Packet Tracer)
- `configs/`: running configs for R1, SW1 and ISP
- `screenshots/`: numbered testing evidence
