# DHCP and server settings

Packet Tracer Server-PT devices are configured in the GUI (Services tab), not
the CLI, so their settings are recorded here instead.

## Inside server farm (VLAN 90, 10.11.11.32/27)

| Server | IP address | Gateway (HSRP VIP) |
|--------|------------|--------------------|
| RADIUS | 10.11.11.36 | 10.11.11.33 |
| DNS    | 10.11.11.37 | 10.11.11.33 |
| DHCP   | 10.11.11.38 | 10.11.11.33 |

## DMZ servers (10.11.11.0/27, static)

| Server  | IP address  |
|---------|-------------|
| FTP     | 10.11.11.10 |
| WEB     | 10.11.11.11 |
| EMAIL   | 10.11.11.12 |
| APP     | 10.11.11.13 |
| STORAGE | 10.11.11.14 |

Firewall interfaces in the DMZ: FW1 = 10.11.11.1, FW2 = 10.11.11.2.

## DHCP server pools (Services > DHCP on 10.11.11.38)

| Pool name | Default gateway (from notes) | Mask | DNS server |
|-----------|------------------------------|------|------------|
| LAN-POOL  | 172.16.0.1 | 255.255.0.0 | 10.11.11.37 |
| WLAN-POOL | 10.20.0.1  | 255.255.0.0 | 10.11.11.37 |
| MGT-POOL  | 192.168.10.11 (see note) | 255.255.255.0 | 10.11.11.37 |

> **Check MGT-POOL:** the HSRP virtual gateway for VLAN 10 is `192.168.10.1`.
> `192.168.10.11` in the original notes looks like the start address of the
> pool, not the gateway. Confirm in the DHCP service and fix if needed.
>
> **Fill in from the .pkt:** start IP address and maximum number of users for
> each pool, and confirm the DNS server value.

Clients in VLANs 10, 20 and 50 reach this server through `ip helper-address
10.11.11.38` on the core switch SVIs. VoIP phones (VLAN 70) get addresses from
the voice gateway's own `VOIP-POOL` instead.

## Wireless

- WLC-2504 management IP: `10.20.0.10`
- Each department has a lightweight AP (LAP) managed by the WLC.
- SSIDs/user groups: auditors, employees, corporate, guests.
- Credentials are deliberately **not** stored in this repo. Keep them in the
  .pkt or a private note.
