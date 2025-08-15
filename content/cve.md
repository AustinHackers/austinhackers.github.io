---
title: CVE
aliases:
  - /gcve
  - /cve.html
  - /gcve.html
---

# AHA! is a Research CNA!

Austin Hackers Anonymous is a **research oriented** [CVE Numbering Authority], under the [MITRE] program root. This means a couple things.

For one, we now have a vulnerability disclosure policy (VDP) that covers vulns discovered in our own stuff and in other parties' assets.

Secondly, it means that we'll occasionally publish artisanal, bespoke CVE entries (CVEs) for these vulnerabilities. For more on AHA!'s CVE assignment scope, see our [CVE Numbering Authority] page on [MITRE]'s site.

Our VDP is derived from the [disclose.io](https://policymaker.disclose.io/policymaker/introduction) Policymaker, edited to cover vulnerability reports involving other parties.

## Vulnerability Disclosure Policy

AHA! welcomes feedback from security researchers and the general public to help improve our security and the security of the internet in general. Click the below to read more about that.

If you believe you have discovered a vulnerability, privacy issue, exposed data, or other security issues in any of our assets, we want to hear from you. This would include, but is not limited to, the AHA! website, AHA! e-mail services, and other AHA! communication channels.

If you believe you have discovered a security issue involving another party, we are happy to help you report that issue to the appropriate organization. Please see "Systems in Scope," below.

This policy outlines steps for reporting vulnerabilities to us, what we expect, what you can expect from us.

### Systems in Scope

This policy applies to any digital assets owned, operated, or maintained by AHA!

Because AHA! is a research organization, we will also accept vulnerability reports involving assets owned, operated, or maintained by another organization which **is not already** participating as a [CVE Numbering Authority].

### Out of Scope

- Assets or other equipment not owned by parties which **are already** participating as a [CVE Numbering Authority].

Vulnerabilities discovered or suspected in out-of-scope systems should be reported to the appropriate vendor or applicable authority.

### Our Commitments

When working with us, according to this policy, you can expect us to:

- Respond to your report promptly, and work with you to understand and validate your report;
- Strive to keep you informed about the progress of a vulnerability as it is processed;
- Work to remediate discovered vulnerabilities in a timely manner, within our operational constraints; and
- Extend Safe Harbor for your vulnerability research that is related to this policy.

### Our Expectations

In participating in our vulnerability disclosure program in good faith, we ask that you:

- Play by the rules, including following this policy and any other relevant agreements. If there is any inconsistency between this policy and any other applicable terms, the terms of this policy will prevail;
- Report any vulnerability you’ve discovered promptly;
- Avoid violating the privacy of others, disrupting our systems, destroying data, and/or harming user experience;
- Use only the Official Channels to discuss vulnerability information with us;
- Provide us a reasonable amount of time (at least 60 days from the initial report) to resolve the issue before you disclose it publicly;
- Perform testing only on in-scope systems, and respect systems and activities which are out-of-scope;
- If a vulnerability provides unintended access to data: Limit the amount of data you access to the minimum required for effectively demonstrating a Proof of Concept; and cease testing and submit a report immediately if you encounter any user data during testing, such as Personally Identifiable Information (PII), Personal Healthcare Information (PHI), credit card data, or proprietary information;
- You should only interact with test accounts you own or with explicit permission from the account holder; and
- Do not engage in extortion.

### Official Channels

Please report security issues affecting AHA! via [aha@takeonme.org](mailto:aha@takeonme.org), providing all relevant information. The more details you provide, the easier it will be for us to triage and fix the issue.

Please report security issues affecting other parties during one of our regularly scheduled meetings if you wish for AHA! to coordinate vulnerability disclosure (including generating a CVE ID) for you. We will not accept vulnerability reports involving other parties that are not presented at a AHA! meeting.

## Safe Harbor

When conducting vulnerability research, according to this policy, we consider this research conducted under this policy to be:

- Authorized concerning any applicable anti-hacking laws, and we will not initiate or support legal action against you for accidental, good-faith violations of this policy;
- Authorized concerning any relevant anti-circumvention laws, and we will not bring a claim against you for circumvention of technology controls;
- Exempt from restrictions in our Terms of Service (TOS) and/or Acceptable Usage Policy (AUP) that would interfere with conducting security research, and we waive those restrictions on a limited basis; and
- Lawful, helpful to the overall security of the Internet, and conducted in good faith.

You are expected, as always, to comply with all applicable laws. If legal action is initiated by a third party against you and you have complied with this policy, we will take steps to make it known that your actions were conducted in compliance with this policy.

If at any time you have concerns or are uncertain whether your security research is consistent with this policy, please submit a report through one of our Official Channels before going any further.

*Note that the Safe Harbor applies only to legal claims under the control of the organization participating in this policy, and that the policy does not bind independent third parties.*

# Generating AHA! CVEs

For issues involving other parties, please see additional requirements, below. Note, these requirements do not apply to AHA! assets.

* Present your findings at a regularly scheduled [meeting], under the usual public embargo terms (see our [rules](rules) for more details).
  - The most important rule is, "What happens at AHA! stays at AHA!"
* Ask a CVE point of contact for a CVE ID reservation.
  - Merely reserving a CVE ID number in no way alters the usual AHA! embargo on material presented at AHA!
* Agree to abide by the the above VDP terms and conditions for publishing.
  - Failing to adhere to the VDP may result in expulsion from AHA!

<br/>

## Published CVEs

When we publish CVEs, we will tend to use this [template], adjusted to taste.

<style>
.nowrap-cve td:first-child {
    white-space: nowrap;
}
</style>

<style>

.nowrap-gcve table {
    width: 125%;
    table-layout: fixed;
}

/* CVE */
.nowrap-gcve th:nth-child(1),td:nth-child(1) {
    width: 30%;
    white-space: nowrap;
}

/* Meeting */
.nowrap-gcve th:nth-child(2),td:nth-child(2) {
    width: 20%;
}

/* Issue Name */
.nowrap-gcve th:nth-child(3),td:nth-child(3) {
    width: 50%;
    white-space: normal;
    overflow-wrap: break-word;
}

/* GCVE - man this was a stupid prank. It overflows on purpose. */
.nowrap-gcve th:nth-child(4),td:nth-child(4) {
    width: 25%;
    white-space: nowrap;
}

/* Reserved Table */

.nowrap-gcve-reserved table {
    width: 100%;
    table-layout: fixed;
}

/* Meeting ID */
.nowrap-gcve-reserved th:first-child,td:first-child {
    width: 25%;
    white-space: nowrap;
}

/* GCVE ID */
.nowrap-gcve-reserved th:last-child,td:last-child {
    width: 75%;
    white-space: nowrap;
}

</style>

### 2023 Disclosures

<div class="nowrap-cve">

| CVE              | Meeting   | Issue                                      |
| ---------------- | --------- | ------------------------------------------ |
| [CVE-2023-0666]  | 0x00c7    | **Wireshark RTPS Parsing Buffer Overflow** |
| [CVE-2023-0667]  | 0x00c7    | **Wireshark MSMMS parsing buffer overflow** |
| [CVE-2023-0668]  | 0x00c7    | **Wireshark IEEE-C37.118 parsing buffer overflow** |
| [CVE-2023-2905]  | 0x00c8    | **Cesanta Mongoose MQTT Message Parsing Heap Overflow** |
| [CVE-2023-2906]  | 0x00c8    | **Wireshark CP2179 divide by zero** |
| [CVE-2023-4504]  | 0x00c9    | **CUPS/libppd PostScript Parsing Heap Overflow** |
| [CVE-2023-5841]  | 0x00cd    | **OpenEXR Heap Overflow in Scanline Deep Data Parsing** |

### 2024 Disclosures

| CVE              | Meeting   | Issue                                      |
| ---------------- | --------- | ------------------------------------------ |
| [CVE-2024-2053]  | 0x00d1    | **Artica Proxy Unauthenticated LFI Protection Bypass** |
| [CVE-2024-2054]  | 0x00d1    | **Artica Proxy Unauthenticated PHP Deserialization** |
| [CVE-2024-2055]  | 0x00d1    | **Artica Proxy Unauthenticated File Manage** |
| [CVE-2024-2056]  | 0x00d1    | **Artica Proxy Loopback Services Remotely Accessible Unauthenticated** |
| [CVE-2024-4224]  | 0x00d3    | **TP-Link TL-SG1016DE XSS** |

### 2025 Disclosures

| CVE              | Meeting   | Issue                                      |
| ---------------- | --------- | ------------------------------------------ |
| [CVE-2025-2894]  | 0x00de    | **Unitree Go1 Backdoor Control Channel** |
| [CVE-2025-3459]  | 0x00df    | **onsemi Quantenna transmit_file ArgInj** |
| [CVE-2025-3460]  | 0x00df    | **onsemi Quantenna set_tx_pow ArgInj** |
| [CVE-2025-3461]  | 0x00df    | **onsemi Quantenna Telent Missing Auth** |
| [CVE-2025-32455] | 0x00df    | **onsemi Quantenna router_command run_cmd ArgInj** |
| [CVE-2025-32456] | 0x00df    | **onsemi Quantenna router_command put_file_to_qtn ArgInj** |
| [CVE-2025-32457] | 0x00df    | **onsemi Quantenna router_command get_file_from_qtn ArgInj** |
| [CVE-2025-32458] | 0x00df    | **onsemi Quantenna router_command get_syslog_from_qtn ArgInj** |
| [CVE-2025-32459] | 0x00df    | **onsemi Quantenna router_command sync_time ArgInj** |
| [CVE-2025-35004] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MFIP ArgInj** |
| [CVE-2025-35005] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MFMAC ArgInj** |
| [CVE-2025-35006] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MFPORTFWD ArgInj** |
| [CVE-2025-35007] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MFRULE ArgInj** |
| [CVE-2025-35008] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MMNAME ArgInj** |
| [CVE-2025-35009] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MNNETSP ArgInj** |
| [CVE-2025-35010] | 0x00df    | **Microhard Bullet-LTE/IPn4Gii AT+MNPINGTM ArgInj** |

</div>
<div class="nowrap-gcve">

### 2025 Disclosures, Now With GCVE Identifiers

| CVE              | Meeting   | Issue                                               | GCVE |
| ---------------- | --------- | ------------------------------------------          | ---- |
| [CVE-2025-8452]  | 0x00e2    | **Brother Printer Default Admin Password Exposure** | [GCVE-1337-2025-00000000000000000000000000000000000000000000000001011111011111010111111001000000000000000000000000000000000000000000000000000000001] |

</div>

## Reserved GCVEs

We've reserved some number of CVEs, but it's all quite secretive and sneaky to avoid the dreaded [RBP Goblins](https://cve.mitre.org/cve/cna/RBP_Policy_v1-0.pdf). We'll publish when we publish.

That said, starting in August of 2025, we've started to reserve [GCVEs](https://gcve.eu/about) for upcoming disclosures. Apparently, there are no goblins in Luxembourg!

<div class="nowrap-gcve-reserved">

| Meeting | GCVE (Reserved) |
|---------|-----------------|
| 0xXXXX  | None yet!       | GCVE-1337-2025-00000000000000000000000000000000000000000000000001011111011111010111111001000000000000000000000000000000000000000000000000000000001       |

</div>


### Contact

Any questions about the AHA! CVE program should be directed to [cve@takeonme.org](mailto:cve@takeonme.org).

Vulnerabilities involving AHA! should be reported to [aha@takeonme.org](mailto:aha@takeonme.org).

Vulnerabilities involving other parties must be either (1) presented at a regular AHA! [meeting], (2) disclosed directly to the affected party, or (3) kept to yourself.


[CVE Numbering Authority]: https://www.cve.org/PartnerInformation/ListofPartners/partner/AHA
[MITRE]: https://www.cve.org/PartnerInformation/ListofPartners/partner/mitre
[meeting]: {{< baseurl >}}meetings
[meetings]: {{< baseurl >}}meetings
[template]: {{< baseurl >}}cves/cve-20xx-yyyy/
[CVE-2023-0666]: {{< baseurl >}}cves/cve-2023-0666/
[CVE-2023-0667]: {{< baseurl >}}cves/cve-2023-0667/
[CVE-2023-0668]: {{< baseurl >}}cves/cve-2023-0668/
[CVE-2023-2905]: {{< baseurl >}}cves/cve-2023-2905/
[CVE-2023-2906]: {{< baseurl >}}cves/cve-2023-2906/
[CVE-2023-4504]: {{< baseurl >}}cves/cve-2023-4504/
[CVE-2023-5841]: {{< baseurl >}}cves/cve-2023-5841/
[CVE-2024-2053]: https://korelogic.com/Resources/Advisories/KL-001-2024-001.txt
[CVE-2024-2054]: https://korelogic.com/Resources/Advisories/KL-001-2024-002.txt
[CVE-2024-2055]: https://korelogic.com/Resources/Advisories/KL-001-2024-003.txt
[CVE-2024-2056]: https://korelogic.com/Resources/Advisories/KL-001-2024-004.txt
[CVE-2024-4224]: {{< baseurl >}}cves/cve-2024-4224/
[CVE-2025-2894]: {{< baseurl >}}cves/cve-2025-2894/
[CVE-2025-3459]: {{< baseurl >}}cves/cve-2025-3459/
[CVE-2025-3460]: {{< baseurl >}}cves/cve-2025-3460/
[CVE-2025-3461]: {{< baseurl >}}cves/cve-2025-3461/
[CVE-2025-32455]: {{< baseurl >}}cves/cve-2025-32455/
[CVE-2025-32456]: {{< baseurl >}}cves/cve-2025-32456/
[CVE-2025-32457]: {{< baseurl >}}cves/cve-2025-32457/
[CVE-2025-32458]: {{< baseurl >}}cves/cve-2025-32458/
[CVE-2025-32459]: {{< baseurl >}}cves/cve-2025-32459/
[CVE-2025-35004]: {{< baseurl >}}cves/cve-2025-35004/
[CVE-2025-35005]: {{< baseurl >}}cves/cve-2025-35005/
[CVE-2025-35006]: {{< baseurl >}}cves/cve-2025-35006/
[CVE-2025-35007]: {{< baseurl >}}cves/cve-2025-35007/
[CVE-2025-35008]: {{< baseurl >}}cves/cve-2025-35008/
[CVE-2025-35009]: {{< baseurl >}}cves/cve-2025-35009/
[CVE-2025-35010]: {{< baseurl >}}cves/cve-2025-35010/
[CVE-2025-8452]: {{< baseurl >}}cves/cve-2025-8452/
[GCVE-1337-2025-00000000000000000000000000000000000000000000000001011111011111010111111001000000000000000000000000000000000000000000000000000000001]: {{< baseurl >}}gcves/GCVE-1337-2025-00000000000000000000000000000000000000000000000001011111011111010111111001000000000000000000000000000000000000000000000000000000001
