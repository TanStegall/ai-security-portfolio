# AI Risk Assessment

**System:** ___________  **Date:** ___________  **Assessor:** ___________  
**System Owner:** ___________  **Review Cycle:** Annual / Triggered by material change

---

## 1. System Overview

| Field | Response |
|-------|----------|
| Purpose | |
| Data inputs (type/classification) | |
| Model provider | |
| Deployment environment | |
| External AI APIs used | |
| User population | |
| Public-facing? | Yes / No |

---

## 2. Risk Classification (NIST AI RMF)

- **Risk level:** [ ] Low  [ ] Medium  [ ] High  [ ] Critical
- **Justification:** ___________

| Risk Factor | Score (1–5) | Notes |
|-------------|------------|-------|
| Autonomy level (human oversight vs. fully autonomous) | | |
| Sensitivity of data accessed | | |
| Scope of actions the system can take | | |
| Reliance on external/third-party AI APIs | | |
| Adversarial exposure (public-facing?) | | |
| Failure mode severity | | |
| **Total Score** | **/30** | |

**Thresholds:** 1–10 🟢 Low · 11–18 🟡 Medium · 19–24 🟠 High · 25–30 🔴 Critical

---

## 3. OWASP LLM Top 10 Applicability

| Risk | Applicable? | Notes |
|------|-------------|-------|
| LLM01: Prompt Injection | Yes / No | |
| LLM02: Insecure Output Handling | Yes / No | |
| LLM03: Training Data Poisoning | Yes / No | |
| LLM04: Model Denial of Service | Yes / No | |
| LLM05: Supply Chain Vulnerabilities | Yes / No | |
| LLM06: Sensitive Information Disclosure | Yes / No | |
| LLM07: Insecure Plugin Design | Yes / No | |
| LLM08: Excessive Agency | Yes / No | |
| LLM09: Overreliance | Yes / No | |
| LLM10: Model Theft | Yes / No | |

---

## 4. MITRE ATLAS Threat Model

| Technique ID | Technique | Likelihood | Impact | Control |
|-------------|-----------|-----------|--------|---------|
| AML.T0051 | LLM Prompt Injection | | | |
| AML.T0020 | Training Data Poisoning | | | |
| AML.T0048 | Exfiltration via Inference API | | | |
| AML.T0015 | Evade ML Model | | | |
| AML.T0029 | Denial of ML Service | | | |
| *(add rows as needed)* | | | | |

**Likelihood / Impact scale:** 1 = Low · 2 = Medium · 3 = High

---

## 5. Controls & Gaps

| Control | Status | Owner | Due Date |
|---------|--------|-------|----------|
| Input validation & sanitization | | | |
| Prompt architecture hardening | | | |
| Output filtering | | | |
| Audit logging | | | |
| Human oversight / HITL | | | |
| Least privilege (agent permissions) | | | |
| Anomaly detection & monitoring | | | |
| Data provenance tracking | | | |
| *(add rows as needed)* | | | |

**Status options:** ✅ In Place · 🔄 In Progress · ❌ Gap · N/A

---

## 6. Risk Decision

- [ ] **Accept** — Risk is within tolerance; no action required
- [ ] **Mitigate** — Implement controls to reduce risk (see Section 5)
- [ ] **Transfer** — Shift risk via contract, insurance, or vendor SLA
- [ ] **Avoid** — Do not deploy / discontinue system

**Rationale:** ___________

**Conditions (if Mitigate):**

| Action | Owner | Due Date |
|--------|-------|----------|
| | | |
| | | |

---

## 7. Sign-off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Assessor | | | |
| System Owner | | | |
| Security Lead | | | |
| CISO (if High / Critical) | | | |

---

*Template from [AI Security Portfolio](../README.md) by Tangia Stegall · Adapt freely with attribution*
