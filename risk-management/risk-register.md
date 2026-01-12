# Risk Register

> **Document Control**  
> Version: 1.0  
> Owner: Chief Information Security Officer (CISO)  
> Last Updated: January 2026  
> Review Frequency: Quarterly

---

## 1. What is a Risk Register?

### 1.1 Definition

The **Risk Register** is a comprehensive **repository of identified cybersecurity risks** with assessment, treatment, and monitoring information. It serves as the central tool for enterprise risk management.

### 1.2 Purpose

- Centralized risk tracking and management
- Prioritization of security investments
- Compliance evidence for audits
- Executive risk reporting
- Treatment progress monitoring

---

## 2. Why Risk Management Matters

### 2.1 Business Value

- **Informed Decision-Making**: Data-driven security investments
- **Compliance**: Mandatory for ISO 27001, SOC 2
- **Stakeholder Confidence**: Demonstrates risk oversight
- **Resource Optimization**: Focus on highest-impact risks

### 2.2 Compliance Requirements

| Framework | Risk Management Requirements |
|-----------|------------------------------|
| **ISO 27001:2022** | Clause 6.1 (Risk assessment and treatment) - MANDATORY |
| **SOC 2** | CC3.2 (Risk identification), CC7.3 (Risk mitigation) |
| **GDPR** | Article 32 (Risk-appropriate security) |
| **DPDPA** | Section 8 (Reasonable security - risk-based) |

---

## 3. Risk Register Template

### 3.1 Risk Entry Structure

Each risk documented with:

| Field | Description |
|-------|-------------|
| **Risk ID** | Unique identifier (e.g., RISK-WEB-001) |
| **Risk Category** | Web/Network/Cloud/Process/Physical |
| **Risk Title** | Short descriptive name |
| **Threat** | What could cause harm |
| **Vulnerability** | What weakness allows exploitation |
| **Asset** | What is at risk |
| **CVSS Score** | Technical severity (if applicable) |
| **Business Impact** | Financial/Operational/Reputational |
| **Likelihood** | Probability of occurrence (1-5) |
| **Impact Rating** | Severity of consequences (1-5) |
| **Inherent Risk** | Risk before controls (Likelihood × Impact) |
| **Current Controls** | Existing mitigations |
| **Residual Risk** | Risk after controls |
| **Risk Level** | Critical/High/Medium/Low |
| **Treatment** | Mitigate/Accept/Transfer/Avoid |
| **Owner** | Accountable individual |
| **Target Closure** | Remediation deadline |
| **Status** | Open/In Progress/Closed |
| **Compliance Mapping** | ISO/SOC 2/GDPR/DPDPA |

---

## 4. Current Risk Register (Sample Entries)

### RISK-WEB-001: SQL Injection in User Input Fields

**Category**: Web Application Security  
**Discovery Date**: January 2026

#### What (Risk Description)
**Threat**: Malicious actors exploiting SQL injection vulnerabilities  
**Vulnerability**: Lack of input validation and parameterized queries  
**Asset**: User database, application data, credentials

#### Where
**Location**: DVWA application, user ID parameter  
**URL**: `/vulnerabilities/sqli/`  
**Parameter**: `id` (GET)

#### Why (Impact)
**Technical Impact**:
- Confidentiality: HIGH (full database read)
- Integrity: HIGH (data modification)
- Availability: MEDIUM (potential DoS)

**Business Impact**:
- Data breach → GDPR/DPDPA violations
- Regulatory fines: Up to €20M (GDPR)
- Reputational damage
- Customer trust erosion

####  When
**First Identified**: January 2026  
**VAPT Test**: Web Application Security Assessment

#### How (Exploitation)
- Attack vector: HTTP GET parameter injection
- **CVSS v3.1 Score**: 9.8 (CRITICAL)
- **Vector**: `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`

#### Risk Assessment

| Metric | Before Controls | After Controls |
|--------|-----------------|----------------|
| **Likelihood** | 5 (Very High - easily exploitable) | 2 (Low - with param queries) |
| **Impact** | 5 (Critical - full DB compromise) | 5 (Still critical if exploited) |
| **Inherent Risk Score** | 25 (CRITICAL) | N/A |
| **Residual Risk Score** | N/A | 10 (MEDIUM) |
| **Risk Level** | CRITICAL | MEDIUM |

#### Current Controls
- ⚠️ NONE (Lab environment - intentionally vulnerable for testing)

#### Planned Treatment
**Strategy**: MITIGATE

**Remediation Actions**:
1. Implement parameterized queries (prepared statements)
2. Input validation (whitelist, type checking)
3. Least privilege database access
4. Web Application Firewall (WAF)
5. Code review and SAST integration

**Timeline**: 48 hours (per critical risk SLA)

#### Compliance Mapping

**ISO 27001:2022**:
- A.8.8: Management of technical vulnerabilities
- A.14.2.1: Secure development policy
- A.14.2.5: Secure system engineering principles

**SOC 2**:
- CC6.1: Logical access controls
- CC7.1: Quality monitoring

**GDPR**:
- Article 32: Security of processing (technical measures)
- Article 33: Personal data breach notification (if exploitation occurs)

**DPDPA**:
- Section 8: Security safeguards

#### Who
**Risk Owner**: CISO  
**Remediation Owner**: Development Team  
**Status**: Documented (Lab Finding)

---

### RISK-WEB-002: stored XSS in feedback/comment Fields

**Category**: Web Application Security  
**Discovery Date**: January 2026

#### What
**Threat**: Attackers injecting malicious JavaScript into stored content  
**Vulnerability**: Inadequate output encoding and content filtering  
**Asset**: User sessions, credentials (session cookies), user data

#### Where
**Location**: DVWA Stored XSS module  
**Field**: Guestbook/message input

#### Why (Impact)
**Technical Impact**:
- Session hijacking
- Credential theft (keylogging)
- Malware distribution
- Defacement

**Business Impact**:
- User account compromise
- Phishing attacks against users
- Reputational damage

#### How
- **CVSS v3.1 Score**: 8.8 (HIGH)
- **Vector**: `CVSS:3.1/AV:N/AC:L/PR:L/UI:R/S:C/C:H/I:H/A:N`

#### Risk Assessment

| Metric | Before Controls | After Controls |
|--------|-----------------|----------------|
| **Likelihood** | 4 (High) | 2 (Low) |
| **Impact** | 4 (High) | 4 (High if bypassed) |
| **Inherent Risk** | 16 (HIGH) | 8 (MEDIUM) |

#### Planned Treatment
**Strategy**: MITIGATE

**Actions**:
1. Output encoding (HTML entity encoding)
2. Content Security Policy (CSP)
3. Input sanitization
4. HTTPOnly cookie flags

**Timeline**: 30 days (High risk SLA)

#### Compliance Mapping
- ISO 27001: A.14.2.1 (Secure development)
- SOC 2: CC6.1
- GDPR: Article 32

---

### RISK-NET-001: Exposed Administration Ports

**Category**: Network Security  
**Discovery Date**: January 2026

#### What
**Threat**: Unauthorized access to management interfaces  
**Vulnerability**: SSH (22), RDP (3389), database ports exposed to internet  
**Asset**: Server administrative access, database

#### Where
**Scope**: Lab network perimeter assessment

#### Why (Impact)
- Remote code execution
- Privilege escalation
- Data exfiltration
- System compromise

#### How
- **CVSS Score**: 9.1 (CRITICAL if weak auth)
- Attack surface: Network-accessible admin services

#### Risk Assessment

| Metric | Value |
|--------|-------|
| **Likelihood** | 5 (Always exposed = always at risk) |
| **Impact** | 5 (Full system compromise) |
| **Inherent Risk** | 25 (CRITICAL) |

#### Treatment
**Strategy**: MITIGATE

**Actions**:
1. Network segmentation (management VLAN)
2. Firewall rules (deny-all, allow specific IPs)
3. VPN/jump box for admin access
4. MFA on all admin accounts
5. Port knocking or change default ports

**Timeline**: 7 days

#### Compliance
- ISO 27001: A.8.20 (Network security), A.8.22 (Segregation)
- SOC 2: CC6.6

---

### RISK-CLOUD-001: Overly Permissive IAM Policies

**Category**: Cloud Security  
**Discovery Date**: January 2026

#### What
**Threat**: Privilege escalation, lateral movement  
**Vulnerability**: IAM policies granting excessive permissions  
**Asset**: Cloud resources, data

#### Why (Impact)
- Unauthorized resource access
- Data  breach
- Cost abuse
- Compliance violations

#### Risk Assessment

| Metric | Value |
|--------|-------|
| **Likelihood** | 3 (Medium - requires access) |
| **Impact** | 4 (High - broad access) |
| **Inherent Risk** | 12 (HIGH) |

#### Treatment
**Strategy**: MITIGATE

**Actions**:
1. Least privilege review
2. Just-in-time access
3. Regular access audits
4. IAM policy cleanup

**Timeline**: 90 days

#### Compliance
- ISO 27001: A.5.15 (Access control), A.8.2 (Privileged access)
- SOC 2: CC6.1, CC6.2
- GDPR: Article 32 (Access controls)
- DPDPA: Section 8

---

### RISK-PROC-001: Lack of Security Awareness Training

**Category**: Process/People  
**Discovery Date**: January 2026

#### What
**Threat**: Phishing, social engineering, insider threats  
**Vulnerability**: Untrained staff susceptible to attacks  
**Asset**: Credentials, sensitive data, systems

#### Why (Impact)
- Phishing success → credential compromise
- Malware infection
- Data leakage
- Insider threats

#### Risk Assessment

| Metric | Value |
|--------|-------|
| **Likelihood** | 4 (Phishing is ubiquitous) |
| **Impact** | 4 (Credential compromise) |
| **Inherent Risk** | 16 (HIGH) |

#### Treatment
**Strategy**: MITIGATE

**Actions**:
1. Quarterly security awareness training (100% attendance)
2. Phishing simulations
3. Incident reporting procedures
4. Security champions program

**Timeline**: 60 days

#### Compliance
- ISO 27001: A.6.3 (Information security awareness)
- SOC 2: CC1.4 (Demonstrates commitment)

---

## 5. Risk Matrix

### 5.1 Likelihood Scale

| Level | Description | Probability |
|-------|-------------|-------------|
| **5 - Very High** | Expected to occur | >75% |
| **4 - High** | Likely to occur | 50-75% |
| **3 - Medium** | Possible | 25-50% |
| **2 - Low** | Unlikely | 10-25% |
| **1 - Very Low** | Rare | <10% |

### 5.2 Impact Scale

| Level | Financial | Operational | Compliance |
|-------|-----------|-------------|------------|
| **5 - Critical** | >$1M | Major disruption | Regulatory action |
| **4 - High** | $100K-$1M | Significant impact | Violation |
| **3 - Medium** | $10K-$100K | Moderate impact | Gap identified |
| **2 - Low** | $1K-$10K | Minor impact | Observation |
| **1 - Very Low** | <$1K | Negligible | No impact |

### 5.3 Risk Heat Map

```
Impact ↑
5  │  5   10   15   20   25
4  │  4    8   12   16   20
3  │  3    6    9   12   15
2  │  2    4    6    8   10
1  │  1    2    3    4    5
   └─────────────────────────→ Likelihood
      1    2    3    4    5

Legend:
20-25: CRITICAL (Red) - Immediate action
15-19: HIGH (Orange) - 30 days
8-14: MEDIUM (Yellow) - 90 days
1-7: LOW (Green) - Monitor
```

---

## 6. Risk Treatment Strategies

### 6.1 Decision Framework

**MITIGATE** (Most common):
- Implement controls to reduce likelihood or impact
- Target: Reduce to within risk appetite

**ACCEPT**:
- Risk within appetite OR
- Cost of mitigation > risk impact
- Requires: Documentation, approval, monitoring

**TRANSFER**:
- Cyber insurance
- Cloud shared responsibility
- Third-party services

**AVOID**:
- Eliminate the risk source
- Decommission insecure systems

---

## 7. Monitoring and Reporting

### 7.1 Key Risk Indicators (KRIs)

| KRI | Target | Current |
|-----|--------|---------|
| Critical vulnerabilities (CVSS 9.0+) | 0 | TBD |
| High vulnerabilities (CVSS 7.0-8.9) | ≤2 | TBD |
| Mean Time to Remediate (MTTR) - Critical | ≤48 hours | TBD |
| Risk register review frequency | Quarterly | On Track |
| Compliance | gap closure | 100% of critical | TBD |

### 7.2 Reporting

**Monthly**: KRI dashboard to CISO  
**Quarterly**: Full risk register review with Security Committee  
**Annual**: Risk management effectiveness review

---

## 8. Related Documents

- [CVSS to Business Risk Translation](cvss-to-business-risk.md)
- [Severity Classification](severity-classification.md)
- [Remediation Planning](remediation-planning.md)
- [Risk Appetite Statement](../docs/GOVERNANCE/risk-appetite-statement.md)

---

**Risk Register Owner**: CISO  
**Next Review**: Quarterly (April 2026)
