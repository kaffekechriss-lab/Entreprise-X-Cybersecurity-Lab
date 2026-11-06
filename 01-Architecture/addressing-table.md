# Entreprise X â€” IP Addressing Plan

This document records verified IP addresses used in the laboratory.

| Device | Interface | IP address / Prefix | VLAN | Role | Status |
|---|---|---|---|---|---|
| R3 | FastEthernet0/0.70 | 192.168.70.1/24 | 70 | Default gateway | Verified |
| Metasploitable 2 | eth0 | 192.168.70.21/24 | 70 | Vulnerable test server | Verified |

## Notes

- VLAN 70 is reserved for the vulnerable lab server.
- Kali reaches the target through the pfSense and routed network.
- Add other interfaces and addresses only after verifying the actual device configurations.
