# FTP Monitoring – Entreprise X

## 1. Objective
Monitor FTP activity between Kali Linux and Metasploitable 2 using Suricata.

## 2. Lab Configuration
- Monitoring tool: Suricata on pfSense
- Interface: OPT1 (em1)
- Source: Kali Linux – `192.168.2.3`
- Destination: Metasploitable 2 – `192.168.70.21`
- FTP port: TCP/21

## 3. Service Enumeration

Command:

```bash
nmap -sV -p 21 192.168.70.21
```

Result:
- Port: 21/tcp open
- Service: FTP
- Version: vsftpd 2.3.4

## 4. FTP Authentication Test

A connection was initiated from Kali Linux:

```bash
ftp 192.168.70.21
```

Result: Authentication successful.

## 5. Suricata Analysis

No FTP-specific alert was observed after the connection test.

The alerts displayed during this test concerned UDP invalid checksums on DNS traffic between pfSense and external DNS servers.

This does not prove that FTP traffic was not inspected. It indicates that no matching FTP alert was generated during this test.

## 6. Security Findings

- The server uses an outdated FTP implementation.
- FTP does not encrypt authentication credentials.
- Successful authentication demonstrates that the provided credentials were accepted.
- Monitoring did not generate a specific FTP alert during this test.

## 7. Conclusion

The FTP connectivity and authentication test was successful. Suricata did not generate a specific FTP alert for this normal login activity. Further monitoring and detection-rule validation are required.