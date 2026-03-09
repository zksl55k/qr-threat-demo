# qr-threat-demo
QR Threat Demo — Social Engineering Proof of Concept
Show Image
Show Image
Show Image

A security awareness proof-of-concept demonstrating how malicious QR codes (Qushing) can be used as a social engineering attack vector.

Live Demo
https://1lnkedin.netlify.app
Scan the QR code on my resume or click the link above to experience the full attack chain.

What is Qushing?
Qushing (QR code phishing) is an attack technique where a malicious QR code redirects victims to phishing sites, malware downloads, or credential harvesters — instead of the legitimate destination they expected. Most users scan QR codes without verifying the destination URL.

Attack Chain Demonstrated

Typosquatting — Domain 1lnkedin.netlify.app mimics linkedin.com to deceive victims
YARA Rule Match — Simulated detection of the scan event using a custom YARA rule
Passive Device Fingerprinting — Real browser metadata collected without any permissions (User Agent, timezone, screen resolution, language)
CTI Threat Report — VirusTotal/Censys-style report generated with simulated IOCs, MITRE ATT&CK mapping, and risk scoring
OOPS Reveal — Security awareness message explaining the attack chain


Technical Details
ComponentDetailLanguageVanilla HTML, CSS, JavaScriptQR LibraryQRious v4.0.2DeploymentNetlifyData CollectionPassive browser metadata only — no PII, no backendMITRE ATT&CKT1566.002 — Spearphishing LinkTTPTA0001 — Initial Access

YARA Rule Used
yararule SuspiciousQRScanner {
  meta:
    description = "Detects unsuspecting QR code scanners"
    author      = "Amanda"
    severity    = "HIGH"
  strings:
    $ua  = "Mozilla" nocase
    $mob = "Mobile" nocase
  condition:
    $ua and ($mob or $qr)
}

Disclaimer
This is a security awareness demo — no real data is collected or stored. Built as a portfolio project to demonstrate threat intelligence concepts for a Threat Collections Engineer role at Anthropic.

Author
Amanda — linkedin.com/in/amanda01010 
