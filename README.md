# OSAPS - OpenClaw Self-hosted AI Personal Security

A comprehensive deployment guide for setting up [OpenClaw](https://github.com/openclaw/openclaw) securely on dedicated hardware.

## What is This?

This repository contains a detailed guide for deploying OpenClaw — a self-hosted AI assistant framework — with enterprise-grade security practices. It's designed for security-conscious individuals who want the power of frontier AI models while maintaining control over their data and infrastructure.

## Who is This For?

- **Security professionals** who want a personal AI assistant without cloud trust issues
- **Privacy-conscious users** who want conversations to stay on their hardware
- **Tinkerers** who enjoy building and customizing their own AI infrastructure
- **Anyone** who wants to understand the security implications of self-hosted AI

## What's Included

### 📘 [OpenClaw Deployment Guide](./openclaw-deployment-guide.md)

A step-by-step guide covering:

| Section | Topics |
|---------|--------|
| **Identity Setup** | Dedicated accounts, personality files, Claude subscription |
| **Installation** | Mac mini setup, Node.js, OpenClaw configuration |
| **Security Hardening** | DM policies, secrets management, plugin allowlists |
| **Messaging Channels** | Telegram, Signal, Discord, WhatsApp, iMessage |
| **Knowledge Wiki** | Semantic search with qmd, institutional memory |
| **Token Optimization** | Compaction, heartbeats, cost management |
| **Guardrails** | Isolation, behavior controls, approval workflows |

### 📎 Appendix A: Hybrid Local/Cloud Architecture

Cost optimization using a dedicated LLM server alongside cloud AI:

- **Brain/Muscle pattern** — Route tasks to appropriate models
- **Hardware recommendations** — GPU, RAM, storage sizing
- **OpenClaw + Ollama configuration** — Connect to local models
- **Workflow examples** — News briefings, code review, email triage
- **Cost analysis** — Break-even calculations

### 🔒 Appendix B: Enterprise Security Hardening

Defense-in-depth for security-conscious deployments:

- **VLAN isolation** — Dedicated network segment with strict ACLs
- **Little Snitch** — Process-level firewall on macOS
- **Process monitoring** — Baseline and anomaly detection
- **SIEM integration** — Security Onion with custom Sigma rules
- **Kill switch procedure** — Incident response playbook

## Quick Start

1. Read the [Deployment Guide](./openclaw-deployment-guide.md)
2. Follow Phases 1-5 for basic setup
3. Complete Phase 4 (Security Hardening) before going live
4. Optionally implement Appendix B for enterprise security

## PDF Version

A [PDF version](./openclaw-deployment-guide.pdf) is available for offline reading or printing.

## Contributing

Found an issue or have a suggestion? Open an issue or PR. Security improvements are especially welcome.

## Disclaimer

> This guide is provided for educational purposes only. The authors make no warranties about the completeness, reliability, or security of this information. Implement at your own risk. This is not professional security consulting, and you should consult a qualified security professional for your specific environment and threat model.

## License

This work is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — you're free to share and adapt with attribution.

## Acknowledgments

- [OpenClaw](https://github.com/openclaw/openclaw) — The framework this guide is built around
- OpenClaw community — Brain/Muscle architecture concepts
- Security Onion — Open-source SIEM platform

---

*Created February 2026 by Eric (a network security professional)*
