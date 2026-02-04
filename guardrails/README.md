# OpenClaw Guardrails

Security boundary templates for OpenClaw AI assistant deployments.

## What Are Guardrails?

Guardrails are behavioral rules that define what an AI assistant can and cannot do autonomously. They protect against:

- **Prompt injection attacks** - Malicious instructions hidden in external content
- **Unauthorized actions** - Preventing the AI from taking actions without approval
- **Data exfiltration** - Protecting sensitive information from leaking
- **Social engineering** - Resisting manipulation attempts

## Files

| File | Description |
|------|-------------|
| `GUARDRAILS-TEMPLATE.md` | Complete template with all security patterns |

## Quick Start

1. Copy `GUARDRAILS-TEMPLATE.md` to your OpenClaw workspace as `GUARDRAILS.md`
2. Customize the trust model (who can give instructions)
3. Adjust operational rules for your use case
4. Add to your agent's startup reading list (AGENTS.md)

## Key Concepts

### Trust Model
Define who can instruct your AI:
- **Full trust:** Direct messages from approved users
- **Zero trust:** Any external content (websites, emails, documents)

### Operational Policies
Three levels of autonomy:
- **Autonomous:** Safe actions the AI can take without asking
- **Confirm first:** Show draft/plan before executing
- **Approval required:** Must wait for explicit user approval

### Prompt Injection Defense
Patterns to detect and block:
- Instruction hijacking (in 10+ languages)
- Jailbreak personas (DAN, developer mode, etc.)
- Authority spoofing
- Social engineering frames
- Delimiter injection
- Obfuscation techniques

## Customization Checklist

- [ ] Define approved users
- [ ] Set email handling policies
- [ ] Set calendar/scheduling policies
- [ ] Configure development guardrails
- [ ] Define communication policies
- [ ] Set up escalation procedures
- [ ] Add domain-specific rules
- [ ] Test with sample attacks

## Defense in Depth

Guardrails are one layer of protection. Consider also:

- **Network isolation** - VLAN segmentation, firewall rules
- **SIEM integration** - Log analysis and alerting (see `/sigma-rules`)
- **Process monitoring** - Detect anomalous behavior
- **Regular audits** - Review what actions were taken

## References

- [OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- [MITRE ATLAS](https://atlas.mitre.org/)
- [OpenClaw Security Docs](https://docs.openclaw.ai/security)

---

*Part of the [OSAPS](https://github.com/er587/osaps) project - OpenClaw Self-hosted AI Personal Security*
