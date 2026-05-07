# AI Vendor Security Assessment Template

**Vendor Name:** ___________  
**Product/Service:** ___________  
**Assessment Date:** ___________  
**Assessor:** ___________  
**Business Sponsor:** ___________

---

## Section 1: Vendor Overview

| Question | Response |
|----------|----------|
| Vendor name & HQ location | |
| AI product(s) being evaluated | |
| LLM provider (OpenAI, Anthropic, internal, etc.) | |
| Data processed (types, classification) | |
| Data residency / hosting region | |
| Relevant certifications (SOC 2, ISO 27001, etc.) | |
| Last security audit date | |
| Penetration test conducted? (date) | |

---

## Section 2: Data Handling

| Question | Yes | No | Notes |
|----------|-----|----|-------|
| Is our data used to train their models? | | | |
| Can we opt out of training data use? | | | |
| Is data encrypted in transit (TLS 1.2+)? | | | |
| Is data encrypted at rest (AES-256)? | | | |
| Is there a data retention policy? | | | |
| Can data be deleted on request? | | | |
| Are sub-processors disclosed? | | | |
| Are sub-processors bound by same terms? | | | |
| GDPR / CCPA / applicable law compliance? | | | |

**Data handling gaps:** ___________

---

## Section 3: AI-Specific Security

| Question | Yes | No | Notes |
|----------|-----|----|-------|
| Is prompt injection protection implemented? | | | |
| Is there output filtering/content safety? | | | |
| Are guardrails documented and auditable? | | | |
| Is model behavior logged? | | | |
| Are model versions pinned (no silent updates)? | | | |
| Is there a model card / system card? | | | |
| Has the model been red-teamed? | | | |
| Is there a vulnerability disclosure program? | | | |
| Are AI incidents reported to customers? | | | |

**AI security gaps:** ___________

---

## Section 4: Access & Integration Security

| Question | Yes | No | Notes |
|----------|-----|----|-------|
| API key authentication supported | | | |
| API key rotation supported | | | |
| IP allowlisting available | | | |
| Rate limiting in place | | | |
| MFA on admin portal | | | |
| Role-based access controls | | | |
| Audit logs available to customer | | | |
| SSO/SAML integration supported | | | |

---

## Section 5: Reliability & Continuity

| Question | Response |
|----------|----------|
| Published SLA / uptime guarantee | |
| Last 12-month uptime (actual) | |
| Status page URL | |
| Mean time to recovery (documented) | |
| Data export / portability available? | |
| Vendor lock-in risk level (Low/Med/High) | |

---

## Section 6: Contractual & Compliance

| Question | Yes | No | Notes |
|----------|-----|----|-------|
| DPA (Data Processing Agreement) available | | | |
| BAA available (if PHI involved) | | | |
| AI-specific liability terms | | | |
| Right to audit | | | |
| Breach notification SLA (hours) | | | |
| Insurance coverage documented | | | |

---

## Section 7: Risk Rating

| Category | Score (1–5) | Weight | Weighted Score |
|----------|------------|--------|----------------|
| Data handling | | 25% | |
| AI-specific security | | 30% | |
| Access controls | | 20% | |
| Contractual protections | | 15% | |
| Reliability | | 10% | |
| **Overall** | | **100%** | **/5.0** |

**Recommendation:**
- 4.0–5.0: ✅ Approve
- 3.0–3.9: ⚠️ Conditional approval (address gaps before go-live)
- 2.0–2.9: 🟠 Defer (significant remediation required)
- < 2.0: ❌ Reject

---

## Section 8: Conditions of Approval

*Complete only if recommending conditional approval*

| Condition | Owner | Due Date | Status |
|-----------|-------|----------|--------|
| | | | |
| | | | |

---

## Section 9: Sign-off

| Role | Name | Date | Decision |
|------|------|------|----------|
| Assessor | | | |
| Procurement | | | |
| Security Lead | | | |
| Legal | | | |
| CISO | | | |

---

*Template from [AI Security Portfolio](../README.md) by Tangia Stegall · Adapt freely with attribution*
