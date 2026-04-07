[NI-01-lan-deployment.md](https://github.com/user-attachments/files/26523788/NI-01-lan-deployment.md)
# NI-01 — Small Business LAN Deployment

> **Deployed a functional small business LAN using Cisco IOS CLI, validated end-to-end connectivity, and confirmed Layer 2 switching behavior through TTL analysis.**

**Skills demonstrated:** Cisco IOS CLI · IP addressing · Layer 2 switching · Network documentation · Connectivity validation
**Tools:** Cisco Packet Tracer 9.0 · Cisco ISR4321 Router · Cisco 2960-24TT Switch
**Date:** 2026-03

---

## What I Did

Built a small business LAN from scratch in Packet Tracer using a Cisco router and switch. Assigned a /24 address scheme, configured the router interface via CLI, and connected three workstations through the switch. Validated connectivity using ping and analyzed TTL values to confirm switching behavior.

```
Main_Router (192.168.1.1)
      |
Main_Switch
   |     |     |
WS1   WS2   WS3
.10   .11   .12
```

**IP Addressing:**

| Device | Interface | IP Address | Gateway |
|--------|-----------|------------|---------|
| Main_Router | G0/0/0 | 192.168.1.1 | — |
| Workstation1 | NIC | 192.168.1.10 | 192.168.1.1 |
| Workstation2 | NIC | 192.168.1.11 | 192.168.1.1 |
| Workstation3 | NIC | 192.168.1.12 | 192.168.1.1 |

**Router configuration:**

```cisco
enable
configure terminal
interface GigabitEthernet0/0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
end
```

---

## What I Found

All three workstations pinged successfully — 4/4 packets, 0% loss across all pairs.

TTL returned as **128** on all pings, confirming traffic was switched at Layer 2 and never touched the router. Devices on the same subnet communicate through the switch directly the router is present but uninvolved in intra-subnet traffic.

---

## What I Learned

Cisco router interfaces are **administratively down by default** — `no shutdown` is required before the interface will pass traffic. That's a simple thing that could cause a real headache.

TTL values are useful. A TTL of 128 tells you traffic stayed at Layer 2. Ping output becomes evidence of how traffic actually moved through the network. Useful when you're troubleshooting or investigating.

---

*Next: [NI-02 — VLAN Segmentation](NI-02-vlan-segmentation.md) extends this topology with traffic isolation and inter-VLAN routing.*
