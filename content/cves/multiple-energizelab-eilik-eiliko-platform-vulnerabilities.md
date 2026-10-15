---
title: Multiple EnergizeLab Eilik / Eiliko Platform Vulnerabilities
aliases:
  - /cves/CVE-2026-105032.html
  - /cves/CVE-2026-105032
  - /cves/CVE-2026-105033.html
  - /cves/CVE-2026-105033
  - /cves/CVE-2026-105034.html
  - /cves/CVE-2026-105034
  - /cves/CVE-2026-105035.html
  - /cves/CVE-2026-105035
  - /cves/CVE-2026-105036.html
  - /cves/CVE-2026-105036
  - /cves/CVE-2026-105037.html
  - /cves/CVE-2026-105037
  - /cves/CVE-2026-105038.html
  - /cves/CVE-2026-105038
  - /cves/CVE-2026-105039.html
  - /cves/CVE-2026-105039
  - /cves/CVE-2026-105040.html
  - /cves/CVE-2026-105040
  - /gcves/GCVE-1337-2026-00000000000000000000000000000000000000000000000001011111111110011111111110000000000000000000000000000000000000000000000000000001100
  - /gcves/GCVE-1337-2026-00000000000000000000000000000000000000000000000001110111111110111111111111000000000000000000000000000000000000000000000000000001101
  - /gcves/GCVE-1337-2026-00000000000000000001111111111100000000000000000000000011111111001111111111000000000000000000010110111111111100000000000000000001110
  - /gcves/GCVE-1337-2026-00000000000000000001111111111100000000000000000000000011111111100111111111000000000000000000011111111111111100000000000000000001111
  - /gcves/GCVE-1337-2026-00000000000000000000111111111100000000000000000000000011111100001111111101000000000000000000011111111111111100000000000000000010000
  - /gcves/GCVE-1337-2026-00000000000000110111111111111111110000000000000000000011111100011111111110000000000000000000011111111111111000000000000000000010001
  - /gcves/GCVE-1337-2026-00000000000000111001111111111111111000000000000000000011111100100111111110000000000000000000011111111111111100000000000000000010010
  - /gcves/GCVE-1337-2026-00000000000000111111111111111111111000000000000000000011111100111111111111000000000000000000011111111111111101010000000000000010011
  - /gcves/GCVE-1337-2026-00000000000000011111111111111111111000000000000000000011111101001111111110000000000000000000011111111111111111111000000000000010100
 
publishDate: 2026-10-15T06:00:00-05:00

---
# EnergizeLab Eilik / EilikO Platform — Multiple Vulnerabilities

**Vendor:** EnergizeLab (Shenzhen Zhuneng Technology Co., Ltd.)  
**Products:** Eilik and EilikO robots, AI Station, mobile and desktop apps, and supporting cloud services  
**Research period:** June–September 2026  
**Status note:** The status below reflects the source report and its September 2026 retests; it is not a fresh assessment.

This research conducted by [Sammy Azdoufal](https://github.com/xn0tsa) and reported to AHA! for CVE coordination, identifies flaws across cloud authentication and authorization, AI configuration and memory, firmware update and device trust, and legacy telemetry. Several issues are independently exploitable; together, the weaknesses can bridge account access, cloud secrets, fleet-level AI and firmware control, and compromise of individual robots. The reviewed builds include `station-middleware` Docker images 1.6.5–1.8.2, robot firmware `v2.1_20260617182218_release`, AI Station firmware, Android app 3.0.0, and Windows desktop app 3.1.2. The research measured several thousand active devices and accounts in September 2026. 

## Attacker Value

The practical risk is not limited to reading data or taking over a single account:

- **Independent compromise paths:** An unauthenticated attacker could execute commands through legacy telemetry (FINDING-1), tamper with AI skill files (CVE-2026-105032), take over accounts through weak OTP controls (FINDING-2) or user-ID mass assignment (CVE-2026-105040), and obtain access to users’ personal information and robot associations (FINDING-8, FINDING-3). Default AI Station root credentials (CVE-2026-105033) and the shared updater key / unsigned update paths (CVE-2026-105035, CVE-2026-105036) create separate routes to persistent device compromise, including from a nearby network or someone with local device access.
- **Cloud-to-fleet escalation:** A registered low-privilege account can exploit the middleware file-read flaw (CVE-2026-105037) to obtain server secrets. Separately, missing admin role checks (CVE-2026-105039) expose AI provider keys and permit configuration and object-store changes. Paired with unsigned firmware updates (CVE-2026-105036), an attacker could turn cloud-side write access into firmware distribution and persistent code execution on devices. These chained consequences are not included in the individual CVSS scores.
- **Abuse of trust in a child-facing product:** Unauthenticated model switching (CVE-2026-105038), cross-user memory access (FINDING-4), and persistent profile poisoning (FINDING-6) could redirect conversations, expose or alter a child’s robot profile, or make the robot repeatedly act on attacker-supplied instructions. FINDING-5 could put unmoderated robot programs into public circulation; the assessed packages contain executable servo choreography and audio.
- **Incentives and reach:** Account takeover, private data, audio/images, cloud API credentials, and reusable device access provide paths to fraud, surveillance, extortion, service disruption, or resale of access. The broad account/device enumeration and shared trust mechanisms make automation and repeated targeting more attractive than a one-off attack.

# Technical Details

For exhaustive technical detail and proofs-of-concept, see Sammy's GitHub repo at https://github.com/xn0tsa/your-secrets-are-safe-with-me.

## Affected components

The table below outlines the individual components of the affected EnergizeLab ecosystem and which issues implicate them. Unversioned hosted services and artifacts are identified as such rather than assigned inferred versions.

| Component | Version | Associated issues |
|---|---|---|
| FastAPI AI inference and profiling services | Sept 2026 build fingerprint; no public version | CVE-2026-105032, CVE-2026-105038, FINDING-6, Tier-2 #27 |
| NestJS station-middleware cloud service | Docker image tags 1.6.5–1.8.2 | CVE-2026-105037, CVE-2026-105039, FINDING-3, FINDING-5 |
| NestJS auth service | 1.8.2-era deployment | CVE-2026-105034, CVE-2026-105040, FINDING-2, FINDING-4, FINDING-7, FINDING-8, Tier-2 #19 |
| Legacy PHP telemetry wrappers (panxer.php, maticontroller.php, update.php) | 2023-era; no version stated | FINDING-1, Tier-2 #18 (panxer.php) |
| AI Station (RK3562) firmware image | No version stated; 3.61 GB image, SHA256 recorded in artifacts | CVE-2026-105033, CVE-2026-105036, Tier-2 #21–23 |
| New Linux robot (Rockchip RK3562, firmware mode 104000; retail model name not specified) | v2.1_20260617182218_release | CVE-2026-105032, CVE-2026-105034, CVE-2026-105036, Tier-2 #21–23, #26 |
| FirmwareUpdater AArch64 ELF | No version stated; distributed in CDN bin.zip | CVE-2026-105035, Tier-2 #20 |
| Eilik Android app (com.energizeLab) | 3.0.0 (versionCode 23) | CVE-2026-105034, Tier-2 #24 |
| EnergizeLab Windows desktop app (EnergizeLabSetup-3.1.2-Win.exe) | 3.1.2 | CVE-2026-105036, Tier-2 #25 |

## Findings

The table below briefly summarizes the research, per-finding.

| ID | Vulnerability | CWE | CVSS 3.1 |
|---|---|---|---:|
| CVE-2026-105032 | Unauthenticated path traversal and arbitrary file write in AI skill upload | CWE-434, CWE-22 | 9.1 Critical |
| CVE-2026-105033 | Default root credentials with SSH enabled on AI Station | CWE-798 | 8.8 High |
| CVE-2026-105034 | Unauthenticated device-token issuance for arbitrary serial numbers | CWE-306, CWE-287 | 8.2 High |
| CVE-2026-105035 | Universal hard-coded AES key in FirmwareUpdater | CWE-321 | 7.8 High |
| CVE-2026-105036 | Firmware updates downloaded over HTTP without integrity checks | CWE-494 | 7.5 High |
| CVE-2026-105037 | Authenticated path traversal reads middleware files and secrets | CWE-73 | 9.9 Critical |
| CVE-2026-105038 | Unauthenticated AI model administration and runtime model switching | CWE-306 | 9.8 Critical |
| CVE-2026-105039 | Missing role checks in middleware admin APIs | CWE-862 | 9.6 Critical |
| CVE-2026-105040 | User-ID mass assignment enables account takeover | CWE-639 | 8.8 High |
| FINDING-1 | Unauthenticated OS command injection in legacy telemetry PHP API | CWE-78 | 9.8 Critical |
| FINDING-2 | Missing rate limits on email OTP login | CWE-307 | 9.1 Critical |
| FINDING-3 | Missing ownership checks allow robot rebinding | CWE-639 | 8.8 High |
| FINDING-4 | Cross-user access to AI long-term memories | CWE-639 | 8.1 High |
| FINDING-5 | is_internal mass assignment bypasses program moderation | CWE-915 | 7.7 High |
| FINDING-6 | Prompt injection persists attacker-controlled facts in user memory | CWE-74 | 7.6 High |
| FINDING-7 | Unauthenticated pre-signed URLs for arbitrary object keys | CWE-306 | 7.5 High |
| FINDING-8 | Public program and comment APIs expose personal information | CWE-359 | 7.5 High |

## Additional Tier-2 candidates

These entries are documented as candidates to consolidate or validate further, not as fully validated findings.

| # | Candidate vulnerability | CWE | CVSS 3.1 | Evidence/status in source |
|---:|---|---|---:|---|
| 18 | Unauthenticated SQL injection in legacy panxer.php telemetry | CWE-89 | 9.8 | Code-proven |
| 19 | Unauthenticated operational endpoints: Feishu relay, CDN purge, moderation oracle | CWE-306 | 6.7 | Live-proven |
| 20 | Unauthenticated LAN firmware push to FirmwareUpdater, leading to root execution | CWE-306, CWE-494 | 8.8 | Reverse-engineered; physical-port validation proposed |
| 21 | Captive-portal Wi-Fi credential disclosure and network configuration without authentication | CWE-306, CWE-200 | 8.1 | Rootfs-proven; device execution proposed |
| 22 | Unauthenticated USB serial commands can flash, format, and control device functions | CWE-862 | 6.9 | Protocol decoded from firmware |
| 23 | Hidden USB trigger starts root SSH Dropbear | CWE-912 | 6.9 | Script-proven; classification held for review |
| 24 | Android app uses cleartext HTTP for backends | CWE-319 | 7.5 | APK-proven |
| 25 | Windows app uses a deterministic Fernet key and disables TLS verification at 13 call sites | CWE-798, CWE-295 | 8.3 | Binary-proven; recommended for promotion |
| 26 | Firmware can send children’s audio and camera images over cleartext HTTP | CWE-319 | 5.3 | Firmware-code proven; server-flag gated |
| 27 | XML system-prompt injection in /ali_inference* | CWE-74 | 7.5 | Live-proven; candidate for promotion |

## Suggested remediation priorities

Enforce authentication, role checks, and per-object ownership on every API; remove secrets from responses and rotate exposed credentials. Constrain file operations to fixed directories, validate upload paths and content, and run services with least privilege. Protect AI configuration and treat conversation-derived memory as untrusted input. For devices, remove default credentials, replace shared keys with per-device asymmetric verification, and require signed, anti-rollback updates delivered over HTTPS. Revalidate the public program/comment endpoints and all reported fixes before relying on them.

## Timeline

All research was conducted in accordance with established, normal research practices, limiting activity to the researcher's own accounts and devices wherever possible. When testing hosted vulnerabilities, the researcher took care to minimize impact, avoid accessing or retaining third-party data, refrain from destructive actions or establishing persistent access, and leave affected systems in a state no worse than they were found.

- June–August 2026: Research, static analysis, firmware reverse engineering, and scoped live validation
- Late August: First vendor notification attempts; no response
- 2026-09-01 (Tue): Master report finalized and first retest completed; vendor notified
- 2026-09-09 (Wed): Second retest found the file-read flaw still open and secrets unrotated
- 2026-09-14 (Mon): Third retest found 42 of 44 remotely testable findings still open. One endpoint (`/api/user/list`) returned 401; a partial biometric CDN cleanup was also noted. No secrets had been rotated
- 2026-09-15 (Tue): Final 72-hour response deadline communicated
- 2026-09-18 (Fri): Final response deadline expired without vendor response
- 2026-09-22 (Tue): AI model switching and persistent persona injection demonstrated on researcher-owned robots; changes were restored
- 2026-09-27 (Sun): CVE distillation and review finalized
- 2026-10-15 (Thu): CVEs and this advisory published