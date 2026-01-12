# SOC 2 Compliance Framework

> **Standard**: SOC 2 (Service Organization Control 2) - Trust Services Criteria  
> **Authority**: American Institute of CPAs (AICPA)  
> **Checklist**: [SOC2 CheckPoints.xlsx](SOC2%20compliance/SOC2%20CheckPoints.xlsx)  
> **Owner**: Chief Information Security Officer (CISO)  
> **Last Updated**: January 2026

---

## 1. What is SOC 2?

### 1.1 Definition

**SOC 2 (Service Organization Control 2)** is an auditing procedure developed by the AICPA that ensures **service providers securely manage customer data** to protect the interests and privacy of their clients. It evaluates an organization's information systems based on **five Trust Services Criteria**.

### 1.2 SOC 2 vs. SOC 1

| Aspect | SOC 1 | SOC 2 |
|--------|-------|-------|
| **Purpose** | Financial reporting controls | Security, availability, confidentiality controls |
| **Audience** | Financial auditors | Security-conscious customers, prospects |
| **Focus** | Impact on client financial statements | Operational security and data protection |
| **Typical Users** | Payroll, billing, transaction processing services | SaaS, cloud, hosting, managed services |

**This organization requires**: **SOC 2** (not SOC 1)

### 1.3 Trust Services Criteria (TSC)

SOC 2 evaluates organizations based on five principles:

#### Common Criteria (CC) - Mandatory for All SOC 2 Audits

**100+ control points across 8 categories**:

1. **CC1: Control Environment** (COSO framework)
   - Demonstrates commitment to integrity and ethical values
   - Board independence and oversight
   - Management structure and responsibilities
   - Competence and accountability

2. **CC2: Communication and Information**
   - Internal communication of security responsibilities
   - External communication with stakeholders
   - Quality information for decision-making

3. **CC3: Risk Assessment**
   - Identification of risks
   - Risk analysis (likelihood and impact)
   - Fraud risk assessment
   - Changes that could impact controls

4. **CC4: Monitoring Activities**
   - Ongoing and separate evaluations
   - Communication of control deficiencies
   - Independent audits

5. **CC5: Control Activities**
   - Selection and development of control activities
   - Technology controls
   - Policies and procedures deployment

6. **CC6: Logical and Physical Access Controls**
   - **CC6.1**: Logical access restrictions
   - **CC6.2**: Privileged access management
   - **CC6.3**: Access removal upon termination
   - **CC6.4**: Physical access restrictions
   - **CC6.5**: Data classification and handling
   - **CC6.6**: Network security
   - **CC6.7**: Transmission security (encryption)
   - **CC6.8**: Authentication and authorization

7. **CC7: System Operations**
   - **CC7.1**: Quality assurance and testing
   - **CC7.2**: Monitoring and detection
   - **CC7.3**: Incident response
   - **CC7.4**: Incident management
   - **CC7.5**: Recovery and continuity

8. **CC8: Change Management**
   - **CC8.1**: Change management procedures
   - **CC8.2**: Change authorization and testing

#### Additional Criteria (Optional)

**Security** (Mandatory for most SOC 2 audits):
- Protection against unauthorized access (physical and logical)
- Already covered substantially by Common Criteria CC6

**Availability**:
- System operational and usable as committed
- Business continuity and disaster recovery
- SLA monitoring (uptime, performance)

**Processing Integrity**:
- System processing is complete, valid, accurate, timely, authorized
- Quality control, data validation, error handling

**Confidentiality**:
- Information designated as confidential is protected
- Encryption, NDAs, access controls for confidential data

**Privacy**:
- Personal information collected, used, retained, disclosed per commitments
- GDPR/CCPA/DPDPA alignment
- Generally requires separate Privacy examination

**Most Common SOC 2 Reports**: Security + Availability

---

### 1.4 SOC 2 Type I vs. Type II

| Type | Description | Audit Period | Value |
|------|-------------|--------------|-------|
| **Type I** | Design evaluation at a point in time | Snapshot (1 day) | Proves controls are designed properly |
| **Type II** | Design + operational effectiveness over time | 3-12 months (typically 6-12) | **GOLD STANDARD** - Proves controls work consistently |

**Recommendation**: Pursue **Type II** for maximum credibility

---

## 2. Why SOC 2 Matters

### 2.1 Business Necessity

**Customer Requirements**:
- **B2B SaaS**: 80%+ of enterprise customers require SOC 2
- **Contract Prerequisite**: Many RFPs mandate SOC 2 Type II
- **Sales Blocker**: Lack of SOC 2 can eliminate you from enterprise deals

**Competitive Advantage**:
- Market differentiation in crowded SaaS landscape
- Premium pricing justification (security = value)
- Faster sales cycles (reduces security questionnaire burden)

**Trust and Credibility**:
- Independent third-party validation
- Demonstrates operational maturity
- Reduces customer perceived risk

### 2.2 Financial Impact

**Positive ROI**:
- **Revenue Enablement**: Access to enterprise market (avg. 30% revenue increase post-SOC 2)
- **Sales Efficiency**: 40-50% reduction in security questionnaire time
- **Higher Valuations**: Investors value SOC 2 compliance (10-15% valuation premium)
- **Insurance**: Better cyber insurance rates and coverage

**Cost of Non-Compliance**:
- Lost enterprise deals (avg. $250K+ per lost opportunity)
- Extended sales cycles (3-6 months additional due diligence)
- Customer churn (security-conscious customers leave for compliant competitors)

### 2.3 Organizational Significance

**Operational Excellence**:
- Formalizes security and operational processes
- Identifies control gaps and weaknesses
- Drives continuous improvement culture
- Reduces incidents through proactive controls

**Compliance Synergies**:
- Significant overlap with ISO 27001 (~70%)
- Aligns with GDPR, HIPAA, PCI DSS requirements
- Reduces multi-framework audit burden

---

## 3. When SOC 2 Applies

### 3.1 Organizational Triggers

**When to Pursue SOC 2**:

**Early Indicators**:
- Targeting enterprise B2B customers
- Handling sensitive customer data
- Cloud/SaaS service provider
- Managed service provider (MSP)
- Data processor for regulated industries

**Concrete Triggers**:
- Enterprise customer security requirement in RFP
- Lost deal due to lack of SOC 2
- Series A+ funding (investors expect SOC 2)
- Handling regulated data (healthcare, finance)
- Expanding into enterprise market segment

**Ideal Timing**:
- **Type I**: 12-18 months post-product launch
- **Type II**: 6-12 months after Type I (or skip Type I and go directly to Type II if mature)

### 3.2 Implementation Timeline

**Typical SOC 2 Type II Journey** (12-18 months):

```
Month 1-3: Readiness Assessment
├─ Gap analysis against Trust Services Criteria
├─ Scope definition (systems, locations, services)
├─ Auditor selection
└─ Remediation roadmap

Month 4-9: Control Implementation
├─ Policy and procedure development
├─ Technical control deployment
├─ Security awareness training
├─ Evidence collection processes
└─ Pre-assessment (dry run)

Month 10: Type II Audit Period Begins
├─ Audit observation period starts (6-12 months)
├─ Continuous evidence collection
├─ Quarterly check-ins with auditor
└─ Maintain operational effectiveness

Month 16-18: Audit Execution
├─ Auditor fieldwork (2-4 weeks)
├─ Control testing and interviews
├─ Evidence review
├─ Management response to findings
└─ SOC 2 Type II Report issued
```

### 3.3 Audit Frequency

**Ongoing Commitment**:
- **Type II Report Validity**: 12 months
- **Re-audit Frequency**: Annual
- **Bridge Letters**: Some auditors provide 6-month updates

**Continuous Improvement**:
- Quarterly internal control reviews
- Monthly evidence collection
- Annual policy updates

---

## 4. Where SOC 2 is Relevant

### 4.1 Geographic Applicability

**Origin**: United States (AICPA standard)

**Global Recognition**:
- **North America**: Primary standard for service providers
- **Europe**: Increasingly accepted alongside ISO 27001
- **Asia-Pacific**: Growing adoption, especially in tech sector
- **India**: Recognized by enterprise customers, complements DPDPA compliance

**Alternative/Complementary Standards**:
- **Europe**: ISO 27001 more common
- **UK**: Cyber Essentials Plus
- **Australia**: IRAP, Essential 8
- **Global**: ISO 27001 + SOC 2 combination provides maximum coverage

### 4.2 Industry Applicability

**Highly Relevant** (Often Mandatory):
- **SaaS and Cloud Services**: Essential for enterprise sales
- **Managed Service Providers (MSPs)**: Customer contractual requirement
- **Data Centers and Hosting**: Infrastructure security validation
- **Health Tech (not covered by HIPAA)**: Demonstrates security commitment
- **FinTech**: Especially if handling financial data
- **HR Tech / Payroll**: Employee data protection

**Less Relevant**:
- Manufacturing (physical products)
- Retail (PCI DSS more relevant)
- Professional services (unless technology-enabled)

### 4.3 Organizational Scope

**Service Organization**: Entity providing services to user entities

**In-Scope Systems**:
- Customer-facing applications
- Data processing infrastructure
- Customer support systems
- Security and monitoring tools

**Out-of-Scope Examples**:
- Internal HR systems (unless customer data involved)
- Corporate finance systems
- Marketing website (unless customer data collected)

**Subservice Organizations**:
- Cloud providers (AWS, Azure, GCP) - Carve-out or inclusive approach
- Payment processors - Typically carved out
- Email providers - Inclusive or carved out

---

## 5. How to Achieve SOC 2 Compliance

### 5.1 Implementation Roadmap

#### Step 1: Define Scope and Trust Criteria

**Actions**:
- Identify in-scope services, systems, and locations
- Select Trust Services Criteria:
  - Common Criteria (CC): Mandatory
  - Security: Mandatory for most
  - Availability: If uptime commitments exist
  - Confidentiality/Privacy/Processing Integrity: Based on service description
- Document service description and boundaries

**Deliverable**: Scope Statement and Service Description

---

#### Step 2: Conduct Gap Assessment

**Actions**:
- Review checklist: [SOC2 CheckPoints.xlsx](SOC2%20compliance/SOC2%20CheckPoints.xlsx)
- Assess current controls against all applicable TSC points
- Identify control gaps
- Estimate remediation effort and timeline

**Tools**:
- TSC control checklist
- GRC platforms (Vanta, Drata, SecureFrame, Tugboat Logic)

**Deliverable**: Gap Analysis Report

---

#### Step 3: Select Auditor

**Choosing a CPA Firm**:
- AICPA member with SOC 2 expertise
- Industry experience (SaaS, cloud, etc.)
- Reputation and customer references
- Cost (typically $15K-$100K+ depending on size and complexity)

**Top Auditors**:
- Big 4: Deloitte, PwC, EY, KPMG (expensive but prestigious)
- Mid-tier: A-LIGN, Schellman, Johanson Group (balance of cost and quality)
- Specialized: Various regional CPA firms

**Engagement Letter**: Defines scope, timeline, cost

---

#### Step 4: Implement Controls

**Common Criteria (CC) Implementation**:

**CC1: Control Environment**
- Document organizational structure
- Code of conduct and ethics policy
- Board/management meeting minutes
- Job descriptions with security responsibilities

**CC2: Communication**
- Internal security communications (newsletters, Slack channels)
- Customer security communications (status page, incident disclosure)
- Employee handbook with security policies

**CC3: Risk Assessment**
- Risk assessment process (annual minimum)
- [Risk Register](../../../risk-management/risk-register.md)
- Threat modeling for critical systems
- Fraud risk assessment

**CC4: Monitoring**
- Internal audit program
- Control self-assessments
- Third-party audits (SOC 2, penetration testing)
- Management review meetings (quarterly)

**CC5: Control Activities**
- Documented policies and procedures
- Automated controls where possible
- Segregation of duties
- Change management process

**CC6: Logical and Physical Access**
- **CC6.1**: Role-based access control (RBAC), least privilege
- **CC6.2**: Privileged access management (PAM), MFA for admins
- **CC6.3**: Offboarding procedure (immediate access revocation)
- **CC6.4**: Physical security (badge access, visitor logs, CCTV)
- **CC6.5**: Data classification and handling procedures
- **CC6.6**: Firewall, network segmentation, IDS/IPS
- **CC6.7**: Encryption in transit (TLS 1.3), at rest (AES-256)
- **CC6.8**: Strong authentication (MFA), session management

**CC7: System Operations**
- **CC7.1**: Code review, penetration testing, QA
- **CC7.2**: SIEM, log monitoring, alerting
- **CC7.3**: Vulnerability management, patch SLAs
- **CC7.4**: Incident response plan, playbooks
- **CC7.5**: Backup and disaster recovery, BCP testing

**CC8: Change Management**
- Change request and approval process
- Development → Staging → Production pipeline
- Rollback procedures
- Change log and audit trail

---

**Additional Criteria**:

**Availability** (if applicable):
- SLA monitoring and reporting
- High availability architecture (load balancers, redundancy)
- Disaster recovery plan with RPO/RTO
- Business continuity testing

**Processing Integrity** (if applicable):
- Input validation
- Data quality checks
- Error handling and logging
- Reconciliation procedures

**Confidentiality** (if applicable):
- NDA with employees and vendors
- Confidential data encryption
- Access controls for confidential data

**Privacy** (if applicable):
- Privacy policy and consent management
- Data subject rights (access, deletion, portability)
- Third-party data sharing controls
- Privacy impact assessments
- Alignment with [GDPR](gdpr-compliance.md) and [DPDPA](dpdpa-compliance.md)

---

#### Step 5: Establish Evidence Collection

**SOC 2 is Evidence-Driven**. For each control, collect evidence:

**Types of Evidence**:
- **Policies and Procedures**: Written documentation
- **Screenshots**: System configurations, access logs
- **Logs**: SIEM logs, change logs, access reviews
- **Tests**: Penetration test reports, vulnerability scans
- **Training Records**: Completion certificates, attendance logs
- **Tickets**: Incident response tickets, change tickets
-**Reports**: Weekly/monthly security reports, board presentations

**Evidence Organization**:
- Centralized repository (shared drive, GRC platform)
- Naming convention: `ControlID_EvidenceType_Date.pdf`
- Version control for policies
- Retention: Minimum audit period + 7 years (AICPA requirement)

**Automation Tools**:
- **Vanta, Drata, SecureFrame**: Automated evidence collection from 50+ integrations
- **AWS/Azure/GCP**: Automated configuration snapshots
- **GitHub**: Code review and change management evidence
- **Slack/Email**: Communication and approval workflows

---

#### Step 6: Conduct Internal Readiness Assessment

**Pre-Audit Testing** (3-6 months before audit):
- Self-assessment against TSC checklist
- Mock audit by consultant or internal audit team
- Identify remaining gaps
- Remediate critical findings

**Benefits**:
- Reduces risk of audit failures
- Fine-tunes evidence collection
- Builds confidence

---

#### Step 7: Audit Kick-Off and Observation Period

**Type II Observation Period**: 6-12 months

**Auditor Activities**:
- Planning meeting (scope confirmation)
- Quarterly check-ins
- Evidence review requests
- Interim testing (optional)

**Your Activities**:
- Continuous evidence collection
- Maintain control operational effectiveness
- Document exceptions and incidents
- Prepare for fieldwork

---

#### Step 8: Audit Fieldwork and Testing

**Duration**: 2-4 weeks (on-site or remote)

**Auditor Activities**:
- **Control Design Testing**: Are controls designed properly?
- **Control Effectiveness Testing**: Did controls operate effectively over the audit period?
- **Sampling**: Review evidence samples (e.g., 25 access reviews over 12 months)
- **Interviews**: Management, IT, security, HR, support staff
- **System Walkthroughs**: Live demonstration of controls

**Your Preparation**:
- Evidence packets organized by control
- Key personnel available for interviews
- System access for auditor (read-only)
- Conference room/virtual meeting space

---

#### Step 9: Management Response and Report Issuance

**Audit Findings**:
- **Clean Opinion**: No exceptions - ideal outcome
- **Qualified Opinion**: Some controls ineffective - still valuable but requires disclosure
- **Adverse Opinion**: Significant deficiencies - rare, indicates major issues

**Management Response**:
- Acknowledge findings
- Corrective action plan with timeline
- Included in SOC 2 report as addendum

**SOC 2 Report Contents**:
- Independent auditor's opinion
- Management's assertion
- Description of system and controls
- Trust Services Criteria tested
- Test results and exceptions
- Management response (if applicable)

**Report Distribution**:
- Under NDA to customers and prospects
- NOT publically sharable (proprietary information)
- Typically shared via secure portal or direct PDF

---

### 5.2 Using the SOC 2 Checklist

**Checklist File**: `SOC2 CheckPoints.xlsx`

**How to Use**:

1. **Control Identification**:
   - Review all Common Criteria (CC1-CC8)
   - Review applicable additional criteria (Security, Availability, etc.)
   - Mark applicable vs. not applicable

2. **Control Assessment**:
   - For each applicable control:
     - ✅ Implemented and Effective
     - ⚠️ Implemented but Needs Improvement
     - ❌ Not Implemented
     - **Evidence Status**: Evidence available / In progress / Missing

3. **Remediation Planning**:
   - Prioritize gaps (High/Medium/Low priority)
   - Assign owners
   - Set target completion dates

4. **Evidence Mapping**:
   - Link each control to evidence location
   - Identify evidence collection gaps
   - Automate where possible

5. **Audit Preparation**:
   - Use checklist as audit guide
   - Ensure all evidence is auditor-ready
   - Mock audit self-assessment

---

### 5.3 Integration with Other Security Programs

**SOC 2 ↔ ISO 27001 Synergies**:

| SOC 2 Control | ISO 27001 Control | Shared Evidence |
|---------------|-------------------|-----------------|
| CC6.1 (Access control) | A.5.15, A.8.2 | Access review logs, RBAC configuration |
| CC6.7 (Encryption) | A.8.24 | TLS configuration, encryption policies |
| CC7.2 (Monitoring) | A.8.15, A.8.16 | SIEM logs, monitoring procedures |
| CC7.4 (Incident response) | A.5.24-A.5.28 | Incident response plan, incident tickets |
| CC8.1 (Change management) | A.8.32 | Change tickets, approval workflows |

**Benefit**: Implementing ISO 27001 substantially reduces SOC 2 effort

---

## 6. Who is Involved

### 6.1 Internal Roles

**Executive Leadership / CEO**:
- Management assertion (signs SOC 2 report)
- Resource allocation approval
- Board communication

**CISO / Security Lead**:
- SOC 2 program ownership
- Control implementation oversight
- Auditor primary contact

**IT / DevOps**:
- Technical control implementation
- Evidence collection from systems
- System access for auditor

**HR**:
- Background checks (CC6.1)
- Onboarding/offboarding (CC6.3)
- Training records (CC2.2)

**Legal / Compliance**:
- Contract reviews (vendor management)
- Regulatory alignment
- NDA management for report distribution

**Finance**:
- Budget for audit and tooling
- Invoicing and contracts with auditor

### 6.2 External Parties

**CPA Firm / Auditor**:
- Independent examination
- Report issuance

**Consultants** (Optional):
- Gap assessment
- Control implementation support
- Mock audits

---

## 7. Compliance Mapping

### 7.1 SOC 2 ↔ GDPR

| SOC 2 Control | GDPR Requirement | Alignment |
|---------------|------------------|-----------|
| **Privacy Criteria** | Entire GDPR | Direct alignment |
| CC6.7 (Encryption) | Article 32 (Security of processing) | Technical measure |
| CC7.4 (Incident response) | Article 33 (Breach notification) | Incident handling |
| CC6.1 (Access control) | Article 32 (Access controls) | Organizational measure |

**Benefit**: SOC 2 Privacy + Security demonstrates GDPR Article 32 compliance

---

### 7.2 SOC 2 ↔ DPDPA (India)

**DPDPA Section 8: Security Safeguards**

SOC 2 controls demonstrate "reasonable security practices":
- **CC6**: Logical and physical access = Access controls
- **CC7**: System operations = Security monitoring
- **Privacy Criteria**: Personal data protection

**Benefit**: SOC 2 report serves as evidence for DPDPA compliance to clients

---

## 8. Common Challenges and Solutions

### 8.1 Challenge: Evidence Collection Overload

**Problem**: Manual evidence gathering is time-consuming

**Solutions**:
- Invest in GRC automation (Vanta, Drata): ROI in year 1 through time savings
- Centralize evidence repository
- Schedule recurring evidence collection (e.g., access reviews quarterly)

---

### 8.2 Challenge: Control Exceptions During Audit

**Problem**: 1-2 controls failed during audit period

**Solution**:
- Document exception in management response
- Provide corrective action plan
- Most customers accept qualified opinions if exceptions are minor and corrected

---

### 8.3 Challenge: Audit Cost

**Problem**: $25K-$100K+ audit fees

**Solutions**:
- Start with Type I (lower cost) before Type II
- Smaller scope initially (e.g., Security only, not all 5 criteria)
- Mid-tier auditors vs. Big 4 (cost savings without sacrificing quality)

---

### 8.4 Challenge: Subservice Organizations (Cloud Providers)

**Problem**: Relying on AWS/Azure/GCP SOC 2 reports

**Solutions**:
- **Carve-Out Method**: Exclude cloud provider controls, rely on their SOC 2
- **Inclusive Method**: Your auditor tests your controls over cloud provider selection and monitoring
- **Recommendation**: Carve-out (industry standard for SaaS)

---

## 9. Metrics and KPIs

| Metric | Target | Purpose |
|--------|--------|---------|
| **Audit Opinion** | Clean (unqualified) | Gold standard |
| **Control Exceptions** | 0 | Operational effectiveness |
| **Time to Remediate Gaps** | 90 days avg | Audit readiness |
| **Evidence Collection Automation** | 70%+ | Efficiency |
| **Customer Report Requests** | Response < 48hrs | Sales enablement |

---

## 10. Resources and References

### 10.1 Official Resources

- **AICPA Trust Services Criteria**: https://www.aicpa.org/soc4so
- **SOC 2 Checklist**: [SOC2 CheckPoints.xlsx](SOC2%20compliance/SOC2%20CheckPoints.xlsx)

### 10.2 Automation Platforms

- **Vanta**: https://vanta.com (SOC 2 automation leader)
- **Drata**: https://drata.com (Strong GRC platform)
- **SecureFrame**: https://secureframe.com (Compliance automation)

### 10.3 Auditor Directories

- **AICPA CPA Firm Directory**: Search for SOC 2 specialists
- **Recommendations**: A-LIGN, Schellman, Johanson Group, Sensiba San Filippo

---

## 11. Next Steps for This Organization

### 11.1 Current Status

- ✅ Security controls implemented (ISO 27001 alignment)
- ✅ Risk management framework
- ⏳ SOC 2 gap assessment (next phase)
- ⏳ Auditor selection pending

### 11.2 Immediate Actions (Next 60 Days)

1. **Gap Assessment**:
   - Complete [SOC2 CheckPoints.xlsx](SOC2%20compliance/SOC2%20CheckPoints.xlsx)
   - Identify critical gaps

2. **Auditor RFP**:
   - Request proposals from 3-5 CPA firms
   - Compare cost, timeline, industry experience

3. **Evidence Collection**:
   - Implement GRC platform (recommended) OR
   - Establish manual evidence collection process

4. **Control Remediation**:
   - Prioritize gaps aligned with audit timeline

### 11.3 Target Timeline

**Goal**: SOC 2 Type II Report within 18 months

- **Month 1-2**: Gap assessment, auditor selection *(Current phase)*
- **Month 3-6**: Control implementation
- **Month 7**: Type II observation period begins (12 months)
- **Month 18-19**: Audit fieldwork
- **Month 19**: SOC 2 Type II Report issuance

---

## 12. Related Documents

- [ISO 27001 Compliance](iso27001-compliance.md)
- [GDPR Compliance](gdpr-compliance.md)
- [DPDPA Compliance](dpdpa-compliance.md)
- [Risk Register](../../../risk-management/risk-register.md)
- [Information Security Policy](../../GOVERNANCE/security-policy.md)

---

**Document Owner**: CISO  
**Audit Lead**: Compliance Officer  
**Last Updated**: January 2026  
**Next Review**: Quarterly

---

**Certification Status**: 🔶 Planning Phase - Target Q4 2026  
**Recommended SOC 2 Scope**: Security + Availability (Type II)
