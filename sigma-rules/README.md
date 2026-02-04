# OpenClaw Sigma Detection Rules

Sigma rules for detecting malicious or suspicious activity in OpenClaw deployments. Designed for use with Security Onion, Splunk, Elasticsearch, or any SIEM that supports Sigma.

## Rules Included

| Rule | Level | Description | Log Source |
|------|-------|-------------|------------|
| `openclaw-suspicious-exec.yml` | HIGH | Dangerous commands (rm -rf, reverse shells, etc.) | Gateway logs |
| `openclaw-data-exfil.yml` | MEDIUM | Exfiltration attempts (pastebin, webhooks, etc.) | Gateway logs |
| `openclaw-exec-audit-dangerous.yml` | HIGH | Destructive, persistence, credential access commands | Exec audit logs |
| `openclaw-exec-audit-recon.yml` | MEDIUM | System/network reconnaissance activity | Exec audit logs |
| `openclaw-exec-audit-credential-access.yml` | HIGH | Reading secrets, keys, env vars | Exec audit logs |
| `openclaw-exec-audit-credential-exfil.yml` | CRITICAL | Exfiltrating API keys/tokens | Exec audit logs |
| `openclaw-exec-audit-exposed-secrets.yml` | CRITICAL | API keys appearing directly in commands | Exec audit logs |

## Log Sources

### Gateway Logs (`logsource.service: gateway`)
Standard OpenClaw gateway logs from `/tmp/openclaw/openclaw-*.log`

### Exec Audit Logs (`logsource.service: exec-audit`)
JSON logs from the exec-audit script. See [scripts/exec-audit](../scripts/) for the extraction tool.

## Deployment

### Security Onion (Elastalert2)

```bash
# Convert to Elastalert format
pip install sigma-cli pysigma-backend-elasticsearch
sigma convert -t elastalert *.yml -o elastalert/

# Copy to SO manager
scp elastalert/*.yml so-manager:/opt/so/rules/elastalert/

# Restart Elastalert
sudo so-elastalert-restart
```

### Splunk

```bash
sigma convert -t splunk *.yml > openclaw_splunk_rules.txt
```

### Elasticsearch (Detection Engine)

```bash
sigma convert -t elasticsearch -p ecs_windows *.yml > openclaw_detections.json
```

## MITRE ATT&CK Coverage

| Tactic | Techniques |
|--------|------------|
| **Execution** | T1059 (Command and Scripting Interpreter) |
| **Persistence** | T1053 (Scheduled Task/Job) |
| **Credential Access** | T1552.001 (Credentials in Files), T1552.004 (Private Keys) |
| **Discovery** | T1082, T1083, T1046 (System/File/Network Discovery) |
| **Exfiltration** | T1041 (Exfiltration Over C2 Channel), T1020 (Automated Exfiltration) |

## Tuning

Adjust `falsepositives` and `level` based on your environment:

- **Recon rules** are medium severity since these commands are common in normal usage
- **Credential access** may trigger on legitimate config management - allowlist known operations
- **Exposed secrets** has specific regex patterns - test against your actual API key formats

## Contributing

PRs welcome! Please include:
- Valid Sigma YAML syntax
- MITRE ATT&CK tags
- Realistic false positive documentation
