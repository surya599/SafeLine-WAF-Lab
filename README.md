# SafeLine WAF: Deployment and Validation Lab

Hands-on cybersecurity lab in which **SafeLine WAF (v9.4.7)** is deployed as a reverse proxy in front of **DVWA**, then tested from a Kali Linux VM using a SQL injection payload and repeated requests that trigger rate limiting.

📄 **Full report:** [`docs/SafeLine_WAF_Technical_Documentation.pdf`](docs/SafeLine_WAF_Technical_Documentation.pdf)

## Lab summary

| Item | Detail |
|---|---|
| Hypervisor | VMware Workstation |
| Attacker | Kali Linux 2026.2 VM |
| Defender | Ubuntu 64-bit VM running SafeLine WAF |
| Protected app | DVWA (reached at `/DVWA/`) |
| WAF site | `www.webserver.vsbr`, 443/HTTPS, reverse proxy |
| Upstream | `http://192.168.1.35:8080` |
| WAF console | `https://192.168.1.35:9443` |

## Evidence highlights

- A SQL injection test on DVWA (`'OR' = 1`) returned an **Access Forbidden** page from SafeLine.
- Rate limiting triggered repeatedly (3 requests within 10 seconds, 5-minute block); HTTP 429 responses were recorded.
- The statistics dashboard showed 224 requests with 29 shown as blocked.

Screenshots are in [`screenshots/`](screenshots/), numbered to match the figures in the report.

## Status

Draft. Some details (install commands, VM specs, exact attack commands) are marked **TO BE CONFIRMED** in the report and will be added.

## Disclaimer

All testing was performed in an isolated personal lab against an intentionally vulnerable application. Do not test systems you do not own or have permission to test.
