# 🗺️ AI Threat Model — MITRE ATLAS Framework

> **Systematic threat modeling for AI/ML systems using MITRE ATLAS**  
> Tactics, Techniques & Procedures (TTPs) mapped to mitigations for production AI deployments.

---

## What is MITRE ATLAS?

ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems) is the AI equivalent of MITRE ATT&CK. It catalogs real-world adversarial techniques targeting machine learning systems, from reconnaissance through impact.

**ATLAS Matrix:** https://atlas.mitre.org/matrices/ATLAS

---

## 🎯 Threat Model Scope

**System Under Analysis:** AI-Augmented Security Operations Platform  
**Components:**
- LLM-based alert triage agents
- RAG knowledge base (security runbooks)
- External API integrations (SIEM, ticketing, threat intel)
- Web-facing chat interface
- Fine-tuned classification models

**Trust Boundaries:**
```
[Internet] → [WAF] → [Chat Interface] → [Orchestration Layer]
                                               │
              [Vector DB] ←──────────────────►[Agent Orchestrator]
              [SIEM API]  ←──────────────────►
              [Ticket API]←──────────────────►
                                               │
                                        [LLM Provider API]
                                           (external)
```

---

## 🔴 ATLAS Threat Coverage

### Reconnaissance (AML.TA0001)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| Search for Victim's AI Resources | AML.T0000 | Attacker identifies AI endpoints, model versions, training data sources | Medium | Medium |
| Active Scanning — AI Applications | AML.T0001 | Probing API endpoints for model fingerprinting | High | Medium |

**Mitigation:** Rate limiting, API key rotation, avoid exposing model version in responses.

---

### Resource Development (AML.TA0002)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| Develop Capabilities — Adversarial ML | AML.T0017 | Crafting adversarial inputs to evade classifiers | Low | High |
| Acquire Infrastructure | AML.T0008 | Setting up infrastructure to exfiltrate data from compromised agents | Low | Critical |

---

### Initial Access (AML.TA0003)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| Prompt Injection | AML.T0051 | Injecting instructions via user input or retrieved content | **High** | **Critical** |
| Exploit Public-Facing Application | AML.T0043 | Exploiting vulnerabilities in the chat interface | Medium | High |
| Supply Chain Compromise | AML.T0010 | Compromising ML model or dependency supply chain | Low | Critical |

**Priority Controls:**
- Input validation and sanitization
- WAF with LLM-specific rules
- Dependency scanning + SBOM for ML packages

---

### Execution (AML.TA0004)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| LLM Prompt Injection — Direct | AML.T0051.000 | Direct instruction override via chat interface | High | High |
| LLM Prompt Injection — Indirect | AML.T0051.001 | Injection via retrieved documents or external content | High | Critical |
| Craft Adversarial Data | AML.T0020 | Poisoning knowledge base with malicious content | Medium | Critical |

---

### Persistence (AML.TA0005)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| Poison Training Data | AML.T0020 | Long-term backdoors via training data manipulation | Low | Critical |
| Backdoor ML Model | AML.T0018 | Embedding triggers in fine-tuned models | Low | Critical |

**Mitigation:** Model provenance tracking, fine-tuning audit logs, behavioral testing before deployment.

---

### Exfiltration (AML.TA0009)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| Exfiltration via ML Inference API | AML.T0048 | Using model outputs to extract sensitive training data | Medium | High |
| Model Inversion | AML.T0024 | Reconstructing training data from model responses | Low | High |
| Membership Inference | AML.T0022 | Determining if specific records were in training data | Medium | Medium |

---

### Impact (AML.TA0010)

| Technique | ID | Description | Likelihood | Impact |
|-----------|-----|-------------|-----------|--------|
| Denial of ML Service | AML.T0029 | Flooding inference API to degrade availability | Medium | High |
| Evade ML Model | AML.T0015 | Crafting alerts that evade triage classifier | Medium | High |
| Functional Adversarial Attack | AML.T0043 | Causing misclassification of real threats as benign | High | **Critical** |

---

## 🛡️ Mitigation Matrix

### Priority Mitigations (Top 10)

| Rank | Mitigation | ATLAS ID | Addresses |
|------|-----------|----------|-----------|
| 1 | Input Validation | AML.M0015 | T0051, T0043 |
| 2 | Prompt Architecture Hardening | AML.M0031 | T0051 |
| 3 | Least Privilege (Agent Access) | AML.M0047 | T0048, T0029 |
| 4 | Data Provenance Tracking | AML.M0007 | T0020, T0018 |
| 5 | Model Behavioral Testing | AML.M0001 | T0015, T0043 |
| 6 | Output Filtering | AML.M0004 | T0048, T0051 |
| 7 | Human-in-the-Loop | AML.M0045 | T0051, T0029 |
| 8 | Anomaly Detection | AML.M0003 | T0048, T0022 |
| 9 | Rate Limiting | AML.M0025 | T0029, T0024 |
| 10 | Supply Chain Security | AML.M0013 | T0010, T0018 |

---

## 📊 Risk Heat Map

```
                    IMPACT
                Low    Med    High   Critical
              ┌──────┬──────┬──────┬──────────┐
         High │      │T0001 │T0029 │T0051(ind)│
L            ├──────┼──────┼──────┼──────────┤
I       Med  │      │T0022 │T0048 │T0020,T0043│
K            ├──────┼──────┼──────┼──────────┤
E       Low  │      │      │T0024 │T0018,T0010│
L            └──────┴──────┴──────┴──────────┘
I
H
O
O
D
```

**Immediate Focus:** T0051 (Indirect Prompt Injection) and T0043 (Adversarial Evasion)

---

## 🔗 Framework Cross-Reference

| Threat | ATLAS | OWASP LLM | NIST AI RMF | STRIDE |
|--------|-------|-----------|-------------|--------|
| Prompt Injection | T0051 | LLM01 | MAP-2.1 | Spoofing |
| Data Poisoning | T0020 | LLM03 | GOVERN-1.1 | Tampering |
| Model Evasion | T0015 | LLM05 | MEASURE-2.3 | Elevation |
| Training Exfil | T0024 | LLM06 | MANAGE-2.2 | Info Disclosure |
| DoS | T0029 | LLM04 | MANAGE-1.4 | Denial of Service |
| Supply Chain | T0010 | LLM05 | GOVERN-4.1 | Tampering |

---

## 📂 Files in This Directory

```
ai-threat-model/
├── README.md                    # This document
├── threat-model-template.md     # Blank template for new systems
├── atlas-ttps-reference.md      # Quick reference for ATLAS TTPs
└── risk-register.md             # Tracked risks with owners & status
```

---

*Part of the [AI Security Portfolio](../../README.md) by Tangia Stegall*
