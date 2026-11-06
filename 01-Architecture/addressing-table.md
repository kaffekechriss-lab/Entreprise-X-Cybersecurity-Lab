# Entreprise X – IP Addressing Table

## 1. Network Devices

| Device | Interface | IP Address | Network / VLAN | Role |
|---|---|---|---|---|
| Kali Linux | eth1 | 192.168.2.3/24 | Red Team Network | Security testing |
| pfSense | OPT1 | 192.168.2.254/24 | Red Team Network | Firewall / Gateway |
| R3 | FastEthernet0/0.70 | 192.168.70.1/24 | VLAN 70 | Default Gateway |
| Metasploitable 2 | eth0 | 192.168.70.21/24 | VLAN 70 | Vulnerable target |

## 2. Routing Information

| Source | Destination Network | Next Hop |
|---|---|---|
| Kali Linux | 192.168.70.0/24 | 192.168.2.254 |
| pfSense | 192.168.70.0/24 | 10.10.0.2 |

## 3. VLAN Information

| VLAN ID | Name | Network | Purpose |
|---|---|---|---|
| 70 | Vulnerable-Lab | 192.168.70.0/24 | Isolated vulnerable machines |

## 4. Network Path

Kali Linux → pfSense → R1 → R2 → R3 → Switch3 → Metasploitable 2

**Note:** This table documents the currently verified addressing information. Additional interfaces and networks will be documented as the project progresses.