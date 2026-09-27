# Cisco Packet Tracer Lab — OSPF & BGP Multi-AS Network

A Packet Tracer lab with two Autonomous Systems, **AS 100** and **AS 200**, each running **OSPF** internally and connected to each other over **BGP**.


## Topology

**AS 100**
- `Switch0` (2960-24TT) with two VLANs
  - VLAN 1: `PC2`, `Printer0`, `PC3`, `Server0` (DHCP server)
  - VLAN 2: `PC0`, `PC1`
- `Router0`, `Router1`, `Router2`, `Router3` — 2911 routers running OSPF, with two redundant paths between `Router0` and `Router3`
- `Router4` — AS border router, peers with AS 200 over BGP

**AS 200**
- `Router4(1)` — AS border router, peers with AS 100 over BGP
- `Router4(2)` — internal router, also runs DHCP for this AS
- `Switch1` (2960-24TT) connecting `PC4`, `PC5`, `PC6`, `PC7`
- OSPF between `Router4(1)` and `Router4(2)`

**Inter-AS link**
- eBGP peering between `Router4` (AS 100) and `Router4(1)` (AS 200)

## Devices

| Device | Role |
|---|---|
| Switch0, Switch1 | 2960-24TT access switches |
| Router0–Router3 | OSPF routers, AS 100 |
| Router4 | AS 100 border router (BGP) |
| Router4(1) | AS 200 border router (BGP) |
| Router4(2) | AS 200 internal router / DHCP |
| Server0 | DHCP server, AS 100 |
| PC0–PC3, Printer0 | End devices, AS 100 |
| PC4–PC7 | End devices, AS 200 |

## Protocols

- OSPF — intra-AS routing in AS 100 and AS 200
- BGP — inter-AS routing between AS 100 and AS 200
- VLANs — Layer 2 segmentation on Switch0
- DHCP — dynamic addressing in both ASes
- ICMP — end-to-end connectivity verification

