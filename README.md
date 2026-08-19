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

Assessment Results & Analysis
        ↓
Cross-Phase Correlation
        ↓
Security Observations
        ↓
Recommendations
        ↓
Assessment Limitations
        ↓
Conclusion
        ↓
Evidence Register

## Assessment Results & Analysis

The Week 02 assessment combined two complementary activities: **W2-PM1 — Footprinting** and **W2-PM5 — Network Scanning**. Together, these activities established an evidence-based view of the authorized target's external footprint and the reachable systems within the assessed local network.

### W2-PM1 — External Footprinting

The footprinting phase used six Kali Linux utilities across multiple reconnaissance layers:

| Reconnaissance Layer | Tool | Assessment Focus |
|---|---|---|
| Domain Intelligence | **WHOIS** | Publicly available domain information |
| DNS Resolution | **nslookup** | Domain-to-address resolution |
| DNS Enumeration | **DNSRecon** | Publicly observable DNS records |
| Web Fingerprinting | **WhatWeb** | Detectable web technologies |
| HTTP Analysis | **cURL** | HTTP response and header information |
| Security-Control Detection | **WAFW00F** | Detectable Web Application Firewall |

The individual results were reviewed and correlated to establish an initial **external attack-surface profile** of the authorized target.

### W2-PM5 — Network Scanning

The network-scanning phase used **Zenmap/Nmap** to perform authorized host discovery within the assessed local network.

| Assessment Metric | Result |
|---|---:|
| Live Hosts Identified | **4** |
| IP Addresses Recorded | **4** |
| MAC Addresses Recorded | **4** |
| Network Topology | **Generated and exported** |
| Discovery Method | **Nmap Ping Scan** |

The discovered host information and topology output were preserved as supporting assessment evidence.

### Cross-Phase Correlation

```text
                    AUTHORIZED SCOPE
                           │
                           ▼
                  W2-PM1 FOOTPRINTING
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
       DOMAIN             DNS              WEB
      INTELLIGENCE      ANALYSIS         ANALYSIS
          │                │                │
          └────────────────┼────────────────┘
                           ▼
                  EXTERNAL FOOTPRINT
                           │
                           ▼
                  W2-PM5 SCANNING
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
      LIVE HOSTS         IP/MAC          TOPOLOGY
                           │
                           ▼
                   NETWORK EXPOSURE
```

## Evidence

All screenshots, terminal outputs, scan results, and topology files from the Week 02 assessment are organized by module.

### W2-PM1 — Footprinting

```text
evidence/footprinting/
├── whois/
├── whatweb/
├── nslookup/
├── curl/
├── wafw00f/
└── dnsrecon/
```
```text
evidence/zenmap/
├── scan-output/
├── host-details/
└── network-topology
```
## Security Observations

The assessment identified the following security-relevant observations within the authorized scope:

1. **Domain Information Exposure**  
   Publicly available domain information was identified through WHOIS reconnaissance, contributing to the target's external information footprint.

2. **DNS Information Exposure**  
   DNS reconnaissance provided visibility into publicly observable DNS records and associated infrastructure.

3. **Web Technology Exposure**  
   Web fingerprinting identified technologies externally detectable from the target application, providing insight into its technology stack.

4. **HTTP Information Exposure**  
   HTTP response analysis provided additional visibility into the target's web environment through observable response information and headers.

5. **Web Security Control Detection**  
   WAF reconnaissance identified an externally detectable Web Application Firewall, providing insight into the target's defensive architecture.

6. **Active Host Discovery**  
   Network scanning identified **four live hosts** within the authorized LAN, establishing the active-host baseline for the assessed network segment.

7. **Network Identifier Visibility**  
   IP and MAC addresses were recorded for the discovered hosts, allowing the identified systems to be documented.

8. **Network Topology Visibility**  
   Zenmap generated a topology representation of the discovered environment, providing a graphical view of the observed network relationships.

### Assessment Note

These observations represent **reconnaissance and network-visibility results**, not confirmed security vulnerabilities. Additional testing and validation would be required to determine exploitability, impact, and severity.

## Recommendations

Based on the observations identified during the assessment, the following security measures are recommended:

1. **Review Domain and DNS Exposure**  
   Periodically review publicly available domain and DNS information and remove unnecessary records or exposure where operationally appropriate.

2. **Maintain Web Technologies**  
   Keep externally exposed web technologies, frameworks, plugins, and supporting components properly maintained and updated.

3. **Review HTTP Configuration**  
   Periodically review web-server configuration and HTTP security headers to reduce unnecessary information disclosure and strengthen the web security posture.

4. **Maintain WAF Controls**  
   Regularly review WAF configuration, coverage, logging, monitoring, and rule effectiveness to ensure that the security control remains appropriately configured.

5. **Maintain Asset Inventory**  
   Keep an accurate inventory of systems connected to the internal network and periodically verify whether each system requires network access.

6. **Strengthen Network Segmentation**  
   Apply appropriate segmentation and access-control policies to limit unnecessary communication between internal systems.

7. **Perform Periodic Attack-Surface Reviews**  
   Conduct authorized reconnaissance and network-discovery assessments periodically to identify changes in exposed assets, technologies, and network infrastructure.

### Recommendation Priority

| Priority | Security Area |
|---|---|
| **High** | Review externally exposed assets and security controls |
| **Medium** | Review DNS, web-server, and HTTP configuration |
| **Medium** | Maintain internal asset inventory and network segmentation |
| **Low** | Conduct periodic attack-surface reviews |

## Assessment Limitations

This assessment was conducted as a controlled cybersecurity laboratory exercise within the defined authorization and assessment scope.

**The assessment was limited to:**

- External footprinting and reconnaissance
- Domain and DNS enumeration
- Web technology identification
- HTTP response analysis
- WAF detection
- Authorized host discovery
- IP and MAC address identification
- Network topology mapping

The assessment did **not** include exploitation, credential attacks, brute-force testing, denial-of-service activity, or comprehensive vulnerability validation.

Therefore, the results represent an **initial reconnaissance and network-exposure assessment** and should not be interpreted as a complete penetration test or vulnerability assessment.

The findings reflect the environment observed during the assessment period and may change as the target or network configuration changes.

## Conclusion

The Week 02 assessment successfully completed the defined **footprinting and network-scanning objectives** within the authorized scope.

**W2-PM1** established an external reconnaissance baseline by collecting domain, DNS, web-technology, HTTP, and security-control information using six Kali Linux tools.

**W2-PM5** provided an active view of the authorized LAN through Zenmap/Nmap, identifying **four live hosts**, recording their IP and MAC addresses, and documenting the observed network topology.

**The assessment followed a structured reconnaissance workflow:**

```text
Scope Definition
        ↓
External Footprinting
        ↓
Information Correlation
        ↓
Network Discovery
        ↓
Host Identification
        ↓
Topology Analysis
        ↓
Evidence Collection
        ↓
Security Reporting
```

## Key Outcomes

The Week 02 assessment successfully completed the core **footprinting and network-scanning activities** within the authorized cybersecurity laboratory environment.

- External footprinting performed using six Kali Linux reconnaissance tools
- Domain and DNS information collected and analyzed
- Web technologies identified through fingerprinting
- HTTP response information examined
- Web Application Firewall detection performed
- DNS records enumerated
- Local network scanned using Zenmap/Nmap
- **4 live hosts** identified within the assessed LAN
- IP and MAC addresses recorded
- Network topology generated and exported for evidence
- Assessment results documented for further security analysis

## Security & Responsible Use

This laboratory is intended for authorized cybersecurity education, reconnaissance, and security testing.

All footprinting and network-scanning activities must remain within systems, networks, and applications that are owned or explicitly authorized for testing.

No unauthorized access, exploitation, brute-force activity, or disruptive testing was performed as part of this assessment.

## Mentor

**Waqas Karim (CCIE)**

Technical guidance and mentorship provided throughout the cybersecurity internship.

## Phase 02 — Completion

**Status:** `COMPLETED`

Week 02 successfully demonstrated the transition from **external reconnaissance to active network discovery**. The target's external footprint was assessed using multiple Kali Linux tools, while Zenmap/Nmap was used to identify live systems and document the authorized network topology.

| Module | Focus | Status |
|---|---|---|
| **W2-PM1** | Footprinting & External Reconnaissance | **Completed** |
| **W2-PM5** | Network Scanning & Topology Mapping | **Completed** |
| **W2-PM-FINAL** | Assessment Documentation & Reporting | **Completed** |

**Environment:** Kali Linux · WHOIS · WhatWeb · nslookup · cURL · DNSRecon · WAFW00F · Zenmap/Nmap

**Next:** Continue with subsequent authorized cybersecurity assessment exercises.

**Week 02 — Footprinting, Network Scanning & Security Assessment: Completed**
