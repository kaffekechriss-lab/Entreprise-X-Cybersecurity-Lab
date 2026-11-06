# OSPF – Dynamic Routing

## 1. Objective

OSPF (Open Shortest Path First) is a dynamic routing protocol used to exchange routing information between routers.

In the Entreprise X laboratory, OSPF allows R1, R2 and R3 to exchange routes between different network segments.

## 2. OSPF Implementation

| Parameter | Value |
|---|---|
| Routing protocol | OSPF |
| OSPF version | OSPFv2 (IPv4) |
| Area | 0 (Backbone Area) |
| Routers | R1, R2 and R3 |
| Advertised network | 192.168.70.0/24 |

## 3. Network Advertisement

The network 192.168.70.0/24 is advertised through OSPF in Area 0.

This allows the other participating routers to learn the route dynamically.

## 4. VLAN 70 Integration

R3 provides Layer 3 connectivity to VLAN 70 through:

- Interface: FastEthernet0/0.70
- Encapsulation: IEEE 802.1Q
- VLAN ID: 70
- IP address: 192.168.70.1/24

## 5. Verification Commands

The following Cisco IOS commands can be used to verify OSPF:

```cisco
show ip ospf neighbor
show ip ospf
show ip route ospf
show ip protocols
show ip interface brief
```

## 6. Expected Results

- OSPF neighbors should reach the FULL state where adjacencies are expected.
- The OSPF routing table should contain learned routes.
- The network 192.168.70.0/24 should be advertised in Area 0.

## 7. Benefits

- Dynamic route exchange.
- Faster adaptation to topology changes.
- Scalability for enterprise networks.
- Reduced need for manually configured static routes.

## 8. Status

**Status:** OSPF configured in the laboratory. Further verification evidence will be documented as the project progresses.