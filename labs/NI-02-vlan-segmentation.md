[NI-02-vlan-segmentation.md](https://github.com/user-attachments/files/26523754/NI-02-vlan-segmentation.md)
# NI-02 — VLAN Segmentation (Router on a Stick)

> **Implemented VLAN segmentation on a Cisco switch, configured inter-VLAN routing via 802.1Q subinterfaces, and used TTL analysis to prove whether traffic was switched or routed.**

**Skills demonstrated:** VLAN configuration · 802.1Q trunking · Router on a Stick · Inter-VLAN routing · TTL analysis · Packet capture validation
**Tools:** Cisco Packet Tracer 9.0 · Cisco ISR4321 Router · Cisco 2960-24TT Switch
**Date:** 2026-03

---

## What I Did

Extended the Lab 1 LAN topology by introducing VLAN segmentation to separate data and voice traffic. Configured access and trunk ports on the switch, created subinterfaces on the router with 802.1Q encapsulation, and validated both same-VLAN and cross-VLAN connectivity. Used TTL values in ping output as proof of whether traffic was switched at Layer 2 or routed at Layer 3.

```
Main_Router
  G0/0/0.10 — 192.168.10.1 (VLAN 10 - Data)
  G0/0/0.20 — 192.168.20.1 (VLAN 20 - Voice)
        |
Main_Switch (Trunk on G0/1)
   |        |        |
Fa0/1    Fa0/2    Fa0/3
VLAN10   VLAN10   VLAN20
WS1      WS2      WS3
.10      .11      .10
```

**IP Addressing:**

| Device | Interface | IP | Gateway | VLAN |
|--------|-----------|-----|---------|------|
| Main_Router | G0/0/0.10 | 192.168.10.1 | — | 10 |
| Main_Router | G0/0/0.20 | 192.168.20.1 | — | 20 |
| Workstation1 | NIC | 192.168.10.10 | 192.168.10.1 | 10 |
| Workstation2 | NIC | 192.168.10.11 | 192.168.10.1 | 10 |
| Workstation3 | NIC | 192.168.20.10 | 192.168.20.1 | 20 |

**Switch configuration:**

```cisco
enable
configure terminal
vlan 10
 name Data
vlan 20
 name Voice
interface FastEthernet0/1
 switchport mode access
 switchport access vlan 10
interface FastEthernet0/2
 switchport mode access
 switchport access vlan 10
interface FastEthernet0/3
 switchport mode access
 switchport access vlan 20
interface GigabitEthernet0/1
 switchport mode trunk
end
```

**Router configuration:**

```cisco
enable
configure terminal
interface GigabitEthernet0/0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
interface GigabitEthernet0/0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
end
```

---

## What I Found

| Test | Source | Destination | Result | TTL |
|------|--------|-------------|--------|-----|
| Same VLAN | WS1 (10.10) | WS2 (10.11) | 4/4 success | 128 |
| Cross VLAN | WS1 (10.10) | WS3 (20.10) | 4/4 success | 127 |

The TTL difference is the key finding. Same-VLAN traffic returned TTL=128 the switch forwarded it at Layer 2, the router never touched it. Cross-VLAN traffic returned TTL=127 the router decremented it by 1 as it routed the packet between subinterfaces. TTL became functional proof of the traffic path.

---

## What I Learned

VLANs don't just organize devices, they enforce isolation. A device in VLAN 10 is completely invisible to VLAN 20 at Layer 2. The only way traffic crosses is through a Layer 3 device, which means every inter-VLAN packet is a routing decision with a visible cost via the TTL decrement.

Router on a Stick is usable but has an obvious bottleneck: all inter-VLAN traffic shares one physical link. In a real environment with significant voice and data traffic that single trunk becomes a chokepoint. A Layer 3 switch solves this but costs more.

Access ports and trunk ports serve completely different purposes. End devices connect to access ports and never see VLAN tags the switch handles tagging transparently. Trunk ports carry tagged traffic for multiple VLANs simultaneously between switches and routers. Getting that distinction wrong would break the entire topology.

---

*Previous: [NI-01 — LAN Deployment](NI-01-lan-deployment.md)*
*Next: [NI-03 — Wireshark Traffic Analysis](NI-03-wireshark-analysis.md)*
