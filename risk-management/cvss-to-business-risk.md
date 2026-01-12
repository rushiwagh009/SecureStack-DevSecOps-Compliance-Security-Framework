# CVSS to Business Risk Translation

> **Document Purpose**: Translate technical CVSS scores into business-understandable risk language  
> **Owner**: CISO / Risk Manager  
> **Last Updated**: January 2026

---

## 1. What is CVSS?

### 1.1 Definition

**CVSS (Common Vulnerability Scoring System)** is an industry-standard framework for assessing the **technical severity of security vulnerabilities** on a scale of 0.0 to 10.0.

**Current Version**: CVSS v3.1

### 1.2 Why CVSS Alone is Insufficient

**Technical vs. Business Perspective**:
- CVSS = Technical exploit difficulty and impact
- Business Risk = Technical severity + business context + likelihood

**Example**: A CVSS 9.8 vulnerability in a test system may have LOWER business risk than a CVSS 6.5 vulnerability in a revenue-generating production system.

---

## 2. CVSS Scoring Breakdown

### 2.1 Base Metrics

#### Attack Vector (AV)
- **Network (N)**: Remotely exploitable
- **Adjacent (A)**: Local network required
- **Local (L)**: Local access required
- **Physical (P)**: Physical access required

#### Attack Complexity (AC)
- **Low (L)**: Simple exploitation
- **High (H)**: Specialized conditions required

#### Privileges Required (PR)
- **None (N)**: No authentication
- **Low (L)**: Basic user privileges
- **High (H)**: Administrator privileges

#### User Interaction (UI)
- **None (N)**: Fully automated
- **Required (R)**: Victim must take action

#### Scope (S)
- **Unchanged (U)**: Affects only vulnerable component
- **Changed (C)**: Affects other components

#### Confidentiality/Integrity/Availability (C/I/A)
- **High (H)**: Total loss
- **Low (L)**: Some loss
- **None (N)**: No impact

---

## 3. Business Risk Translation Framework

### 3.1 Technical Severity → Business Impact

| CVSS Range | Technical Rating | Business Impact | Financial Estimate | Remediation SLA |
|------------|------------------|-----------------|-------------------|-----------------|
| **9.0-10.0** | CRITICAL | Catastrophic | >$1M | 24-48 hours |
| **7.0-8.9** | HIGH | Major | $100K-$1M | 30 days |
| **4.0-6.9** | MEDIUM | Moderate | $10K-$100K | 90 days |
| **0.1-3.9** | LOW | Minor | <$10K | Next release (180 days) |

### 3.2 Context Multipliers

Business risk = CVSS Score × Context Multipliers

**Context Factors**:

1. **Asset Criticality**:
   - Customer-facing production: 1.5x multiplier
   - Internal production: 1.2x
   - Development/test: 0.7x
   - Lab/research: 0.3x

2. **Data  Sensitivity**:
   - PII/PHI/financial data: 1.5x
   - Confidential business data: 1.2x
   - Public data: 0.8x

3. **Internet Exposure**:
   - Publicly accessible: 1.3x
   - Internal only: 1.0x
   - Air-gapped: 0.7x

4. **Exploit Availability**:
   - Public exploit exists: 1.4x
   - Proof-of-concept available: 1.2x
   - No known exploit: 1.0x

5. **Compensating Controls**:
   - No controls: 1.3x
   - Some controls: 1.0x
   - Multiple layers: 0.8x

**Example Calculation**:
```
CVSS 8.5 (High) vulnerability in customer-facing system with PII:
Business Risk = 8.5 × 1.5 (production) × 1.5 (PII) = 19.1
→ Effectively CRITICAL business risk
```

---

## 4. Compliance Checkpoint Integration

### 4.1 CVSS Critical (9.0-10.0) → Compliance Requirements

**ISO 27001:2022**:
- **A.16.1**: Information security incident management
  - *Requirement*: Immediate escalation, incident declared
  - *Evidence*: Incident log, management notification, remediation plan
  
- **A.8.8**: Management of technical vulnerabilities
  - *Requirement*: Urgent patch deployment
  - *Evidence*: Patch status, testing results, deployment logs

**SOC 2**:
- **CC7.3**: Risk mitigation activities
  - *Requirement*: Immediate risk treatment
  - *Evidence*: Risk register update, mitigation actions, timeline

- **CC7.4**: Incident response
  - *Requirement*: Incident procedures activated
  - *Evidence*: IR playbook execution, communication logs

**GDPR**:
- **Article 33**: Personal data breach notification
  - *Requirement*: If PII affected, notify DPA within 72 hours
  - *Evidence*: Breach assessment, notification sent

- **Article 32**: Security of processing
  - *Requirement*: Demonstrate risk-appropriate measures
  - *Evidence*: Control implementation, testing

**DPDPA (India)**:
- **Section 8**: Security safeguards
  - *Requirement*: Reasonable security measures implemented
  - *Evidence*: Technical controls, remediation timeline

- **Section 6**: Data breach notification
  - *Requirement*: Notify Data Protection Board and affected individuals
  - *Evidence*: Notification records, impact assessment

---

### 4.2 CVSS High (7.0-8.9) → Compliance Requirements

**ISO 27001:2022**:
- **A.12.6**: Technical vulnerability management
  - *Requirement*: Risk assessment, treatment plan
  - *Evidence*: CVSS scoring, remediation roadmap

**SOC 2**:
- **CC7.2**: System monitoring
  - *Requirement*: Detection and alerting
  - *Evidence*: Monitoring logs, alerts generated

**GDPR**:
- **Article 32**: Appropriate technical measures
  - *Requirement*: Security measures proportionate to risk
  - *Evidence*: Control selection justification

**DPDPA**:
- **Section 8**: Implement safeguards based on risk
  - *Evidence*: Risk-based security measures

---

### 4.3 Compliance Violation Severity Mapping

| Compliance Gap | ISO 27001 Impact | SOC 2 Impact | GDPR Fine Risk | DPDPA Penalty Risk |
|----------------|------------------|--------------|----------------|--------------------|
| **Critical CVSS unpatched** | Major non-conformity | Modified opinion (Type II) | Up to €20M or 4% | Per Section 33 penalties |
| **High CVSS unpatched >SLA** | Minor non-conformity | Qualified opinion | Possible fine | Compliance notice |
| **Medium CVSS tracked** | Observation | No impact (if managed) | No fine (good faith) | No action |

---

## 5. Financial Impact Estimation

### 5.1 Data Breach Cost Components

**Per-Record Cost** (Industry Average):
- Healthcare: $429/record
- Financial: $210/record
- Technology: $183/record
- Retail: $165/record

**Additional Costs**:
- **Detection & Escalation**: $200K-$500K
- **Notification**: $50-$100 per affected individual
- **Post-Breach Response**: $500K-$2M
- **Legal Fees**: $1M-$5M
- **Regulatory Fines**: Variable (GDPR: up to €20M or 4%)
- **Reputation Damage**: 20-30% customer churn

**Example**:
```
SQL Injection (CVSS 9.8) in customer database with 100,000 records:
- Breach cost: 100,000 × $180 = $18M
- Notification: 100,000 × $75 = $7.5M
- Response & legal: $3M
- GDPR fine: €10M (~$11M)
- Total: ~$40M+ potential cost
```

---

## 6. Risk Scenarios by CVSS

### 6.1 CRITICAL (CVSS 9.0-10.0)

**Example**: SQL Injection (CVSS 9.8)

**Business Scenario**:
- Attacker extracts all customer database
- 100,000 customer PII records exposed
- Credentials compromised

**Business Impact**:
- **Financial**: $20M-$50M (breach costs, fines)
- **Operational**: System taken offline for forensics (3-7 days)
- **Reputational**: Front-page news, customer churn
- **Legal**: Class-action lawsuits, regulatory investigations
- **Compliance**: GDPR Article 33 notification, potential €20M fine

**Stakeholder Impact**:
- Customers: Identity theft risk
- Investors: Stock price drop
- Board: Liability, governance questions

---

### 6.2 HIGH (CVSS 7.0-8.9)

**Example**: Stored XSS (CVSS 8.8)

**Business Scenario**:
- Attacker injects malicious JavaScript
- User sessions hijacked
- Credentials stolen via keylogging

**Business Impact**:
- **Financial**: $500K-$2M (incident response, user remediation)
- **Operational**: Feature disabled until fix deployed
- **Reputational**: Trust issues, negative reviews
- **Legal**: Breach notification, possible lawsuits

---

### 6.3 MEDIUM (CVSS 4.0-6.9)

**Example**: Information Disclosure (CVSS 5.3)

**Business Scenario**:
- Internal file paths exposed in error messages
- System architecture revealed

**Business Impact**:
- **Financial**: <$100K (developer time to fix)
- **Operational**: Minimal
- **Reputational**: None (unless exploited further)
- **Legal**: None directly

**Risk**: Enables reconnaissance for future attacks

---

## 7. Executive Communication Templates

### 7.1 CRITICAL Risk Communication

**Subject**: URGENT: Critical Security Vulnerability Requiring Immediate Action

**Summary**:
We have identified a [VULNERABILITY TYPE] affecting [SYSTEM]. This vulnerability has a CVSS score of [X.X] (CRITICAL) and could result in:
- [PRIMARY IMPACT, e.g., complete database exposure]
- Potential cost: $[AMOUNT]
- Regulatory notification required: [YES/NO]

**Immediate Actions**:
- System [STATUS - e.g., taken offline, monitoring increased]
- Remediation underway, ETA: [TIMELINE]
- Incident response team activated

**Business Impact**:
- [CUSTOMER/REVENUE/OPERATIONS IMPACT]

---

### 7.2 HIGH Risk Communication

**Subject**: High-Priority Security Issue - Action Required within 30 Days

[More measured tone, focus on managed response]

---

## 8. Decision Trees

### 8.1 Remediation Priority Decision

```
Is CVSS ≥ 9.0?
├─ YES → IMMEDIATE (24-48 hours)
└─ NO
    │
    Is CVSS ≥ 7.0?
    ├─ YES
    │   │
    │   Is system production?
    │   ├─ YES → HIGH PRIORITY (30 days)
    │   └─ NO → MEDIUM PRIORITY (90 days)
    │
    └─ NO → Is CVSS ≥ 4.0?
        ├─ YES → LOW PRIORITY (180 days)
        └─ NO → INFORMATIONAL (Monitor)
```

---

## 9. Related Documents

- [Risk Register](risk-register.md)
- [Severity Classification](severity-classification.md)
- [Risk Appetite Statement](../docs/GOVERNANCE/risk-appetite-statement.md)
- [Incident Response Plan](../docs/ARCHITECTURE/incident-response-plan.md)

---

**Owner**: CISO  
**Contributors**: Risk Manager, Finance, Legal  
**Review Cycle**: Annual or upon major incident
