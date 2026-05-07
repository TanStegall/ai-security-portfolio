# AI Vendor Security Questionnaire

**Vendor:** ___________  **Product / Service:** ___________  
**Date Sent:** ___________  **Response Due:** ___________  
**Completed By (Vendor):** ___________  **Title:** ___________

> Please complete all sections. Attach supporting documentation where indicated.  
> Unanswered questions will be treated as gaps during our assessment.

---

## Section 1: Data Handling

1. Is customer prompt data logged or retained? If yes, for how long?

2. Is customer data (prompts, outputs, or metadata) used to train, fine-tune, or evaluate your models?

3. What is the process for a customer to opt out of data retention or training use?

4. Who within your organization can access customer prompts or outputs? Are background checks required for those roles?

5. Where is customer data stored? List all regions and cloud providers.

6. Is customer data ever transferred outside the country of origin? Under what legal mechanism (e.g., Standard Contractual Clauses)?

7. What is your data retention period, and what is the deletion process at contract end?

---

## Section 2: Security Certifications

8. Do you hold **SOC 2 Type II**?  
   [ ] Yes — please attach current report  [ ] In progress (expected: _______)  [ ] No

9. Do you hold **ISO 27001**? If yes, what is the certification scope?  
   [ ] Yes — scope: ___________  [ ] In progress  [ ] No

10. Do you hold **CSA STAR** certification?  
    [ ] Level 1 (Self-Assessment)  [ ] Level 2 (Third-Party Audit)  [ ] No

11. Any other relevant certifications? (e.g., FedRAMP, HIPAA BAA, PCI-DSS, ISO 42001)

12. When was your last third-party penetration test? Can you share the executive summary?

---

## Section 3: AI-Specific Security

13. Have you implemented controls specifically for **prompt injection** attacks? Describe.

14. Do you perform **output filtering** or content safety checks? How are these maintained?

15. How are your model versions managed? Are customers notified before model updates that may affect behavior?

16. Has your system been **red-teamed** for adversarial inputs? By whom and when?

17. Do you have a published **model card** or **system card** documenting model behavior, limitations, and known failure modes?

18. How do you detect and respond to **abuse or misuse** of your API?

---

## Section 4: Incident Response

19. What is your **breach notification SLA**? (Hours from discovery to customer notification)

20. Have you experienced any security incidents or breaches in the **last 3 years** affecting customer data? If yes, describe.

21. What is your **vulnerability disclosure process**? Do you have a public security disclosure policy or bug bounty program?

22. What is your documented **Mean Time to Respond (MTTR)** for critical security incidents?

---

## Section 5: Access & Infrastructure

23. Is **multi-factor authentication (MFA)** enforced for all internal staff with access to customer data?

24. How is access to production systems and customer data controlled and reviewed?

25. Do you conduct regular **security awareness training** for staff?

26. What is your **patch management** process for critical vulnerabilities?

27. Describe your **business continuity and disaster recovery** capabilities. What is your documented RTO/RPO?

---

## Section 6: Contract & Compliance Requirements

28. Do you provide a **GDPR-compliant Data Processing Agreement (DPA)**?  
    [ ] Yes — standard DPA available  [ ] Yes — negotiable  [ ] No

29. Will you **contractually prohibit** using our data for model training or fine-tuning?  
    [ ] Yes  [ ] No  [ ] Negotiable

30. Do you support the **right to erasure**? What are the timelines and processes for data deletion on request?

31. Will you provide **audit rights** or accept third-party audits on request?  
    [ ] Yes  [ ] No  [ ] Subject to mutual agreement

32. Do you carry **cyber liability insurance**? What is the coverage amount?

33. Are your **sub-processors** disclosed? Will you notify us of changes to sub-processors?

---

## Section 7: Additional Information

*Use this space for any context, clarifications, or supporting documentation references.*

___________

---

## Vendor Sign-Off

By completing this questionnaire, the vendor confirms responses are accurate to the best of their knowledge.

| Field | Detail |
|-------|--------|
| Completed by | |
| Title | |
| Date | |
| Email | |

---

## Internal Use Only — Reviewer Notes

| Question # | Flag | Notes |
|------------|------|-------|
| | | |
| | | |

**Overall assessment:** [ ] Pass  [ ] Conditional  [ ] Fail  
**Linked to vendor assessment:** `ai-vendor-assessment-template.md`

---

*Template from [AI Security Portfolio](../README.md) by Tangia Stegall · Adapt freely with attribution*
