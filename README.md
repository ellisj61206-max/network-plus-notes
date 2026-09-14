# CompTIA Network+ (N10-009) - Passed

Notes and practice-quiz record from my Network+ preparation. Kept as a technical reference and as a record of how I actually studied for it.

**Result:** Passed
**Exam:** CompTIA Network+ N10-009
**Next up:** CompTIA Security+ SY0-701 (notes in my security-plus-notes repo)

## By the numbers

| Metric | Value |
| --- | --- |
| Practice quizzes logged | 34 |
| Average, first attempt | 81.6% |
| Average, after retakes | 87.4% |
| Quizzes below 75% on first attempt | 10 |
| Quizzes below 75% after retakes | 0 |

## Repo layout

| Path | What's in it |
| --- | --- |
| notes/01-networking-concepts.md | Domain 1.0 - OSI model, devices, cloud, IP, cabling, topologies, subnetting, SDN, IPv6 |
| notes/02-network-implementation.md | Domain 2.0 - routing, NAT, VLANs and trunking, STP, wireless, physical installations |
| notes/03-network-operations.md | Domain 3.0 - documentation, SNMP, monitoring, disaster recovery, DHCP, DNS, VPNs, remote access |
| notes/04-network-security.md | Domain 4.0 - PKI, AAA, security technologies, compliance, attacks, device hardening |
| notes/05-network-troubleshooting.md | Domain 5.0 - methodology, cable and interface issues, switching, wireless, tools and commands |
| quiz-log.md | All 34 practice quizzes with first-attempt and retake scores |
| missed-questions.md | Every question I got wrong, my answer next to the correct one |

## Domain coverage

| Domain | Exam weight | Notes |
| --- | --- | --- |
| 1.0 Networking Concepts | 23% | Covered |
| 2.0 Network Implementation | 20% | Covered |
| 3.0 Network Operations | 19% | Covered |
| 4.0 Network Security | 14% | Covered |
| 5.0 Network Troubleshooting | 24% | Covered |

## How I studied

- Worked the Professor Messer N10-009 series start to finish, rewriting each objective in my own words rather than copying slides.
- Took a practice quiz after every section. Anything under 75% got retaken until it cleared. Ten quizzes needed a second pass.
- Logged every missed question with my wrong answer beside the correct one. That file (missed-questions.md) ended up being the main review material in the final week - the wrong answers showed patterns the scores alone did not.
- Built my own study tools along the way: an interactive roadmap with checkbox progress tracking and timers, and a 90-question timed practice exam with domain-weighted scoring, flagging, and per-domain results.

## Weakest areas going in

Identified from quiz performance, not guesswork:

1. Troubleshooting patterns and methodology
2. Security tool roles - IPS vs IDS vs SIEM
3. OSI model and TCP/UDP port numbers

The cheat sheet I wrote for #2, because these three get confused constantly:

- **IPS** (Intrusion Prevention System) - actively blocks malicious traffic.
- **IDS** (Intrusion Detection System) - detects only, does not block.
- **SIEM** (Security Information and Event Management) - aggregates, logs, and analyzes. Not real-time detection.
- **Honeypot** - decoy system, for research and observation.
- **VPN** - a secure tunnel. Not a threat mitigation control.
