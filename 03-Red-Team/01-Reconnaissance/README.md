# Red Team – Network Reconnaissance

## 1. Objective

The objective of this phase is to identify active services and exposed ports on the Metasploitable 2 target machine.

All tests are performed in the authorized Entreprise X laboratory.

## 2. Target Information

| Parameter | Value |
|---|---|
| Target | Metasploitable 2 |
| IP address | 192.168.70.21 |
| Operating environment | Isolated laboratory |
| Testing machine | Kali Linux |
| Tool | Nmap |

## 3. Network Discovery and Port Scanning

The following command was used for a fast scan:

```bash
sudo nmap -n -Pn -F 192.168.70.21
```

Options:

- `-n`: disables DNS resolution.
- `-Pn`: skips host discovery and treats the target as online.
- `-F`: scans the 100 most common TCP ports.

## 4. Initial Results

The scan identified 18 open TCP ports and 82 closed TCP ports.

Some of the exposed services include:

| Port | Service | Purpose |
|---|---|---|
| 21 | FTP | File transfer |
| 22 | SSH | Secure remote access |
| 23 | Telnet | Remote terminal |
| 25 | SMTP | Email transfer |
| 53 | DNS | Name resolution |
| 80 | HTTP | Web service |
| 139 | NetBIOS | Network file sharing |
| 445 | SMB | File sharing |
| 3306 | MySQL | Database |
| 5432 | PostgreSQL | Database |
| 5900 | VNC | Remote desktop |
| 8009 | AJP13 | Apache Java connector |

Other open ports identified: 111, 2049, 2121, 513, 514 and 6000.

## 5. Service Version Detection

A second scan was performed to identify service versions on selected ports:

```bash
sudo nmap -n -Pn -sV --version-light -p 21,22,23,25,80,139,445,3306,5432,8180 192.168.70.21
```

Some identified versions:

- FTP: vsftpd 2.3.4
- SSH: OpenSSH 4.7p1
- HTTP: Apache 2.2.8
- SMB: Samba 3.x–4.x

## 6. Initial Security Observations

The target exposes several network services, including legacy remote-access and file-sharing protocols.

These services require further investigation to determine their versions, configurations and potential security weaknesses.

An open port alone does not prove that a vulnerability exists.

## 7. Next Steps

- Detailed FTP enumeration.
- SSH and Telnet service analysis.
- SMB enumeration.
- Web server analysis.
- Vulnerability assessment.
- Controlled exploitation in the isolated laboratory.

## 8. Status

**Status:** Initial reconnaissance completed.