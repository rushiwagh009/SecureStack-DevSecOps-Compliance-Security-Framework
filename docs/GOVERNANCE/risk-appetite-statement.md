# Risk Appetite Statement

> **Document Control**  
> Version: 1.0  
> Effective Date: January 2026  
> Review Cycle: Annual  
> Owner: Chief Information Security Officer (CISO)

---

## 1. What is Risk Appetite?

### 1.1 Definition

**Risk Appetite** is the amount and type of risk that the organization is willing to accept in pursuit of business objectives. It defines the boundaries between acceptable and unacceptable risk exposure.

### 1.2 Purpose

This statement establishes:
- Quantitative and qualitative risk tolerance levels
- Decision-making criteria for risk acceptance
- Investment thresholds for risk mitigation
- Escalation triggers for risk management

---

## 2. Why Risk Appetite Matters

### 2.1 Strategic Value

- **Informed Decision-Making**: Consistent criteria for security investments
- **Resource Optimization**: Focus on risks exceeding appetite
- **Compliance Alignment**: Demonstrate to auditors and regulators
- **Stakeholder Confidence**: Clear risk governance

### 2.2 Compliance Framework Alignment

| Framework | Risk Appetite Requirement |
|-----------|---------------------------|
| **ISO 27001:2022** | Clause 6.1.2 (Information security risk assessment), A.5.2 (Risk assessment) |
| **SOC 2** | CC3.2 (Risk identification and assessment), CC7.3 (Risk mitigation) |
| **GDPR** | Article 32 (Risk-appropriate security measures) |
| **DPDPA** | Section 8 (Reasonable security safeguards) |

---

## 3. When Risk Appetite is Assessed

### 3.1 Assessment Triggers

**Regular Reviews:**
- Quarterly risk register reviews
- Annual strategic planning cycle
- Post-incident risk reassessment

**Event-Driven Reviews:**
- New system deployments
- Significant vulnerability discoveries (CVSS ≥ 7.0)
- Regulatory requirement changes
- Major business model changes

---

## 4. Where Risk Appetite Applies

### 4.1 Scope

**Asset Categories:**
- Information systems and data
- Infrastructure (lab and production)
- Cloud services and platforms
- Third-party vendor risks
- Human resources (insider threats)

**Risk Domains:**
- Cybersecurity threats
- Compliance violations
- Data breaches
- Availability disruptions
- Reputational damage

---

## 5. How Risk Appetite is Defined

### 5.1 Risk Tolerance Levels

#### 5.1.1 Quantitative Risk Appetite

| Risk Metric | Appetite (Acceptable) | Tolerance (Maximum) | Unacceptable |
|-------------|----------------------|---------------------|--------------|
| **CVSS Critical (9.0-10.0)** | 0 findings | 0 findings (Zero tolerance) | Any critical finding |
| **CVSS High (7.0-8.9)** | ≤ 2 findings | ≤ 5 findings | > 5 findings |
| **CVSS Medium (4.0-6.9)** | ≤ 10 findings | ≤ 20 findings | > 20 findings |
| **CVSS Low (0.1-3.9)** | ≤ 30 findings | ≤ 50 findings | > 50 findings |
| **Compliance Violations** | 0 critical gaps | 0 critical gaps | Any critical gap |
| **Data Breach Probability** | < 5% annually | < 10% annually | ≥ 10% |
| **System Downtime (Security)** | < 0.1% (9 hours/year) | < 0.5% (44 hours/year) | ≥ 0.5% |

#### 5.1.2 Qualitative Risk Appetite

**Acceptable Risks:**
- ✅ Low-impact vulnerabilities with lengthy remediation cycles (90+ days)
- ✅ Informational findings from security scans
- ✅ Risks with effective compensating controls
- ✅ Business-justified exceptions with time limits and monitoring

**Unacceptable Risks:**
- ❌ Any risk to customer/user data confidentiality
- ❌ Known exploitable vulnerabilities without mitigation plan
- ❌ Non-compliance with ISO 27001, SOC 2, GDPR, or DPDPA
- ❌ Unauthorized access to production systems
- ❌ Unencrypted sensitive data in transit or at rest

### 5.2 Risk Acceptance Criteria

#### Decision Framework

```
┌─────────────────────────────────────────────────┐
│ Is risk within appetite thresholds?             │
│ └─ YES: Monitor and Continue  │ NO: Continue ▼  │
└─────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────┐
│ Can risk be mitigated to within appetite?       │
│ └─ YES: Implement mitigation  │ NO: Continue ▼  │
└─────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────┐
│ Is cost of mitigation > business impact?        │
│ └─ YES: Consider acceptance   │ NO: Mitigate    │
└─────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────┐
│ Are compensating controls feasible?             │
│ └─ YES: Accept with controls  │ NO: Escalate    │
└─────────────────────────────────────────────────┘
```

#### Approval Authority by Risk Level

| Risk Level | Business Impact | Approval Authority |
|------------|----------------|-------------------|
| **Critical** | Catastrophic (>$1M, regulatory action) | CTO + CISO (Mandatory mitigation) |
| **High** | Major ($100K-$1M, compliance violation) | CISO (Mitigation plan required) |
| **Medium** | Moderate ($10K-$100K, operational impact) | CISO (Risk acceptance allowed with compensation) |
| **Low** | Minor (<$10K, minimal impact) | Security Manager |

---

## 6. Who is Involved in Risk Decisions

### 6.1 Risk Governance Roles

**Chief Information Security Officer (CISO)**
- **What**: Primary risk decision authority for medium/high risks
- **Why**: Security program ownership and technical expertise
- **How**: Review risk register, approve mitigations or acceptances

**Chief Technology Officer (CTO)**
- **What**: Final authority for critical risks and risk appetite changes
- **Why**: Ultimate accountability for technology and security
- **How**: Quarterly risk briefings, critical risk approvals

**Security Team**
- **What**: Risk identification, assessment, and remediation
- **Why**: Technical analysis and operational execution
- **How**: VAPT activities, risk scoring (CVSS), mitigation implementation

**Compliance Officer**
- **What**: Regulatory risk assessment and compliance gap analysis
- **Why**: Ensure risk appetite aligns with legal obligations
- **How**: Control testing, audit coordination, gap reporting

**Business Stakeholders**
- **What**: Business impact assessment for security decisions
- **Why**: Balance security and operational needs
- **How**: Impact analysis consultation, major change approvals

---

## 7. Risk Treatment Strategies

### 7.1 Mitigation Strategy

**When Used**: Risk exceeds appetite and mitigation is cost-effective

**Examples:**
- Patching critical vulnerabilities immediately
- Implementing multi-factor authentication (MFA)
- Deploying web application firewalls (WAF)
- Encrypting sensitive data

**SLA by Risk Level:**
- Critical: 24-48 hours
- High: 30 days
- Medium: 90 days
- Low: Next maintenance cycle (180 days)

### 7.2 Acceptance Strategy

**When Used**: Risk within appetite OR cost of mitigation > risk impact

**Requirements:**
- Documented business justification
- Compensating controls evaluation
- Time-limited (maximum 12 months)
- Quarterly risk review
- Appropriate authority approval

**Compliance Mapping:**
- ISO 27001 Clause 6.1.3 (Risk treatment)
- SOC 2 CC3.4 (Risk treatment decisions)

### 7.3 Transfer Strategy

**When Used**: Risk can be shared with third parties

**Examples:**
- Cyber insurance for breach response costs
- Cloud provider shared responsibility model
- Third-party security services (SOC, managed detection)

**Requirements:**
- Vendor security assessment
- Contractual SLAs and liability clauses
- Regular vendor risk reviews

### 7.4 Avoidance Strategy

**When Used**: Risk completely outside appetite with no feasible mitigation

**Examples:**
- Decommissioning insecure legacy systems
- Discontinuing services with unacceptable risks
- Blocking high-risk integrations

---

## 8. Risk Appetite Monitoring

### 8.1 Key Risk Indicators (KRIs)

**Leading Indicators** (Predictive):
- Number of unpatched critical vulnerabilities
- Time to patch (P50, P90, P99)
- Phishing simulation failure rate
- Failed access control reviews

**Lagging Indicators** (Historical):
- Number of security incidents
- Audit findings severity distribution
- Compliance violation count
- Mean time to detect (MTTD) and respond (MTTR)

### 8.2 Reporting and Escalation

**Monthly**: KRI dashboard to CISO  
**Quarterly**: Risk appetite vs. actual exposure to Security Committee  
**Immediate**: Any risk exceeding tolerance triggers escalation

**Escalation Thresholds:**
- Any critical (CVSS 9.0+) vulnerability discovered
- Any compliance violation identified
- Actual incident exceeding defined impact thresholds
- Risk appetite breach in any category

---

## 9. Regulatory Compliance Considerations

### 9.1 Zero-Tolerance Compliance Risks

**Mandatory Compliance** (No acceptance allowed):

**ISO 27001 Critical Controls:**
- A.5.1: Information security policies
- A.8.10: Information deletion
- A.8.11: Data masking
- A.8.24: Use of cryptography

**SOC 2 Trust Principles:**
- CC1: Control environment
- CC2: Communication and information
- CC6.1: Logical access controls

**GDPR Fundamental Requirements:**
- Article 5: Data processing principles
- Article 32: Security of processing
- Article 33: Breach notification (72 hours)

**DPDPA Core Obligations:**
- Section 8: Security safeguards
- Section 6: Data breach notification

### 9.2 Compliance Risk Mitigation Priority

1. **Priority 1** (Zero tolerance): Immediate mitigation required
2. **Priority 2** (High compliance risk): 30-day SLA
3. **Priority 3** (Moderate compliance risk): 90-day SLA

---

## 10. Business Context and Exceptions

### 10.1 Business-Justified Risk Acceptance

In rare cases, business requirements may justify temporary risk acceptance exceeding normal appetite.

**Criteria for Exception:**
- Clear business value exceeding risk cost
- Time-limited (maximum 90 days)
- Compensating controls implemented
- Enhanced monitoring during exception period
- Executive approval (CTO + CISO)

**Example Scenario:**
- Critical business deadline requiring use of legacy system
- Compensating controls: Network segmentation, enhanced logging, limited access
- Exception expires with system migration timeline

### 10.2 Appetite Adjustment Process

If business requirements consistently conflict with risk appetite:

1. **Assess**: Analyze pattern of exceptions
2. **Consult**: Engage stakeholders on business needs vs. security
3. **Propose**: Draft risk appetite adjustment with rationale
4. **Approve**: CTO approval required for appetite changes
5. **Update**: Revise this document and communicate changes

---

## 11. Related Documents

- [Information Security Charter](information-security-charter.md)
- [Information Security Policy](security-policy.md)
- [Risk Management Framework](../../risk-management/risk-register.md)
- [CVSS to Business Risk Translation](../../risk-management/cvss-to-business-risk.md)

---

## 12. Review and Approval

**Statement Approved By:**  
Chief Technology Officer (CTO)  
Date: January 2026

**CISO Endorsement:**  
Chief Information Security Officer  
Date: January 2026

**Next Review Date**: January 2027

---

**Version History:**

| Version | Date | Changes | Approver |
|---------|------|---------|----------|
| 1.0 | January 2026 | Initial risk appetite definition | CTO |

---

**Contact**: CISO Office  
**Risk Escalation**: security-risk@organization.example
