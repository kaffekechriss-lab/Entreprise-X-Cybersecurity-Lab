# Entreprise X - Network Engineering & Cybersecurity Lab

## Project Overview
Entreprise X is a practical enterprise network engineering and cybersecurity laboratory built with GNS3, VirtualBox, Cisco IOS, pfSense, Kali Linux, Metasploitable 2 and Suricata.

The project demonstrates enterprise network design, routing, segmentation, security assessment, controlled exploitation, intrusion detection and network traffic analysis.

## Objectives
- Design and deploy a segmented enterprise network.
- Configure VLANs and OSPF routing.
- Deploy pfSense as a firewall and network gateway.
- Perform reconnaissance, service enumeration and vulnerability assessment.
- Conduct controlled exploitation in an isolated laboratory.
- Deploy Suricata for intrusion detection.
- Analyze network traffic using tcpdump and Wireshark.
- Document findings, risks and security recommendations.

## Laboratory Environment
| Component | Technology |
|---|---|
| Network simulation | GNS3 |
| Virtualization | VirtualBox |
| Routing | Cisco IOS / OSPF |
| Firewall | pfSense |
| Red Team | Kali Linux |
| Vulnerable target | Metasploitable 2 |
| Intrusion detection | Suricata |
| Network analysis | Nmap, tcpdump, Wireshark |

## Project Progress
- [x] Enterprise network architecture deployed.
- [x] VLAN segmentation and OSPF routing configured.
- [x] pfSense gateway and firewall environment configured.
- [x] Kali-to-Metasploitable connectivity established.
- [x] Red Team reconnaissance and service enumeration completed.
- [x] Vulnerability assessment completed.
- [x] Controlled exploitation of vsftpd and Samba completed; root access obtained in the isolated lab.
- [x] Suricata IDS configured and Nmap detection validated.
- [x] ICMP traffic captured and analyzed using tcpdump and Wireshark.
- [x] Security reports and technical evidence documented.
- [ ] Suricata IPS blocking validation.

## Repository Structure
- 01-Architecture/ - Network topology and IP addressing.
- 02-Network-Infrastructure/ - Routing, VLANs and firewall infrastructure.
- 03-Red-Team/ - Reconnaissance, enumeration, vulnerability analysis and exploitation.
- 04-Blue-Team/ - Firewall, Suricata and traffic analysis.
- 05-Security-Reports/ - Security assessment and packet capture.
- 06-Evidence/ - Evidence indexes for screenshots and test results.

## Security Assessment
The laboratory identified critical vulnerabilities in the intentionally vulnerable Metasploitable 2 target, including successful exploitation of vsftpd 2.3.4 and Samba 3.0.20.

Suricata IDS detection was validated using Nmap traffic. IPS blocking has not yet been tested.

## Security Disclaimer
All testing is conducted exclusively within an authorized, isolated virtual laboratory. No production systems are targeted.

## Project Status
**Blue Team IDS and traffic analysis completed. IPS validation remains pending.**
