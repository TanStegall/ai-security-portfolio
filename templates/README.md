# 📄 Templates

> **Reusable templates for AI risk management, vendor assessment, incident response, and agent governance**

---

## Available Templates

| Template | Use When | Send To |
|----------|----------|---------|
| [AI System Inventory Record](./ai-system-inventory-template.md) | Registering any AI system in your org's inventory | Internal |
| [AI Risk Assessment](./ai-risk-assessment-template.md) | Evaluating risk of a new AI system or feature | Internal |
| [Agent Access Matrix](./agent-access-matrix-template.md) | Documenting and auditing all agents in a system | Internal |
| [AI Vendor Security Questionnaire](./ai-vendor-questionnaire.md) | Sent to vendor to complete before onboarding | **→ Vendor** |
| [AI Vendor Security Assessment](./ai-vendor-assessment-template.md) | Your internal scorecard after vendor responds | Internal |
| [AI Incident Report](./ai-incident-report-template.md) | Documenting an AI security incident | Internal |

---

## How These Fit Together

```
New AI System Identified
        │
        ▼
[AI System Inventory Record]        ← Register it first
        │
        ▼
[AI Risk Assessment]                ← Score its risk level
        │
        ▼
[AI Vendor Questionnaire]           ← Send to vendor to fill out
        │
        ▼
[AI Vendor Security Assessment]     ← Your internal scorecard using their answers
        │
        ▼
[Agent Access Matrix]               ← If it uses AI agents
        │
        ▼
[AI Incident Report]                ← If something goes wrong
```

---

*Part of the [AI Security Portfolio](../README.md) by Tangia Stegall*
