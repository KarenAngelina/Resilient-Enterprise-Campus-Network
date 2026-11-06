# Secure Company Network: Design and Implementation

A resilient, hierarchical enterprise network designed and simulated in
**Cisco Packet Tracer 8.2.2**. It has two ISP uplinks, a pair of perimeter
ASA firewalls with a DMZ, redundant multilayer core switches, departmental
access switches, centrally managed Wi-Fi, and VoIP.

## Topology

![Logical topology](screenshots/logical-view.png)

## Design at a glance

| Layer | Devices |
|-------|---------|
| Internet / ISPs | 2 ISP routers, simulated cloud with USA and CHINA user networks |
| Perimeter | 2 Cisco ASA firewalls (INSIDE, DMZ, OUTSIDE zones) |
| Core | 2 multilayer switches joined by an LACP EtherChannel |
| Access | 5 departmental switches across 3 floors (Admin, Finance, ICT, Sales & Management, HR & Logistics), plus a server switch and a DMZ switch |
| Services | DHCP, DNS, RADIUS (inside server farm); FTP, Web, Email, App, Storage (DMZ) |
| Wireless | WLC-2504 managing one lightweight AP per department |
| Voice | 2811 voice gateway with 9 extensions (501-509) |



## Lab credentials (for reviewers)

These are lab-only credentials used in the simulation.

| Access | Username | Password |
|--------|----------|----------|
| Console (all switches) | none | cisco |
| Enable mode | none | cisco |
| SSH | karen | cisco |


Just press enter for firewalls

## WiFi credentials:
WLC Login - Username : karen, password: Cisco@123
AUDITORS - Cisco@123
EMPLOYEES - Cisco@123
CORPORATE - Cisco@123
GUEST - Cisco@123

## How to log in

- **Console:** click a switch in Packet Tracer, open the CLI tab, enter
  the console password, then type `enable` and the enable password.
- **SSH:** SSH is allowed only from the management network
  (192.168.10.0/24). From a PC command prompt in that network:
  `ssh -l karen <switch management IP>`

## Requirements coverage

| # | Requirement | Where |
|---|-------------|-------|
| 2 | Hierarchical, redundant design | Topology image |
| 3 | Two ISPs | `configs/firewalls/` |
| 4 | WAPs + WLC | Topology, `configs/servers/` |
| 5 | VLANs 10, 20, 50, 70, 199 (plus 90 for servers) | `docs/ip-addressing-plan.md` |
| 6 | LACP EtherChannel | Topology; config export pending (`configs/README.md`) |
| 7 | Telephony service | `configs/voip/voice-gateway.txt` |
| 8 | PortFast + BPDU Guard | `configs/access-switches/` |
| 9 | Subnetting | `docs/ip-addressing-plan.md` |
| 10 | Basic device hardening | `configs/access-switches/` |
| 11, 12 | Inter-VLAN routing on multilayer switches | `configs/core-switches/` |
| 13 | DHCP server in server farm | `configs/servers/`, `ip helper-address` on SVIs |
| 14 | HSRP | `configs/core-switches/` |
| 15 | Static addressing for servers | `configs/servers/` |
| 16 | OSPF (firewalls, switches) | `configs/core-switches/`, `configs/firewalls/` |
| 17 | Standard ACL for SSH | `configs/access-switches/` |
| 18 | ASA routes, zones, policies, NAT | `configs/firewalls/` |

## Repository layout

```
.
├── README.md
├── secure_company_network.pkt     
├── screenshots/
├── docs/
│   ├── ip-addressing-plan.md
└── configs/
    ├── README.md
    ├── access-switches/
    ├── core-switches/
    ├── firewalls/
    ├── voip/
    └── servers/
```

## How to open

1. Install Cisco Packet Tracer 8.2.2 or newer.
2. Open `secure_company_network.pkt`.


## Author

Karen Angelina
