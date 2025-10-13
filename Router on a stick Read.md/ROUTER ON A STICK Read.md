**Router-on-a-Stick Configuration — VLAN 10 | 20 | 30**



**Project Overview**



This configuration demonstrates \*\*Inter-VLAN Routing\*\* using the \*Router-on-a-Stick\* method in Cisco Packet Tracer.  

A single router interface is used to route traffic between \*\*VLAN 10\*\*, \*\*VLAN 20\*\*, and \*\*VLAN 30\*\* through subinterfaces.



---



Network Design Summary



| VLAN | VLAN Name | IPv4 Network        | IPv4 Gateway      | IPv6 Network            | IPv6 Gateway        | IP Range                        |

|------|------------|---------------------|--------------------|--------------------------|----------------------|----------------------------------|

| 10   | VLAN10     | 192.168.10.0/24     | 192.168.10.1       | 2001:DB8:10::/64         | 2001:DB8:10::1       | 192.168.10.10 - 192.168.10.12 / 2001:DB8:10::10 - 2001:DB8:10::12 |

| 20   | VLAN20     | 192.168.20.0/24     | 192.168.20.1       | 2001:DB8:20::/64         | 2001:DB8:20::1       | 192.168.20.10 - 192.168.20.12 / 2001:DB8:20::10 - 2001:DB8:20::12 |

| 30   | VLAN30     | 192.168.30.0/24     | 192.168.30.1       | 2001:DB8:30::/64         | 2001:DB8:30::1       | 192.168.30.10 - 192.168.30.12 / 2001:DB8:30::10 - 2001:DB8:30::12 |



\*\*Subnet Mask:\*\* `255.255.255.0` (for all VLANs)  

\*\*Router Interface:\*\* `GigabitEthernet0/0`   

\*\*Switch Model:\*\* 2960 (Trunk Port)  

\*\*Router Model:\*\* ISR 4321 / 2911 / 2811 (any supported)



---



**Router Configuration (Sample)**



```bash

enable

configure terminal



! Subinterface for VLAN 10

interface g0/0.10

&nbsp;encapsulation dot1Q 10

&nbsp;ip address 192.168.10.1 255.255.255.0

&nbsp;ipv6 address 2001:DB8:10::1/64

&nbsp;no shutdown



! Subinterface for VLAN 20

interface g0/0.20

&nbsp;encapsulation dot1Q 20

&nbsp;ip address 192.168.20.1 255.255.255.0

&nbsp;ipv6 address 2001:DB8:20::1/64

&nbsp;no shutdown



! Subinterface for VLAN 30

interface g0/0.30

&nbsp;encapsulation dot1Q 30

&nbsp;ip address 192.168.30.1 255.255.255.0

&nbsp;ipv6 address 2001:DB8:30::1/64

&nbsp;no shutdown



! Main interface (do not assign IP)

interface g0/0

&nbsp;no shutdown





Switch configuration

enable

configure terminal



vlan 10

&nbsp;name VLAN10

vlan 20

&nbsp;name VLAN20

vlan 30

&nbsp;name VLAN30



interface range f0/1 - 3

&nbsp;switchport mode access

&nbsp;switchport access vlan 10



interface range f0/4 - 6

&nbsp;switchport mode access

&nbsp;switchport access vlan 20



interface range f0/7 - 9

&nbsp;switchport mode access

&nbsp;switchport access vlan 30



interface g0/1

&nbsp;switchport mode trunk

&nbsp;switchport trunk allowed vlan 10,20,30



| VLAN | Device | IPv4 Address  | Subnet Mask   | Default Gateway | IPv6 Address       | IPv6 Gateway   |

| ---- | ------ | ------------- | ------------- | --------------- | ------------------ | -------------- |

| 10   | PC1    | 192.168.10.10 | 255.255.255.0 | 192.168.10.1    | 2001:DB8:10::10/64 | 2001:DB8:10::1 |

| 10   | PC2    | 192.168.10.11 | 255.255.255.0 | 192.168.10.1    | 2001:DB8:10::11/64 | 2001:DB8:10::1 |

| 20   | PC3    | 192.168.20.10 | 255.255.255.0 | 192.168.20.1    | 2001:DB8:20::10/64 | 2001:DB8:20::1 |

| 20   | PC4    | 192.168.20.11 | 255.255.255.0 | 192.168.20.1    | 2001:DB8:20::11/64 | 2001:DB8:20::1 |

| 30   | PC5    | 192.168.30.10 | 255.255.255.0 | 192.168.30.1    | 2001:DB8:30::10/64 | 2001:DB8:30::1 |

| 30   | PC6    | 192.168.30.11 | 255.255.255.0 | 192.168.30.1    | 2001:DB8:30::11/64 | 2001:DB8:30::1 |



**VERIFICATION COMMANDS**



! 1. Check interface status

show ip interface brief

show ipv6 interface brief



! 2. Check trunk status

show interfaces trunk



! 3. Check VLANs on switch

show vlan brief



! 4. Verify subinterface configuration

show running-config interface g0/0.10

show running-config interface g0/0.20

show running-config interface g0/0.30



! 5. Check routing table

show ip route

show ipv6 route



! 6. Check encapsulation \& counters

show interfaces g0/0.10

show interfaces g0/0.20

show interfaces g0/0.30



**Testing Inter-VLAN Communication**

**From PC in VLAN 10**



ping 192.168.20.10

ping 192.168.30.10

ping 2001:DB8:20::10

ping 2001:DB8:30::10



**From PC in VLAN 20**

ping 192.168.10.10

ping 192.168.30.10



**From PC in VLAN 30**

ping 192.168.10.10

ping 192.168.20.10











