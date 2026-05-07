# 📄 Templates

> **Reusable templates for AI risk management, vendor assessment, incident response, and agent governance**

---

## Available Templates

| Template | Use When |
|----------|----------|
| [AI System Inventory Record](./ai-system-inventory-template.md) | Registering any AI system in your org's inventory |
| [AI Risk Assessment](./ai-risk-assessment-template.md) | Evaluating risk of a new AI system or feature |
| [Agent Access Matrix](./agent-access-matrix-template.md) | Documenting and auditing all agents in a system |
| [AI Vendor Security Assessment](./ai-vendor-assessment-template.md) | Onboarding a new AI vendor or LLM provider |
| [AI Incident Report](./ai-incident-report-template.md) | Documenting an AI security incident |

---

## How These Fit Together

```
New AI System Identified
        │
        ▼
[AI System Inventory Record]  ← Register it first
        │
        ▼
[AI Risk Assessment]          ← Score its risk level
        │
        ▼
[AI Vendor Assessment]        ← If using external LLM/API
        │
        ▼
[Agent Access Matrix]         ← If it uses AI agents
        │
        ▼
[AI Incident Report]          ← If something goes wrong
```

---

*Part of the [AI Security Portfolio](../README.md) by Tangia Stegall*
