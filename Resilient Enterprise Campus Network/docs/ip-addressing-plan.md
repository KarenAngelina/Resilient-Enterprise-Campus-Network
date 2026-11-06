# IP addressing plan

## Address blocks (from the project brief)

| Network | Block |
|---------|-------|
| Management | 192.168.10.0/24 |
| WLAN | 10.20.0.0/16 |
| LAN | 172.16.0.0/16 |
| VoIP | 172.30.0.0/16 |
| DMZ | 10.11.11.0/27 |
| Public (ISP 1) | 105.100.50.0/30 |
| Public (ISP 2) | 197.200.100.0/30 |



## VLANs and gateways

| VLAN | Name | Subnet | HSRP virtual IP | CORE-SW1 | CORE-SW2 | STP root |
|------|------|--------|-----------------|----------|----------|----------|
| 10 | Management | 192.168.10.0/24 | 192.168.10.1 | .2 | .3 | SW1 primary, SW2 secondary |
| 20 | LAN | 172.16.0.0/16 | 172.16.0.1 | .2 | .3 | SW1 primary, SW2 secondary |
| 50 | WLAN | 10.20.0.0/16 | 10.20.0.1 | .2 | .3 | SW2 primary, SW1 secondary |
| 70 | VoIP | 172.30.0.0/16 | 172.30.0.1 (voice gateway) | none | none | SW2 primary, SW1 secondary |
| 90 | Servers | 10.11.11.32/27 | 10.11.11.33 | .34 | .35 | SW2 primary, SW1 secondary |
| 199 | Blackhole | none | none | none | none | unused ports, shut down |

Access-switch native VLAN on trunks: 1000.

## Fixed hosts

| Device | IP |
|--------|----|
| DHCP server | 10.11.11.38 |
| DNS server | 10.11.11.37 |
| RADIUS server | 10.11.11.36 |
| WLC-2504 | 10.20.0.10 |
| DMZ FTP / WEB / EMAIL / APP / STORAGE | 10.11.11.10 / .11 / .12 / .13 / .14 |
| FW1 DMZ / FW2 DMZ | 10.11.11.1 / 10.11.11.2 |

## Point-to-point links

| Link | Subnet | Addresses |
|------|--------|-----------|
| FW1 INSIDE1 | 10.2.2.0/30 | FW1 .2 |
| FW2 INSIDE2 | 10.2.2.4/30 | FW2 .6 |
| FW1 INSIDE2 | 10.2.2.8/30 | FW1 .10 |
| FW2 INSIDE1 | 10.2.2.12/30 | FW2 .14 |
| FW1 OUTSIDE1 to ISP | 105.100.50.0/30 | FW1 .2, ISP .1 |
| FW1 OUTSIDE2 to ISP | 197.200.100.0/30 | FW1 .2, ISP .1 |
| FW2 OUTSIDE2 to ISP | 105.100.50.4/30 | FW2 .6, ISP .5 |
| FW2 OUTSIDE1 to ISP | 197.200.100.4/30 | FW2 .6, ISP .5 |

CORE-SW1's OSPF config advertises 10.2.2.8/30 and 10.2.2.12/30. Fill in which
firewall-facing links CORE-SW2 uses (expected: 10.2.2.0/30 and 10.2.2.4/30)
once its config is exported.

## Simulated internet

| Link | Subnet |
|------|--------|
| TATA-ISP to cloud | 20.20.20.0/30 |
| AIRTEL-ISP to cloud | 30.30.30.0/30 |
| Cloud to USA-USER router | 8.0.0.0/30 |
| Cloud to CHINA-USER router | 9.0.0.0/30 |
| USA-USER LAN | 100.200.50.0/24 |
| CHINA-USER LAN | 100.200.60.0/24 |

## Voice

| Item | Value |
|------|-------|
| Voice gateway subinterface | Fa0/0.70, 172.30.0.1/16 |
| Extensions | 501 to 509 |
