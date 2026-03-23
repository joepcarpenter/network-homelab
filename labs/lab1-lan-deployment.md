# Lab 1 — Small Business LAN Deployment

## Objective
Deploy a functional small business LAN using a Cisco router and switch, assign IP addressing, and validate end-to-end connectivity between workstations.

## Tools
- Cisco Packet Tracer 9.0
- Cisco ISR4321 Router
- Cisco 2960-24TT Switch
- 3x PC-PT Workstations

## Topology
```
Main_Router (192.168.1.1)
      |
Main_Switch
   |     |     |
WS1   WS2   WS3
.10   .11   .12
```

## IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Gateway |
|--------|-----------|------------|-------------|---------|
| Main_Router | G0/0/0 | 192.168.1.1 | 255.255.255.0 | — |
| Workstation1 | NIC | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| Workstation2 | NIC | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| Workstation3 | NIC | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |

## Router Configuration
```
enable
configure terminal
interface GigabitEthernet0/0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
end
```

## Results

All workstations pinged successfully — 4/4 packets, 0% loss, TTL=128.

TTL of 128 confirmed traffic was switched at Layer 2 and did not pass through the router.

## What I Learned
- Cisco router interfaces are administratively down by default and require `no shutdown` to activate
- Devices on the same subnet can communicate through a Layer 2 switch without routing
- TTL=128 on ping results confirms traffic stayed within the same subnet and was not routed
- Consistent device naming and documentation keeps lab work organized and repeatable
