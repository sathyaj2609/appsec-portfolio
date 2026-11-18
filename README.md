# AppSec Portfolio — Sathya Jayaraman

Application Security Engineer. Secure code review (Python, Java), SAST/DAST in CI/CD, threat modeling, cloud/IAM security.

This repo is the index for my hands-on security work. Each row links to code or a write-up.

| # | Project | What it shows | Status | Link |
|---|---------|---------------|--------|------|
| 1 | PortSwigger Web Security Academy (API + GraphQL + auth labs) | Hands-on exploitation and remediation of modern web/API flaws | In progress | [notes](notes/) · [write-ups](writeups/) |
| 2 | Bug bounty / VDP practice | Scoped, methodical testing and clear reporting | Starting | — |
| 3 | Semgrep Registry contribution | Writing precise, tested detection rules | Planned | — |
| 4 | Terraform on AWS + Checkov/Trivy | Secure IaC, least-privilege IAM, scan-driven fixes | Planned | — |
| 5 | AppSec CI/CD pipeline | Semgrep rules + Python policy gate | Done | [sathyaj2609](https://github.com/sathyaj2609) |

## Write-ups

1. [GraphQL attack surface](writeups/01-graphql-attack-surface.md) — draft

## Ground rules I follow

- Only test systems I own or that explicitly authorize testing.
- No credentials, account IDs, or undisclosed findings in this repo.
- Write-ups explain concepts and fixes, not flag-by-flag lab answers.
