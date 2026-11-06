## Project - Resilient Enterprise Campus Network 
The company emphasizes top-tier network performance, redundancy, scalability, and availability, requiring a comprehensive network design and implementation.

The organization has allocated the following IP address ranges for this project:
Management Network: 192.168.10.0/24
WLAN: 10.20.0.0/16
LAN: 172.16.0.0/16
VoIP: 172.30.0.0/16
DMZ: 10.11.11.0/27
Public Addresses: 105.100.50.0/30 (TATA-ISP) and 197.200.100.0/30 (AIRTEL-ISP)

## Technical Requirements: 
1. Design Tool: Utilize Cisco Packet Tracer for designing and implementing the network solution.

2. Hierarchical Design: Implement a hierarchical model that incorporates redundancy for enhanced network resilience.

3. ISPs: Establish connectivity to the two ISPs within the network infrastructure.

4. WLC: Ensure that each department is equipped with a Wireless Access Point (WAP) to provide WIFI access to employees, corporate users, external auditors, and guests, all centrally managed by the Wireless LAN Controllers (WLC).

5. VLAN: Maintain VLANs with the following IDs: 10 for Management, 20 for LAN, 50 for WLAN, 70 for VoIP, and finally 199 for Blackhole in which all unused ports are placed.

6. EtherChannel: Implement the Link Aggregation Control Protocol (LACP) for EtherChannel configuration, enhancing link aggregation and redundancy.

7. Telephony Service: Configure VoIP on the voice gateway router and allocate dial numbers. 

8. STP PortFast and BPDUGuard: Configure Spanning Tree Protocol (STP) PortFast and BPDUguard to expedite port transitions from blocking to forwarding states.

9. Subnetting: Utilize subnetting techniques to allocate the appropriate number of IP addresses to each network group.

10. Basic Settings: Configure fundamental device settings, including hostnames, console passwords, enable passwords, banner messages, password encryption, and disable IP domain lookup.

11. Inter-VLAN Routing: Enable devices in all departments to communicate with one another by configuring the respective multilayer switch for inter-VLAN routing.

12. Core Switch: Assign IP addresses to Multilayer Switches to enable both routing and switching functionalities.

13. DHCP Server: Ensure that all devices in the network obtain IP addresses dynamically from the DHCP servers located at the server farm site.

14. HSRP: Implement high-availability router protocols such as HSRP to achieve redundancy, load balancing, and failover capabilities.

15. Static Addressing: Allocate static IP addresses to devices located in the server room.

16. Routing Protocol: Utilize Open Shortest Path First (OSPF) as the routing protocol to advertise routes on the firewall, routers, and multilayer switches.

17. Standard ACL for SSH: Establish a simple standard Access Control List (ACL) on the VTY line to permit remote administrative tasks via SSH only for the Senior Network Security Engineer PC.

18. Cisco ASA Firewall: Configure default static routes, basic settings, security levels, zones, and policies on the Cisco ASA Firewall to define access control and resource utilization within the network.

19. Final Testing: Conduct thorough testing to verify proper communication and ensure that all configured elements function as intended.
