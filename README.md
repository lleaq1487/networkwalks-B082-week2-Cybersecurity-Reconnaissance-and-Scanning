# Cybersecurity Lab Environment

### WEEK 02 | FOOTPRINTING, SCANNING & REPORT WRITING

**Kali Linux · Zenmap · Footprinting · Network Reconnaissance · Security Reporting**

## Lab Purpose

This lab focuses on **controlled footprinting, reconnaissance, network scanning, and security report writing** using Kali Linux and authorized laboratory targets.

The environment is designed to provide practical experience with multiple reconnaissance tools, including Maltego and other Kali Linux utilities, followed by network discovery and scanning using Zenmap/Nmap. The final phase requires documenting the activities, observations, findings, and results in a structured cybersecurity assessment report.

All activities must be performed **only against authorized laboratory targets, systems owned by the learner, or targets explicitly provided for the training program.** No scanning or reconnaissance should be performed against unauthorized systems or networks.

## Week 02 Modules

**W2-PM1 — Footprinting with Multiple Kali Tools**
Perform controlled footprinting and reconnaissance using the designated Kali Linux tools, including the six tools provided through NetworkWalks Academy.

**W2-PM5 — Zenmap-Based Network Scanning**
Perform authorized network discovery and scanning using Zenmap/Nmap to identify available hosts, ports, services, and relevant network information.

**W2-PM-FINAL — Detailed Security Report**
Prepare a detailed report covering the selected Week 02 modules, tools used, methodology, observations, scan results, findings, screenshots, and conclusions.


## Assessment Scope & Rules of Engagement

This repository documents a **controlled reconnaissance and network-scanning assessment** performed within the authorized scope of the NetworkWalks cybersecurity training environment.

| Parameter            | Details                                              |
| -------------------- | ---------------------------------------------------- |
| **Assessment Type**  | Reconnaissance & Network Scanning                    |
| **Security Track**   | Offensive Security / Red Team                        |
| **Assessment Phase** | Footprinting · Reconnaissance · Network Enumeration  |
| **Platform**         | Kali Linux                                           |
| **Primary Target**   | `networkwalks.com`                                   |
| **Footprinting**     | WHOIS · WhatWeb · nslookup · WAFW00F · DnsRecon |
| **Network Scanning** | Nmap · Zenmap                                        |
| **Evidence**         | Screenshots · Terminal Output · Scan Results         |
| **Deliverable**      | Security Assessment Report                           |

### Scope Controls

* Testing was restricted to **authorized laboratory targets**.
* Reconnaissance and scanning were performed only within the defined assessment scope.
* No unauthorized systems or third-party infrastructure were intentionally targeted.
* No exploitation, credential attacks, brute-force activity, or denial-of-service testing were performed as part of this assessment.
* Tool output was validated before being treated as a security observation.
* Findings were documented using supporting technical evidence.

> **Out-of-scope assets were not tested. Discovery of an asset does not constitute authorization to interact with it.**

.
## Module 1 — Footprinting With Multiple Kali Tools

**Objective:** Collect information about the authorized target to understand its publicly visible domain, DNS, web, and security details.

**Task 1 —** Domain & DNS Reconnaissance
Used WHOIS, nslookup, and DNSRecon to gather domain information and identify DNS records and infrastructure.

**Task 2 —** Web Fingerprinting
Used WhatWeb to identify the technologies used by the target's website.

**Task 3 —** WAF Detection
Used WAFW00F to check whether a Web Application Firewall was present.

**Task 4 —** HTTP Analysis
Used cURL to inspect the website's HTTP/HTTPS response and headers.

**Key Takeaway:** These six tools provide different views of the target and together help build a clear picture of its external attack surface before network scanning.

## Command
## 1. WHOIS — Domain Information

### Command

```bash
whois networkwalks.com
```

<img width="1917" height="951" alt="Screenshot 2026-08-19 193554" src="https://github.com/user-attachments/assets/605303b6-cafe-4b86-8754-6893f94773d6" />

## 2. WhatWeb — Web Technology Fingerprinting

### Command

```bash
whatweb networkwalks.com
```

<img width="1919" height="681" alt="Screenshot 2026-08-19 193831" src="https://github.com/user-attachments/assets/5cdb8dc6-38a1-4ea5-8bfd-727437c413d6" />

## 3. nslookup — DNS Resolution

### Command

```bash
nslookup networkwalks.com
```

<img width="1919" height="635" alt="Screenshot 2026-08-19 194000" src="https://github.com/user-attachments/assets/23ebd26e-143c-4888-9cd7-e9083d55acd0" />

## 4. cURL — HTTP Response Analysis

### Command

```bash
curl -I https://networkwalks.com
```

<img width="1913" height="694" alt="Screenshot 2026-08-19 194138" src="https://github.com/user-attachments/assets/603714a1-3f56-4fce-9cb7-e385c17d6daa" />

## 5.WAFW00F — Web Application Firewall Detection

### Command

```bash
wafw00f networkwalks.com
```

<img width="1919" height="852" alt="Screenshot 2026-08-19 194301" src="https://github.com/user-attachments/assets/fb29b4e8-ca56-4113-81a9-fa3f2fcb2e03" />

## 6. DNSRecon — DNS Enumeration

### Command

```bash
dnsrecon -d networkwalks.com
```

<img width="1919" height="902" alt="Screenshot 2026-08-19 194421" src="https://github.com/user-attachments/assets/004538ea-d259-4f98-8603-a1b9f1f6de52" />

## PM1 Results Summary

| Tool | Purpose |
|---|---|
| WHOIS | Domain information |
| WhatWeb | Web technology fingerprinting |
| nslookup | DNS resolution |
| cURL | HTTP response analysis |
| DNSRecon  | WAF detection |
| DNSRecon | DNS enumeration |

The results from all six tools were reviewed and correlated to build an initial view of the target's external attack surface.

## PM1 Key Takeaway

The six reconnaissance tools provided complementary information about the authorized target. WHOIS, nslookup, and DNSRecon focused on domain and DNS infrastructure, while WhatWeb, cURL, and WAFW00F provided visibility into the web environment and its security controls.

Together, these results established the initial external attack-surface profile and provided the reconnaissance baseline for the next phase, **W2-PM5 — Zenmap-Based Network Scanning**.

## Module 5 — Network Scanning with Zenmap

**Objective:** Conduct controlled network reconnaissance within the authorized scope to identify reachable hosts, exposed network services, and the structure of the assessed network.

**Task 1 — Host Discovery**  
Performed an authorized Nmap/Zenmap discovery scan to identify active hosts and determine which systems were reachable within the assessment range.

**Task 2 — Port & Service Enumeration**  
Analyzed responsive hosts to identify accessible ports, protocols, and services, providing an initial view of the network's exposed service surface.

**Task 3 — Network Topology Analysis**  
Used Zenmap's **Topology** view to visualize relationships between discovered hosts and generate a graphical representation of the assessed network.

**Evidence:** Scan output, host details, screenshots, and the exported topology are maintained under `evidence/zenmap/` and referenced in the final assessment report.

**Key Takeaway:** Network scanning provides an active perspective of the authorized environment, complementing the passive intelligence collected during footprinting. The resulting host, port, service, and topology data establish the network-exposure baseline for subsequent security analysis.

## 1. Network Configuration & Scope

### Objective

Identify the local IP address and LAN subnet before performing network discovery. This establishes the scanning range for the authorized assessment.

### Command

```cmd
ipconfig
```



## 2. Live Host Discovery

### Objective

Identify active hosts within the authorized LAN subnet using Zenmap's Ping Scan.

### Scan Configuration

- **Target:** Local LAN subnet identified in Task 1
- **Profile:** Ping Scan
- **Nmap Scan:** Host discovery

### Command

```bash
nmap -sn 10.0.0.0/24
```


## 3. Live Host Count

### Objective

Determine the total number of active hosts identified during the Zenmap host-discovery scan.

### Result

The scan identified **4 live hosts**, including the assessment system.

### Evidence

The live-host count is confirmed in the Zenmap scan output and recorded as part of the assessment results.


## 4. Live Host IP Addresses

### Objective

Record the IPv4 addresses of the hosts identified as active during the Zenmap discovery scan.

### Results

The following hosts were identified as live:

| Host | IP Address |
|---|---|
| Host 1 | `10.0.0.1` |
| Host 2 | `10.0.0.4` |
| Host 3 | `10.0.0.19` |
| Host 4 | `10.0.0.5` |

### Evidence

The IP addresses were obtained from the Zenmap host-discovery results and recorded for the final assessment.


## 5. Live Host MAC Addresses

### Objective

Record the MAC addresses associated with the live hosts identified during the Zenmap discovery scan.

### Results

| Host | MAC Address |
|---|---|
| Host 1 | `00:50:56:E3:B3:2C` |
| Host 2 | `00:0C:29:C0:94:8F` |
| Host 3 | `00:50:56:E9:64:82` |
| Host 4 | `00-0C-29-40-C0-93` |

The fourth MAC address represents the local system and was obtained using the system's network configuration.

### Evidence

The MAC addresses were recorded from the Zenmap scan results and local network configuration.


## 6. Network Topology Mapping

### Objective

Visualize the discovered hosts and network relationships using Zenmap's **Topology** view and preserve the result as supporting assessment evidence.

### Procedure

1. Open the **Topology** tab in Zenmap.
2. Enable the topology legend.
3. Review the displayed network relationships.
4. Save the topology graphic.
5. Select **PDF** as the output format.
6. Store the exported topology with the assessment evidence.

### Output

**Topology File:** `evidence/zenmap/network-topology.pdf`

### Evidence

The exported topology PDF provides a graphical representation of the hosts discovered during the authorized network scan.


## W2-PM5 Results Summary

| Assessment Item | Result |
|---|---|
| Live Hosts Identified | **4** |
| Network Discovery | Completed |
| IP Addresses Recorded | **4** |
| MAC Addresses Recorded | **4** |
| Network Topology | Generated and exported to PDF |
| Scanning Tool | Zenmap / Nmap |
| Assessment Scope | Authorized local LAN |

### Key Takeaway

The Zenmap assessment successfully identified the active hosts within the authorized LAN and documented their IP and MAC addresses. The resulting topology diagram provides a visual representation of the discovered network and has been preserved as supporting evidence.

### Evidence

Zenmap scan output, host information, and the exported topology PDF are retained under:

```text
evidence/zenmap/
