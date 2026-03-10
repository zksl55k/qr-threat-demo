# QR Threat Demo — Social Engineering Proof of Concept

A security awareness proof-of-concept demonstrating how malicious QR codes (**Qushing**) can be used as a social engineering attack vector.

### 🚀 **Live Demo**
[https://1lnkedin.netlify.app](https://1lnkedin.netlify.app)

> **Note:** Scan the QR code on my resume or click the link above to experience the full attack chain.

---

## What is Qushing?
**Qushing (QR code phishing)** is an attack technique where a malicious QR code redirects victims to phishing sites, malware downloads, or credential harvesters — instead of the legitimate destination they expected. Most users scan QR codes without verifying the destination URL.

## Attack Chain Demonstrated
* **Typosquatting** — Domain `1lnkedin.netlify.app` mimics `linkedin.com` to deceive victims.
* **YARA Rule Match** — Simulated detection of the scan event using a custom YARA rule.
* **Passive Device Fingerprinting** — Real browser metadata collected without any permissions (User Agent, timezone, screen resolution, language).
* **CTI Threat Report** — VirusTotal/Censys-style report generated with simulated IOCs, MITRE ATT&CK mapping, and risk scoring.
* **OOPS Reveal** — Security awareness message explaining the attack chain.

---

## Technical Details

| Component | Detail |
| :--- | :--- |
| **Language** | Vanilla HTML, CSS, JavaScript |
| **QR Library** | QRious v4.0.2 |
| **Deployment** | Netlify |
| **Data Collection** | Passive browser metadata only — no PII, no backend |
| **MITRE ATT&CK** | `T1566.002` — Spearphishing Link |
| **TTP** | `TA0001` — Initial Access |

---

## YARA Rule Used

> ### 🔍 Detection Logic
> ```yara
> rule SuspiciousQRScanner {
>   meta:
>     description = "Detects unsuspecting QR code scanners"
>     author      = "Amanda"
>     severity    = "HIGH"
>
>   strings:
>     $ua  = "Mozilla" nocase
>     $mob = "Mobile" nocase
>
>   condition:
>     $ua and ($mob or $qr)
> }
> ```

---

## Disclaimer
This is a **security awareness demo** — no real data is collected or stored. Built as a portfolio project to demonstrate threat intelligence concepts.

### **Author**
**Amanda** — [linkedin.com/in/amanda01010](https://linkedin.com/in/amanda01010)
