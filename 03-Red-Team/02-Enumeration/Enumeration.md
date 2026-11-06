# HTTP Enumeration – Metasploitable 2

## 1. Objective

The objective of this assessment is to enumerate the HTTP service running on Metasploitable 2 and identify exposed web technologies, directories, applications and potential information disclosure.

## 2. Target Information

| Parameter | Value |
|---|---|
| Target | Metasploitable 2 |
| IP Address | 192.168.70.21 |
| Protocol | HTTP |
| Port | 80 |
| Web Server | Apache 2.2.8 |
| Testing Machine | Kali Linux |

## 3. Technologies Detected

Tools used:
- WhatWeb
- cURL
- Gobuster

Detection results:

| Technology | Version / Information |
|---|---|
| Apache | 2.2.8 |
| Additional technologies | To be completed from WhatWeb results |
| HTTP headers | To be completed from cURL results |

## 4. Directory Enumeration

Tool: Gobuster

Command:

```bash
gobuster dir -u http://192.168.70.21/ \
-w /usr/share/wordlists/dirb/common.txt \
-t 20
```

Discovered directories and files:

| Path | HTTP Status | Observation |
|---|---|---|
| To be completed | To be completed | To be completed |

## 5. Accessible Web Applications

Applications and pages discovered:

- To be completed using actual browser observations.

## 6. Information Disclosure

The HTTP service was examined to identify potentially exposed information, including:

- Web server version.
- Technology information.
- Accessible directories and files.
- Potentially sensitive information.

Findings:

To be completed based on actual test results.

## 7. Security Observations

An exposed web directory or a disclosed software version may increase the attack surface.

However, an accessible resource or a server banner alone does not prove the existence of a vulnerability.

## 8. Recommendations

- Keep the web server and applications updated.
- Disable directory listing where unnecessary.
- Restrict access to sensitive files.
- Remove unnecessary applications and test resources.
- Avoid exposing detailed server version information.
- Review HTTP response headers and security configurations.

## 9. Conclusion

HTTP enumeration provided an initial overview of the web services exposed by Metasploitable 2.

Further vulnerability assessment is required to determine whether the identified services and resources present exploitable weaknesses.

**Assessment status:** HTTP enumeration completed.