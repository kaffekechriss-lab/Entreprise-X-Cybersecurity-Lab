# VLAN 70 – Vulnerable Lab Network

## 1. Objective

VLAN 70 is used to isolate the vulnerable laboratory network containing the Metasploitable 2 machine.

The objective is to separate this environment from other network segments and control communication through the routing infrastructure and pfSense firewall.

## 2. Network Information

| Parameter | Value |
|---|---|
| VLAN ID | 70 |
| VLAN Name | Vulnerable-Lab |
| Network | 192.168.70.0/24 |
| Default Gateway | 192.168.70.1 |
| Router | R3 |
| Switch | Switch3 |
| Target Machine | Metasploitable 2 |
| Target IP | 192.168.70.21 |

## 3. VLAN Architecture

- Switch3 provides Layer 2 connectivity.
- The port connected to Metasploitable 2 is configured as an access port in VLAN 70.
- The uplink between Switch3 and R3 operates as an IEEE 802.1Q trunk.
- R3 uses a subinterface to provide Layer 3 connectivity to VLAN 70.

## 4. Router Configuration

The R3 subinterface is:

- Interface: FastEthernet0/0.70
- Encapsulation: dot1Q
- VLAN: 70
- IP address: 192.168.70.1/24

## 5. Connectivity Verification

The following tests were performed:

- Kali Linux can reach the target network through pfSense.
- Metasploitable 2 is reachable at 192.168.70.21.
- The target uses 192.168.70.1 as its default gateway.

## 6. Security Purpose

VLAN segmentation helps isolate vulnerable systems from other network segments.

Additional firewall policies and monitoring controls are required to enforce security between these networks.

## 7. Status

**Status:** Implemented and connectivity verified.