# 🤖 Agent Risk Matrix

> **AI Agent Access Control Framework — Permissions, Boundaries & Blast Radius**

A practical framework for assessing and controlling the risk surface of autonomous AI agents, covering tool access, privilege levels, and human-in-the-loop checkpoints.

---

## Why Agent Security is Different

Traditional software has deterministic behavior. AI agents don't. They make autonomous decisions about which tools to call, what data to access, and what actions to take — creating a dynamic and hard-to-predict attack surface.

```
Traditional Software:  Input → [Fixed Logic] → Output
AI Agent:              Input → [LLM Reasoning] → [Tool Selection] → [Action] → Output
                                      ↑                   ↑
                              Unpredictable          Unbounded if not controlled
```

**The core risk:** An agent that can read email, write files, call APIs, and browse the web has enormous blast radius if compromised or manipulated.

---

## 🎯 Risk Matrix

### Agent Capability Risk Scoring

Rate each capability on **Likelihood × Impact** (1–5 scale):

| Capability | Likelihood | Impact | Risk Score | Control Required |
|------------|-----------|--------|------------|------------------|
| Read internal documents | 3 | 3 | 9 | Access logging |
| Send emails / messages | 3 | 5 | 15 | HITL approval |
| Execute code | 4 | 5 | 20 | Sandboxing + HITL |
| Write/delete files | 3 | 5 | 15 | Scope limits + HITL |
| Call external APIs | 3 | 4 | 12 | Allowlist + rate limits |
| Web browsing | 4 | 4 | 16 | Content filtering |
| Database queries | 3 | 5 | 15 | Read-only + row limits |
| System commands | 5 | 5 | 25 | Deny by default |
| Financial transactions | 2 | 5 | 10 | HITL + thresholds |
| User impersonation | 2 | 5 | 10 | Deny by default |

**Risk Thresholds:**
- 🟢 1–8: Monitor only
- 🟡 9–14: Logging + alerts
- 🟠 15–19: Human-in-the-loop approval
- 🔴 20–25: Deny or strict sandbox

---

## 🏗️ Access Control Framework

### Principle of Least Privilege — Agent Edition

```yaml
# agent-permissions.yaml — Template

agent:
  name: "SecurityTriageAgent"
  version: "1.0"
  trust_level: "low"          # low | medium | high | autonomous
  
  permissions:
    data_access:
      read:
        - "alerts/*"           # Scoped path access
        - "playbooks/read-only/*"
      write:
        - "tickets/create"     # Can create, not modify existing
      deny:
        - "users/*"            # No access to user data
        - "credentials/*"      # Never access secrets
        
    tool_access:
      allowed:
        - name: "search_alerts"
          rate_limit: "100/hour"
        - name: "create_ticket"
          rate_limit: "20/hour"
          requires_approval: false
        - name: "send_notification"
          rate_limit: "10/hour"
          requires_approval: true    # HITL required
      denied:
        - "execute_code"
        - "delete_*"
        - "modify_user"
        
    network:
      allowlist:
        - "internal-siem.company.com"
        - "ticketing.company.com"
      denylist:
        - "*"                  # Default deny all external
        
  guardrails:
    max_actions_per_run: 50
    max_run_duration_seconds: 300
    human_in_the_loop:
      required_for: ["send_notification", "escalate_incident"]
      timeout_action: "pause"   # pause | abort | alert
    auto_abort_on:
      - "repeated_errors > 3"
      - "unexpected_tool_call"
      - "data_volume_anomaly"
```

### Trust Level Definitions

| Level | Description | Example | HITL Required |
|-------|-------------|---------|---------------|
| `low` | Read-only, no external calls | Report generator | Never |
| `medium` | Internal writes, limited scope | Ticket creator | High-risk actions |
| `high` | External calls, broader scope | Alert responder | Destructive actions |
| `autonomous` | Full capability (avoid in production) | — | Audit trail only |

---

## 🛡️ The Minimal Agent Pattern

Design agents with the smallest possible capability set:

```python
# ❌ OVER-PRIVILEGED: Agent with unrestricted tool access
class UnsafeAgent:
    tools = ["read_files", "write_files", "delete_files", 
             "send_email", "execute_code", "call_api", "browse_web"]
    # One prompt injection = full system compromise

# ✅ MINIMAL: Agent scoped to its specific task
class SecureTriageAgent:
    tools = [
        Tool("read_alert", scope="alerts/{alert_id}", permission="read"),
        Tool("classify_severity", pure_function=True),   # No I/O side effects
        Tool("create_ticket", scope="tickets/new", rate_limit="20/hr"),
    ]
    max_iterations = 10
    timeout = 120  # seconds
    human_approval_required = ["create_ticket"]
```

---

## 🔍 Monitoring & Anomaly Detection

### Agent Behavioral Baseline

Track these metrics per agent run and alert on deviations:

```python
AGENT_METRICS = {
    "tool_calls_per_run": {"baseline": 5, "alert_threshold": 20},
    "data_volume_bytes": {"baseline": 10_000, "alert_threshold": 500_000},
    "run_duration_seconds": {"baseline": 30, "alert_threshold": 300},
    "external_requests": {"baseline": 0, "alert_threshold": 1},
    "error_rate": {"baseline": 0.05, "alert_threshold": 0.3},
    "unique_tools_used": {"baseline": 3, "alert_threshold": 8},
}
```

### Red Flags — Investigate Immediately

- Agent attempts to access tools outside its allowlist
- Sudden spike in data volume accessed
- Agent modifies its own configuration or permissions
- Circular or recursive tool calls
- Agent requests credentials or API keys
- Unexpected external network connections

---

## 📋 Control Mapping

| Control | MITRE ATLAS | NIST AI RMF | CIS |
|---------|-------------|-------------|-----|
| Least privilege | AML.M0047 | GOVERN-2.1 | CIS 4 |
| Tool allowlisting | AML.M0015 | MAP-2.2 | CIS 2 |
| Human-in-the-loop | AML.M0045 | MANAGE-1.3 | — |
| Behavioral monitoring | AML.M0003 | MEASURE-2.7 | CIS 8 |
| Sandboxing | AML.M0031 | MAP-2.1 | CIS 4 |

---

## 📂 Files in This Directory

```
agent-risk-matrix/
├── README.md                    # This file
├── agent-permissions.yaml       # Permission template
├── risk-scoring-worksheet.md    # Blank scoring worksheet
└── monitoring-queries.md        # SIEM queries for agent monitoring
```

---

*Part of the [AI Security Portfolio](../../README.md) by Tangia Stegall*
