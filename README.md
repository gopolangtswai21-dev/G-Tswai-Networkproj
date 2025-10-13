# G-Tswai-Networkproj
Cisco Packet Tracer project demonstrating bus, mesh, star, ring, extended star, and hybrid topologies with IPv4/IPv6, VLANs, servers, and security.
A — BUS (Central Switch = 2960, PCs = 4)

IPv4 range: 192.168.1.1 – 192.168.1.4

IPv6 range provided: 2001:DB8:1::2 – 2001:DB8:1::7 (I assigned the first 4 IPv6 addrs to the 4 PCs)

| Device | Interface | IPv4 Address | Subnet Mask | IPv4 Gateway | IPv6 Address | IPv6 Prefix | IPv6 Gateway |

| ------ | --------- | -----------: | ------------: | ------------: | ------------- | ----------: | ------------------------------------: |

| PC1 | NIC | 192.168.1.1 | 255.255.255.0 | 192.168.1.254 | 2001:DB8:1::2 | /64 | 2001:DB8:1::1 (or ::ff if you prefer) |

| PC2 | NIC | 192.168.1.2 | 255.255.255.0 | 192.168.1.254 | 2001:DB8:1::3 | /64 | 2001:DB8:1::1 |

| PC3 | NIC | 192.168.1.3 | 255.255.255.0 | 192.168.1.254 | 2001:DB8:1::4 | /64 | 2001:DB8:1::1 |

| PC4 | NIC | 192.168.1.4 | 255.255.255.0 | 192.168.1.254 | 2001:DB8:1::5 | /64 | 2001:DB8:1::1 |

B — MESH (Central Switch = 2960, PCs = 6)
Router-on-a-Stick Configuration — VLAN 10 | 20 | 30






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












IPv4 range: 192.168.2.1 – 192.168.2.6

IPv6 range: 2001:DB8:2::1 – 2001:DB8:2::6 (/64)

| Device | Interface | IPv4 Address | Mask | IPv4 Gateway | IPv6 Address | Prefix | IPv6 Gateway |

| ------ | --------- | -----------: | ---: | ------------: | ------------- | -----: | -------------: |

| PC1 | NIC | 192.168.2.1 | /24 | 192.168.2.254 | 2001:DB8:2::1 | /64 | 2001:DB8:2::ff |

| PC2 | NIC | 192.168.2.2 | /24 | 192.168.2.254 | 2001:DB8:2::2 | /64 | 2001:DB8:2::ff |

| PC3 | NIC | 192.168.2.3 | /24 | 192.168.2.254 | 2001:DB8:2::3 | /64 | 2001:DB8:2::ff |

| PC4 | NIC | 192.168.2.4 | /24 | 192.168.2.254 | 2001:DB8:2::4 | /64 | 2001:DB8:2::ff |

| PC5 | NIC | 192.168.2.5 | /24 | 192.168.2.254 | 2001:DB8:2::5 | /64 | 2001:DB8:2::ff |

| PC6 | NIC | 192.168.2.6 | /24 | 192.168.2.254 | 2001:DB8:2::6 | /64 | 2001:DB8:2::ff |

C — STAR (Central Switch = 2960, PCs = 5)

IPv4: 192.168.3.1 – 192.168.3.5

IPv6: 2001:DB8:3::1 – 2001:DB8:3::5

| Device | Interface | IPv4 Address | Mask | IPv4 Gateway | IPv6 Address | Prefix | IPv6 Gateway |

| ------ | --------- | -----------: | ---: | ------------: | ------------: | -----: | -------------: |

| PC1 | NIC | 192.168.3.1 | /24 | 192.168.3.254 | 2001:DB8:3::1 | /64 | 2001:DB8:3::ff |

| PC2 | NIC | 192.168.3.2 | /24 | 192.168.3.254 | 2001:DB8:3::2 | /64 | 2001:DB8:3::ff |

| PC3 | NIC | 192.168.3.3 | /24 | 192.168.3.254 | 2001:DB8:3::3 | /64 | 2001:DB8:3::ff |

| PC4 | NIC | 192.168.3.4 | /24 | 192.168.3.254 | 2001:DB8:3::4 | /64 | 2001:DB8:3::ff |

| PC5 | NIC | 192.168.3.5 | /24 | 192.168.3.254 | 2001:DB8:3::5 | /64 | 2001:DB8:3::ff |

D — RING (Central Switch = 2960, PCs = 4)

IPv4: 192.168.4.1 – 192.168.4.4

IPv6: 2001:DB8:4::1 – 2001:DB8:4::4

| Device | Interface | IPv4 Address | Mask | IPv4 Gateway | IPv6 Address | Prefix | IPv6 Gateway |

| ------ | --------- | -----------: | ---: | ------------: | ------------: | -----: | -------------: |

| PC1 | NIC | 192.168.4.1 | /24 | 192.168.4.254 | 2001:DB8:4::1 | /64 | 2001:DB8:4::ff |

| PC2 | NIC | 192.168.4.2 | /24 | 192.168.4.254 | 2001:DB8:4::2 | /64 | 2001:DB8:4::ff |

| PC3 | NIC | 192.168.4.3 | /24 | 192.168.4.254 | 2001:DB8:4::3 | /64 | 2001:DB8:4::ff |

| PC4 | NIC | 192.168.4.4 | /24 | 192.168.4.254 | 2001:DB8:4::4 | /64 | 2001:DB8:4::ff |

E — EXTENDED RING (Central Switch = 2960, PCs = 12)

IPv4: 192.168.5.1 – 192.168.5.12

IPv6: 2001:DB8:5::1 – 2001:DB8:5::12

| Device | Interface | IPv4 Address | Mask | IPv4 Gateway | IPv6 Address | Prefix | IPv6 Gateway |

| ------ | --------- | -----------: | ---: | ------------: | -------------: | -----: | -------------: |

| PC1 | NIC | 192.168.5.1 | /24 | 192.168.5.254 | 2001:DB8:5::1 | /64 | 2001:DB8:5::ff |

| PC2 | NIC | 192.168.5.2 | /24 | 192.168.5.254 | 2001:DB8:5::2 | /64 | 2001:DB8:5::ff |

| PC3 | NIC | 192.168.5.3 | /24 | 192.168.5.254 | 2001:DB8:5::3 | /64 | 2001:DB8:5::ff |

| PC4 | NIC | 192.168.5.4 | /24 | 192.168.5.254 | 2001:DB8:5::4 | /64 | 2001:DB8:5::ff |

| PC5 | NIC | 192.168.5.5 | /24 | 192.168.5.254 | 2001:DB8:5::5 | /64 | 2001:DB8:5::ff |

| PC6 | NIC | 192.168.5.6 | /24 | 192.168.5.254 | 2001:DB8:5::6 | /64 | 2001:DB8:5::ff |

| PC7 | NIC | 192.168.5.7 | /24 | 192.168.5.254 | 2001:DB8:5::7 | /64 | 2001:DB8:5::ff |

| PC8 | NIC | 192.168.5.8 | /24 | 192.168.5.254 | 2001:DB8:5::8 | /64 | 2001:DB8:5::ff |

| PC9 | NIC | 192.168.5.9 | /24 | 192.168.5.254 | 2001:DB8:5::9 | /64 | 2001:DB8:5::ff |

| PC10 | NIC | 192.168.5.10 | /24 | 192.168.5.254 | 2001:DB8:5::10 | /64 | 2001:DB8:5::ff |

| PC11 | NIC | 192.168.5.11 | /24 | 192.168.5.254 | 2001:DB8:5::11 | /64 | 2001:DB8:5::ff |

| PC12 | NIC | 192.168.5.12 | /24 | 192.168.5.254 | 2001:DB8:5::12 | /64 | 2001:DB8:5::ff |

F — HYBRID NETWORK

Hybrid — RING

IPv4: 192.168.10.2 – 192.168.10.5 → gateway 192.168.10.1

IPv6: FD00:ABCD:10::2 – FD00:ABCD:10::5 → gateway FD00:ABCD:10::1

| Device | IPv4 | Mask | IPv4 GW | IPv6 | Prefix | IPv6 GW |

| -------- | -----------: | ---: | -----------: | --------------: | -----: | --------------: |

| RING-PC1 | 192.168.10.2 | /24 | 192.168.10.1 | FD00:ABCD:10::2 | /64 | FD00:ABCD:10::1 |

| RING-PC2 | 192.168.10.3 | /24 | 192.168.10.1 | FD00:ABCD:10::3 | /64 | FD00:ABCD:10::1 |

| RING-PC3 | 192.168.10.4 | /24 | 192.168.10.1 | FD00:ABCD:10::4 | /64 | FD00:ABCD:10::1 |

| RING-PC4 | 192.168.10.5 | /24 | 192.168.10.1 | FD00:ABCD:10::5 | /64 | FD00:ABCD:10::1 |

Hybrid — BUS

IPv4: 192.168.30.2 – 192.168.30.5 → gateway 192.168.30.1

IPv6: FD00:ABCD:30::2 – FD00:ABCD:30::5 → gateway FD00:ABCD:30::1

| Device | IPv4 | Mask | IPv4 GW | IPv6 | Prefix | IPv6 GW |

| ------- | -----------: | ---: | -----------: | --------------: | -----: | --------------: |

| BUS-PC1 | 192.168.30.2 | /24 | 192.168.30.1 | FD00:ABCD:30::2 | /64 | FD00:ABCD:30::1 |

| BUS-PC2 | 192.168.30.3 | /24 | 192.168.30.1 | FD00:ABCD:30::3 | /64 | FD00:ABCD:30::1 |

| BUS-PC3 | 192.168.30.4 | /24 | 192.168.30.1 | FD00:ABCD:30::4 | /64 | FD00:ABCD:30::1 |

| BUS-PC4 | 192.168.30.5 | /24 | 192.168.30.1 | FD00:ABCD:30::5 | /64 | FD00:ABCD:30::1 |

Hybrid — STAR

IPv4: 192.168.40.2 – 192.168.40.6 → gateway 192.168.40.1

IPv6: FD00:ABCD:40::2 – FD00:ABCD:40::6 → gateway FD00:ABCD:40::1

| Device | IPv4 | Mask | IPv4 GW | IPv6 | Prefix | IPv6 GW |

| -------- | -----------: | ---: | -----------: | --------------: | -----: | --------------: |

| STAR-PC1 | 192.168.40.2 | /24 | 192.168.40.1 | FD00:ABCD:40::2 | /64 | FD00:ABCD:40::1 |

| STAR-PC2 | 192.168.40.3 | /24 | 192.168.40.1 | FD00:ABCD:40::3 | /64 | FD00:ABCD:40::1 |

| STAR-PC3 | 192.168.40.4 | /24 | 192.168.40.1 | FD00:ABCD:40::4 | /64 | FD00:ABCD:40::1 |

| STAR-PC4 | 192.168.40.5 | /24 | 192.168.40.1 | FD00:ABCD:40::5 | /64 | FD00:ABCD:40::1 |

| STAR-PC5 | 192.168.40.6 | /24 | 192.168.40.1 | FD00:ABCD:40::6 | /64 | FD00:ABCD:40::1 |

Hybrid — MESH

IPv4: 192.168.20.2 – 192.168.20.6 → gateway 192.168.20.1

IPv6: FD00:ABCD:20::2 – FD00:ABCD:20::6 → gateway FD00:ABCD:20::1

| Device | IPv4 | Mask | IPv4 GW | IPv6 | Prefix | IPv6 GW |

| -------- | -----------: | ---: | -----------: | --------------: | -----: | --------------: |

| MESH-PC1 | 192.168.20.2 | /24 | 192.168.20.1 | FD00:ABCD:20::2 | /64 | FD00:ABCD:20::1 |

| MESH-PC2 | 192.168.20.3 | /24 | 192.168.20.1 | FD00:ABCD:20::3 | /64 | FD00:ABCD:20::1 |

| MESH-PC3 | 192.168.20.4 | /24 | 192.168.20.1 | FD00:ABCD:20::4 | /64 | FD00:ABCD:20::1 |

| MESH-PC4 | 192.168.20.5 | /24 | 192.168.20.1 | FD00:ABCD:20::5 | /64 | FD00:ABCD:20::1 |

| MESH-PC5 | 192.168.20.6 | /24 | 192.168.20.1 | FD00:ABCD:20::6 | /64 | FD00:ABCD:20::1 |

Router-on-a-Stick Configuration — VLAN 10 | 20 | 30

Project Overview

This configuration demonstrates **Inter-VLAN Routing** using the *Router-on-a-Stick* method in Cisco Packet Tracer.

A single router interface is used to route traffic between **VLAN 10**, **VLAN 20**, and **VLAN 30** through subinterfaces.

Network Design Summary

| VLAN | VLAN Name | IPv4 Network | IPv4 Gateway | IPv6 Network | IPv6 Gateway | IP Range |

|------|------------|---------------------|--------------------|--------------------------|----------------------|----------------------------------|

| 10 | VLAN10 | 192.168.10.0/24 | 192.168.10.1 | 2001:DB8:10::/64 | 2001:DB8:10::1 | 192.168.10.10 - 192.168.10.12 / 2001:DB8:10::10 - 2001:DB8:10::12 |

| 20 | VLAN20 | 192.168.20.0/24 | 192.168.20.1 | 2001:DB8:20::/64 | 2001:DB8:20::1 | 192.168.20.10 - 192.168.20.12 / 2001:DB8:20::10 - 2001:DB8:20::12 |

| 30 | VLAN30 | 192.168.30.0/24 | 192.168.30.1 | 2001:DB8:30::/64 | 2001:DB8:30::1 | 192.168.30.10 - 192.168.30.12 / 2001:DB8:30::10 - 2001:DB8:30::12 |

**Subnet Mask:** 255.255.255.0 (for all VLANs)

**Router Interface:** GigabitEthernet0/0

**Switch Model:** 2960 (Trunk Port)

**Router Model:** ISR 4321 / 2911 / 2811 (any supported)

Router Configuration (Sample)

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











