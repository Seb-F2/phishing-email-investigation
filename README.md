# Phishing Email Investigation & Threat Intelligence Analysis

A practical cybersecurity portfolio project investigating four historical phishing email incidents using a SOC-style investigation workflow.

## Project Overview

This project examines four phishing email samples and their corresponding network packet captures.

Rather than simply identifying the samples as phishing, each case was approached as an independent investigation. Evidence was collected and correlated across the email and network layers before reaching an analyst verdict.

The investigation included:

- Raw `.eml` email analysis
- Email header and routing analysis
- Sender impersonation identification
- Social-engineering analysis
- Suspicious URL and IOC extraction
- Threat-intelligence enrichment
- DNS analysis
- HTTP traffic analysis
- Credential-form inspection
- HTTP stream reconstruction
- Redirect analysis
- Base64 decoding
- Incident classification and response recommendations

## Tools Used

- **Kali Linux** – isolated investigation environment
- **Wireshark** – offline PCAP and network traffic analysis
- **VirusTotal** – threat-intelligence enrichment
- **Mousepad** – inspection of raw email and HTML content
- **SHA-256** – evidence hashing and file identification
- **Base64 utilities** – offline decoding of encoded HTTP parameters

## Investigation Workflow

Each phishing case followed a structured investigation process:

1. Preserve and hash the supplied evidence
2. Inspect the raw email
3. Analyse sender information and email headers
4. Identify social-engineering techniques
5. Extract and defang suspicious URLs
6. Enrich relevant indicators using threat intelligence
7. Analyse the corresponding PCAP in Wireshark
8. Correlate DNS and HTTP activity with email indicators
9. Investigate credential submissions and server responses
10. Reconstruct the attack workflow
11. Produce an evidence-based analyst verdict
12. Recommend appropriate incident-response actions

## Case Investigations

### Case 01 – Account Ownership Verification

A phishing email impersonated the recipient's email support service and requested account ownership confirmation.

Network analysis subsequently identified a credential submission containing the targeted email address and a synthetic password, followed by a fake authentication-error workflow.

**Classification:** True Positive – Credential Phishing / Credential Harvesting

### Case 02 – Failed Email Delivery

The recipient was told that three emails had failed to reach their mailbox and was instructed to verify their information.

PCAP analysis identified DNS and HTTP activity associated with the phishing destination and directly exposed login and password fields being submitted to the server.

**Classification:** True Positive – Credential Phishing / Credential Harvesting

### Case 03 – Email Registration Confirmation

The phishing message presented the recipient with **Confirm** and **Decline** options, despite both actions directing the user toward the same external destination.

Network analysis revealed a fake sign-in form and submission of password data to the phishing infrastructure.

**Classification:** True Positive – Credential Phishing / Credential Harvesting

### Case 04 – Email Re-Validation

The email impersonated the recipient's organisation and instructed the user to re-validate their account within 24 hours.

The corresponding PCAP demonstrated an email/password credential submission followed by a second fake WebMail login page requesting another password attempt.

**Classification:** True Positive – Credential Phishing / Credential Harvesting

## Key Learning

One of the most important lessons from this project was the difference between **evidence that suggests malicious activity and evidence that directly proves behaviour**.

For example:

- Infrastructure was not automatically classified as malicious simply because it appeared within a phishing email.
- VirusTotal results were used as supporting evidence rather than treated as definitive proof.
- Legitimate domains referenced within phishing workflows were distinguished from malicious indicators.
- Credential harvesting was only confirmed where network traffic demonstrated form submissions.
- Where a phishing page requested a second password but no second POST request existed in the capture, the investigation did not claim that a second credential submission occurred.

This evidence-led approach helped produce more defensible incident classifications.

## Skills Demonstrated

- Phishing email investigation
- SOC-style incident analysis
- Email header analysis
- IOC extraction and classification
- Threat intelligence
- Wireshark
- DNS analysis
- HTTP analysis
- Credential-harvesting identification
- HTTP stream reconstruction
- Social-engineering analysis
- Evidence hashing
- Base64 decoding
- Incident-response recommendations
- Technical report writing

## Safety

Potentially malicious URLs are defanged throughout the project.

Email samples and packet captures were analysed within an isolated Kali Linux environment. Potentially malicious websites were not intentionally visited or interacted with during the investigation.

## Full Investigation Report

A complete investigation report containing the methodology, evidence, screenshots, analyst verdicts and response recommendations will be available within this repository.

## Dataset Attribution

The historical phishing email and network-capture samples used in this project originate from the educational material provided by **Malware-Traffic-Analysis.net**.

The analysis, screenshots, interpretations and conclusions presented in this portfolio project were produced independently.

---

*This project was completed as part of my independent cybersecurity learning and portfolio development.*
