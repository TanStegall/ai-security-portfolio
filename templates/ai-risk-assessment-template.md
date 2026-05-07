# AI Risk Assessment Template

**Assessment Date:** ___________  
**Assessor:** ___________  
**System Name:** ___________  
**System Owner:** ___________  
**Review Cycle:** Annual / Triggered by material change

---

## Section 1: System Overview

| Field | Response |
|-------|----------|
| System Name | |
| Business Purpose | |
| AI/ML Components | |
| Data Classifications Processed | |
| External AI APIs Used | |
| Deployment Environment | |
| User Population | |
| Go-Live Date | |

---

## Section 2: AI-Specific Risk Factors

Rate each factor: **1** (Negligible) → **5** (Critical)

| Risk Factor | Score (1–5) | Notes |
|-------------|------------|-------|
| Autonomy Level (human oversight vs. fully autonomous) | | |
| Sensitivity of data accessed | | |
| Scope of actions agent can take | | |
| Reliance on external/third-party AI APIs | | |
| Adversarial exposure (public-facing?) | | |
| Interpretability of model decisions | | |
| Training data provenance & quality | | |
| Failure mode severity | | |
| **Total Score** | **/40** | |

**Risk Level:**
- 1–15: 🟢 Low — Standard controls
- 16–25: 🟡 Medium — Enhanced controls required
- 26–35: 🟠 High — Security review required
- 36–40: 🔴 Critical — CISO approval required

---

## Section 3: Control Assessment

### Access & Authorization
- [ ] Principle of least privilege applied to AI agent permissions
- [ ] Human-in-the-loop for high-risk actions
- [ ] MFA on all AI management interfaces
- [ ] Role-based access to AI configuration

**Gaps identified:** ___________

### Input Security
- [ ] Input validation and sanitization implemented
- [ ] Prompt injection detection active
- [ ] Rate limiting on inference endpoints
- [ ] Content filtering on user inputs

**Gaps identified:** ___________

### Data Protection
- [ ] PII minimization in prompts
- [ ] Training data access controls
- [ ] Output filtering for sensitive data
- [ ] Data retention limits enforced

**Gaps identified:** ___________

### Monitoring & Detection
- [ ] Behavioral baseline established
- [ ] Anomaly detection configured
- [ ] Logging of all agent actions
- [ ] Alerting on policy violations

**Gaps identified:** ___________

### Model Security
- [ ] Model provenance verified
- [ ] Supply chain review completed
- [ ] Behavioral testing before deployment
- [ ] Rollback capability tested

**Gaps identified:** ___________

---

## Section 4: Identified Risks

| Risk ID | Description | Likelihood | Impact | Score | Owner | Remediation |
|---------|-------------|-----------|--------|-------|-------|-------------|
| R-001 | | | | | | |
| R-002 | | | | | | |
| R-003 | | | | | | |

---

## Section 5: Recommendations

### Immediate (< 30 days)
1. 
2. 

### Short-term (30–90 days)
1. 
2. 

### Long-term (90+ days)
1. 
2. 

---

## Section 6: Sign-off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Assessor | | | |
| System Owner | | | |
| Security Lead | | | |
| CISO (if High/Critical) | | | |

---

*Template from [AI Security Portfolio](../README.md) by Tangia Stegall · Adapt freely with attribution*
