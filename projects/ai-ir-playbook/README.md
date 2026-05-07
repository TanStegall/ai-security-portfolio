# 🚨 AI Incident Response Playbook

> **IR Templates & Runbooks for AI System Security Incidents**  
> Adapted from NIST SP 800-61 with AI-specific detection, containment, and recovery procedures.

---

## AI Incidents Are Different

Traditional IR focuses on systems behaving outside their design. AI incidents can be subtler:

| Traditional IR | AI IR |
|---------------|-------|
| Clear indicators (malware, exploit) | Subtle behavioral drift |
| Binary state (compromised / clean) | Probabilistic degradation |
| Restore from backup | Retrain / revalidate model |
| One-time remediation | Ongoing monitoring required |
| Known attack patterns | Novel adversarial techniques |

---

## 📋 AI Incident Classification

### Severity Levels

**SEV-1 (Critical)** — Immediate response required
- AI agent taking unauthorized destructive actions
- Confirmed data exfiltration via LLM outputs
- Backdoored model in production
- AI system weaponized against users

**SEV-2 (High)** — Response within 1 hour
- Confirmed prompt injection causing policy violations
- AI outputting sensitive internal information
- Agent exceeding authorized permissions
- Significant model performance degradation (>20%)

**SEV-3 (Medium)** — Response within 4 hours
- Suspected data poisoning attempt
- Repeated jailbreak attempts by users
- Model evasion in security classification tasks
- Anomalous agent behavior patterns

**SEV-4 (Low)** — Response within 24 hours
- Individual prompt injection attempts (blocked)
- Minor model drift detected
- Unusual inference API usage patterns

---

## 🔄 Incident Response Lifecycle

```
DETECT → ANALYZE → CONTAIN → ERADICATE → RECOVER → LESSONS LEARNED
   ↑                                                        │
   └────────────────── Improve Controls ───────────────────┘
```

---

## Playbook 1: Prompt Injection Incident

**Trigger:** Monitoring alert — LLM output contains system prompt, credential patterns, or unexpected external URLs.

### Phase 1: Detect & Analyze (0–30 min)

```
□ Acknowledge alert and assign incident owner
□ Classify severity (SEV-1 through SEV-4)
□ Capture full conversation context:
    - User input that triggered the incident
    - Full LLM response
    - System prompt (current version)
    - Retrieved context (if RAG)
    - Timestamp, user ID, session ID
□ Determine injection type:
    - Direct (user input) → Likely SEV-3
    - Indirect via retrieved content → Likely SEV-2
    - Agent taking unauthorized actions → Likely SEV-1
□ Check for exfiltration:
    - Did output contain secrets, PII, or internal data?
    - Did agent make unexpected external requests?
```

### Phase 2: Contain (30–60 min)

```
□ If SEV-1 or SEV-2:
    - [ ] Suspend affected agent or conversation session
    - [ ] Block user if malicious actor confirmed
    - [ ] Isolate affected agent from production traffic
    - [ ] Enable enhanced logging on all related sessions
    
□ Preserve evidence:
    - [ ] Export full conversation logs
    - [ ] Capture current system prompt version
    - [ ] Record agent tool call history
    - [ ] Snapshot vector database state (if RAG involved)
```

### Phase 3: Eradicate

```
□ Identify root cause:
    - [ ] Input validation gap?
    - [ ] Prompt architecture weakness?
    - [ ] Malicious content in knowledge base?
    - [ ] Missing output filtering?
    
□ Remediate:
    - [ ] Patch input validation rules
    - [ ] Update system prompt with stronger boundaries
    - [ ] Purge and re-index affected knowledge base content
    - [ ] Update output filters
```

### Phase 4: Recover

```
□ Validation before restore:
    - [ ] Run injection test suite against patched system
    - [ ] Verify output filters catching known patterns
    - [ ] Confirm knowledge base integrity
    - [ ] Red team review (if SEV-1)
    
□ Restore:
    - [ ] Gradually restore traffic (10% → 50% → 100%)
    - [ ] Monitor error rates and anomaly detectors
    - [ ] Alert on-call if any recurrence within 24h
```

---

## Playbook 2: AI Agent Unauthorized Action

**Trigger:** Agent executes tool calls outside its authorized scope, accesses restricted data, or takes destructive actions.

### Immediate Actions (0–15 min)

```
□ KILL SWITCH: Immediately terminate agent session
□ Preserve state:
    - [ ] Full tool call log (what it tried to do)
    - [ ] Current memory / context window
    - [ ] All I/O since session start
□ Assess blast radius:
    - [ ] What data was accessed?
    - [ ] What actions were completed vs. attempted?
    - [ ] Were any external systems modified?
□ Notify: Security lead, affected system owners
```

### Investigation Checklist

```
□ How did the agent exceed its permissions?
    - [ ] Permissions were misconfigured (check YAML/policy)
    - [ ] Prompt injection caused tool misuse
    - [ ] Jailbreak removed guardrails
    - [ ] Logic error in agent orchestration
    
□ Was this targeted or opportunistic?
    - [ ] Review conversation for injection patterns
    - [ ] Check user history and authentication
    - [ ] Correlate with other anomalous sessions
```

---

## Playbook 3: Data Poisoning Suspected

**Trigger:** Model performance drops significantly, outputs become biased/manipulated, or suspicious content found in training/knowledge base.

### Detection Indicators

```
Quantitative:
- Classification accuracy drops >10% on known test set
- Output sentiment/tone shifts without config change
- Specific query patterns produce consistently wrong results
- Embedding distribution shifts in vector DB

Qualitative:
- Users report consistently wrong/misleading information
- Model refuses legitimate queries it handled before
- Outputs show unexpected bias toward specific conclusions
- "Trigger words" cause dramatically different behavior
```

### Response Steps

```
□ Freeze: Halt new content ingestion immediately
□ Snapshot: Export current model weights and knowledge base
□ Test: Run full behavioral test suite — document all failures
□ Trace: 
    - [ ] When did degradation begin? (Binary search logs)
    - [ ] What content was ingested in that window?
    - [ ] Who had ingestion access?
□ Quarantine: Remove suspect content from knowledge base
□ Validate: Re-run test suite and compare
□ Decision: Rollback model or retrain from clean checkpoint?
```

---

## 📊 IR Metrics to Track

| Metric | Target | How to Measure |
|--------|--------|----------------|
| Mean Time to Detect (MTTD) | < 15 min | Alert timestamp vs. incident start |
| Mean Time to Contain (MTTC) | < 60 min | Contain timestamp vs. detect timestamp |
| Mean Time to Recover (MTTR) | < 4 hours | Restore timestamp vs. incident start |
| Injection Block Rate | > 99% | Blocked / Total injection attempts |
| False Positive Rate | < 5% | False alerts / Total alerts |
| Exfiltration Incidents | 0 | Count per quarter |

---

## 📞 Escalation Matrix

| Severity | First Responder | Escalate To | Notify |
|----------|----------------|-------------|--------|
| SEV-1 | On-call Security Engineer | CISO + Legal | All stakeholders, affected users |
| SEV-2 | Security Engineer | Security Lead | Affected team leads |
| SEV-3 | Security Analyst | Security Engineer | Security team |
| SEV-4 | Security Analyst | — | Ticket only |

---

## 📂 Files in This Directory

```
ai-ir-playbook/
├── README.md                      # This document (overview + playbooks)
├── incident-report-template.md    # Blank IR report form
├── evidence-collection-guide.md   # What to preserve and how
├── post-incident-review.md        # PIR template
└── test-scenarios.md              # Tabletop exercise scenarios
```

---

## 🔗 References

- [NIST SP 800-61r3 — Computer Security Incident Handling Guide](https://csrc.nist.gov/publications/detail/sp/800-61/rev-3/final)
- [CISA AI Incident Response](https://www.cisa.gov/ai)
- [MITRE ATLAS Response Mitigations](https://atlas.mitre.org/mitigations/)
- [OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

---

*Part of the [AI Security Portfolio](../../README.md) by Tangia Stegall*
