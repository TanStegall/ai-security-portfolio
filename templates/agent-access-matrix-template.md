# Agent Access Matrix

**System:** ___________  **Date:** ___________  **Reviewed By:** ___________  
**Review Cycle:** Quarterly / On agent change

---

## Agent Inventory

| Agent | Purpose | Data Access (Classification) | Tools Allowed | Write Access | Human Approval Required | Risk Level |
|-------|---------|------------------------------|---------------|-------------|------------------------|------------|
| [Name] | [Purpose] | [Public / Internal / Confidential / Restricted] | [List tools] | Yes / No | Yes / No | L / M / H |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |

**Risk Level:** L = Low (read-only, internal) · M = Medium (writes, scoped) · H = High (external calls, broad access)

---

## Per-Agent Detail

*Complete one block per agent. Copy and paste as needed.*

### Agent: ___________

| Field | Value |
|-------|-------|
| Purpose | |
| Trust Level | Low / Medium / High / Autonomous |
| Max actions per run | |
| Max run duration | |
| On unexpected action | Pause / Abort / Alert |

**Data Access**

| Dataset / System | Permission | Classification |
|-----------------|------------|----------------|
| | Read / Write / Deny | |
| | | |

**Tools Allowed**

| Tool | Rate Limit | Approval Required |
|------|-----------|-------------------|
| | | Yes / No |
| | | |

**Tools Explicitly Denied**

- 
- 

**Network Access**

| Destination | Allowed? |
|-------------|----------|
| Internal systems only | Yes / No |
| External APIs (list) | Yes / No |
| Public internet | Yes / No |

---

## Access Control Principles

- [ ] Least privilege enforced for all agents
- [ ] Write access explicitly justified per agent
- [ ] Human approval gates defined for high-impact actions
- [ ] Audit logging enabled for all tool calls
- [ ] Secrets managed via secrets manager (not env vars)
- [ ] Rate limits configured on all tool calls
- [ ] Auto-abort conditions defined per agent
- [ ] Agent permissions reviewed on this schedule: ___________

---

## Change Log

| Date | Agent | Change Made | Approved By |
|------|-------|-------------|-------------|
| | | | |
| | | | |

---

*Template from [AI Security Portfolio](../README.md) by Tangia Stegall · Adapt freely with attribution*
