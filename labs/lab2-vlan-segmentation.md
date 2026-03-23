# Lab 2 — VLAN Segmentation (Router on a Stick)

## Objective
Extend the Lab 1 topology by implementing VLAN segmentation to separate data and voice traffic. Configure inter-VLAN routing using a Router on a Stick topology with 802.1Q trunking.

## Tools
- Cisco Packet Tracer 9.0
- Cisco ISR4321 Router
- Cisco 2960-24TT Switch
- 3x PC-PT Workstations

## Topology
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

## IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Gateway | VLAN |
|--------|-----------|------------|-------------|---------|------|
| Main_Router | G0/0/0.10 | 192.168.10.1 | 255.255.255.0 | — | 10 |
| Main_Router | G0/0/0.20 | 192.168.20.1 | 255.255.255.0 | — | 20 |
| Workstation1 | NIC | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 | 10 |
| Workstation2 | NIC | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 | 10 |
| Workstation3 | NIC | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 | 20 |

## Switch Configuration
```
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

## Router Configuration
```
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

## Results

| Test | Source | Destination | Result | TTL |
|------|--------|-------------|--------|-----|
| Same VLAN | WS1 (10.10) | WS2 (10.11) | 4/4 success | 128 |
| Cross VLAN | WS1 (10.10) | WS3 (20.10) | 4/4 success | 127 |

## TTL Analysis
- TTL=128 on same-VLAN ping confirmed traffic was switched at Layer 2 — no router involved
- TTL=127 on cross-VLAN ping confirmed traffic passed through the router — decremented by 1

## What I Learned
- VLANs logically separate devices on the same physical switch into isolated networks
- A Layer 2 switch cannot route between VLANs — a router or Layer 3 switch is required
- Router on a Stick uses a single physical link with 802.1Q subinterfaces to route between VLANs
- Access ports carry traffic for a single VLAN — end devices are unaware of VLAN tagging
- Trunk ports carry traffic for multiple VLANs simultaneously using dot1Q tags
- TTL values in ping results provide proof of whether traffic was switched or routed
- QoS policies applied to a Voice VLAN prevent jitter and latency on VoIP calls
