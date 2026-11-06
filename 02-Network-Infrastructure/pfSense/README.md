# pfSense – Firewall and Routing

## 1. Objective

pfSense is deployed as a firewall and routing component in the Entreprise X laboratory.

It provides network connectivity between the Red Team network and the internal enterprise infrastructure.

## 2. Network Information

| Parameter | Value |
|---|---|
| Firewall | pfSense |
| OPT1 interface | 192.168.2.254/24 |
| Connected network | 192.168.2.0/24 |
| Static route destination | 192.168.70.0/24 |
| Static route gateway | 10.10.0.2 |

## 3. Routing Configuration

A static route is configured on pfSense:

- Destination: 192.168.70.0/24
- Next hop: 10.10.0.2

This route allows pfSense to forward traffic toward the VLAN 70 network through R1.

## 4. Network Communication

The communication path between Kali Linux and Metasploitable 2 is:

Kali Linux → pfSense → R1 → R2 → R3 → Switch3 → Metasploitable 2

## 5. Security Role

pfSense provides firewall capabilities to:

- Control incoming and outgoing traffic.
- Filter network communications.
- Restrict access between network segments.
- Monitor firewall events and traffic.

## 6. Verification

Connectivity was verified between Kali Linux and Metasploitable 2.

Additional firewall rule testing and logging evidence will be documented in the Blue Team section.

## 7. Status

**Status:** Routing configured and connectivity verified.