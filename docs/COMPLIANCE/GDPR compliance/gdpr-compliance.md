# GDPR Compliance Framework

> **Regulation**: General Data Protection Regulation (EU) 2016/679  
> **Effective Date**: May 25, 2018  
> **Checklist**: [GDPR CheckPoints.xlsx](GDPR%20compliance/GDPR%20CheckPoints%20(1).xlsx)  
> **Owner**: Data Protection Officer (DPO) / Chief Information Security Officer (CISO)  
> **Last Updated**: January 2026

---

## 1. What is GDPR?

### 1.1 Definition

The **General Data Protection Regulation (GDPR)** is a comprehensive data protection law in the European Union that regulates **how organizations collect, process, store, and protect personal data** of EU/EEA residents. It grants individuals strong rights over their personal data and imposes strict obligations on organizations.

### 1.2 Scope - When GDPR Applies

**Territorial Scope**: GDPR applies if:

1. **Establishment**: Organization is established in the EU/EEA (regardless of where data processing occurs)
   - Example: German company processing data in India → GDPR applies

2. **Targeting**: Organization offers goods/services to EU/EEA individuals OR monitors their behavior (regardless of organization location)
   - Example: Indian SaaS company with EU customers → GDPR applies
   - Example: Website tracking EU visitors → GDPR applies

**Material Scope - What Data**: 
- **Personal Data**: Any information relating to an identified or identifiable natural person
  - Names, email addresses, IP addresses
  - Location data, online identifiers (cookies)
  - Special categories: Health data, biometric data, racial/ethnic origin, religious beliefs (higher protection)

**Who Must Comply**:
- Data Controllers: Determine purposes and means of processing
- Data Processors: Process data on behalf of controllers
- Both have obligations under GDPR

---

## 2. Why GDPR Matters

### 2.1 Legal/Regulatory Necessity

**Massive Penalties for Non-Compliance**:
- **Tier 1 Violations** (e.g., inadequate records): Up to €10M or 2% of global annual turnover (whichever is higher)
- **Tier 2 Violations** (e.g., breach of core principles): Up to **€20M or 4% of global annual turnover**

**Real-World Fines (Examples)**:
- Amazon: €746M (2021) - Privacy violations
- WhatsApp: €225M (2021) - Transparency violations  
- Google: €90M (2020) - Cookie consent violations
- H&M: €35.3M (2020) - Employee surveillance
- British Airways: €22M (2020) - Data breach

**Individual Rights**: GDPR grants individuals enforceable rights:
- Class-action lawsuits possible
- Compensation for damages (material and non-material)

### 2.2 Business Impact

**Trust and Reputation**:
- Demonstrates commitment to privacy
- Competitive advantage in privacy-conscious markets
- Customer confidence and loyalty

**Operational Benefits**:
- Forces data minimization and clean data practices
- Improves data governance and security
- Reduces risk of data breaches
- Streamlines cross-border data operations in EU

**Market Access**:
- Required for EU/EEA market access
- Enterprise customers (especially EU) mandate GDPR compliance
- Standard contractual clauses (SCCs) for international transfers

### 2.3 Synergies with Other Regulations

**Global Privacy Laws Modeled on GDPR**:
- **DPDPA (India)**: Similar principles, inspired by GDPR
- **LGPD (Brazil)**: Nearly identical structure
- **CCPA/CPRA (California)**: Similar rights, different structure
- **POPIA (South Africa)**: GDPR-aligned

**Benefit**: GDPR compliance substantially covers other privacy laws

---

## 3. When GDPR Requirements Apply

### 3.1 Data Lifecycle Stages

GDPR applies at **every stage** of personal data processing:

```
Collection → Storage → Use → Sharing → Retention → Deletion
    ↓          ↓        ↓        ↓          ↓          ↓
 Consent/   Encryption Access   DPAs/SCCs  Limits   Right to
  Legal     Security   Controls Agreements  Defined  Erasure
   Basis    Measures                                
```

### 3.2 Triggering Events

**Consent Collection** (Article 7):
- At point of data collection
- Must be freely given, specific, informed, unambiguous
- Granular consent (separate consent for different purposes)
- Easy withdrawal

**Data Processing Activities**:
- Marketing campaigns
- Analytics and tracking
- Third-party data sharing
- Cross-border data transfers

**Data Breach** (Article 33):
- Notification to supervisory authority within **72 hours**
- Notification to affected individuals if high risk

**Individual Rights Requests** (Articles 15-22):
- Right of access
- Right to rectification
- Right to erasure ("right to be forgotten")
- Right to data portability
- Right to object

---

## 4. Where GDPR Applies

### 4.1 Geographic Applicability

**Primary Jurisdiction**: European Union (27 member states) + EEA (Iceland, Liechtenstein, Norway)

**Extraterritorial Application**: Worldwide if:
- Offering goods/services to EU/EEA individuals
- Monitoring behavior of EU/EEA individuals

**Example Scenarios**:

| Scenario | GDPR Applies? |
|----------|---------------|
| Indian company with only Indian customers | ❌ No |
| Indian company with EU customers via website | ✅ Yes |
| Indian company tracking EU visitors (analytics) | ✅ Yes |
| US company with EU employees | ✅ Yes (employee data) |
| Cloud provider storing EU customer data (processor) | ✅ Yes (processor obligations) |

### 4.2 Data Location vs. GDPR Jurisdiction

**Common Misconception**: "Data stored outside EU = GDPR doesn't apply"

**Reality**: GDPR applies based on **data subject location**, NOT data storage location

**Cross-Border Data Transfers** (Chapter V):
- **Adequacy Decision**: Transfer to countries with adequate protection (e.g., UK post-Brexit, Japan)
- **Standard Contractual Clauses (SCCs)**: Legal mechanism for transfers (e.g., EU → India)
- **Binding Corporate Rules (BCRs)**: For multinational companies
- **Derogations**: Limited exceptions (e.g., explicit consent, contract necessity)

**India → EU Transfers**: Use SCCs as legal basis

---

## 5. How to Comply with GDPR

### 5.1 Core Principles (Article 5)

#### Principle 1: Lawfulness, Fairness, and Transparency

**What**: Processing must have a legal basis and be transparent

**Legal Bases (Article 6)** - Need at least ONE:
1. **Consent**: Individual explicitly agrees
2. **Contract**: Necessary to fulfill a contract
3. **Legal Obligation**: Required by law
4. **Vital Interests**: Protect someone's life
5. **Public Task**: Public interest or official authority
6. **Legitimate Interest**: Balancing test (organization interest vs. individual rights)

**Implementation**:
- Privacy policy clearly states legal basis for each processing activity
- Consent mechanisms (checkboxes, opt-in)
- Legitimate interest assessments (LIA) documented

---

#### Principle 2: Purpose Limitation

**What**: Data collected for specified, explicit, legitimate purposes only

**Implementation**:
- Document purposes in privacy policy
- Do NOT repurpose data without new consent/legal basis
- Example: Email collected for account creation CANNOT be used for marketing without separate consent

---

#### Principle 3: Data Minimization

**What**: Collect only data adequate, relevant, and necessary

**Implementation**:
- Regular data inventory and hygiene
- Remove unnecessary form fields
- "Why do we need this?" test for each data point

**Example**:
- ❌ Bad: Collecting date of birth when only age verification (yes/no) needed
- ✅ Good: Checkbox "I am over 18"

---

#### Principle 4: Accuracy

**What**: Keep personal data accurate and up-to-date

**Implementation**:
- Allow users to update their data (self-service profile)
- Regular data quality reviews
- Rectification process for inaccurate data

---

#### Principle 5: Storage Limitation

**What**: Keep data only as long as necessary

**Implementation**:
- Define retention periods for each data category
- Automated deletion workflows
- Archival policies

**Example Retention**:
- Customer data: Until account deletion + 30 days
- Marketing consents: Until withdrawal
- Financial records: 7 years (legal requirement)

---

#### Principle 6: Integrity and Confidentiality (Security)

**What**: Appropriate technical and organizational measures

**Implementation** (Article 32):
- **Encryption**: Data at rest (AES-256) and in transit (TLS 1.3)
- **Access Controls**: Role-based access, least privilege
- **Pseudonymization**: Where possible
- **Regular Testing**: Penetration tests, vulnerability scans
- **Incident Response**: Breach notification procedures

**Compliance Alignment**:
- ISO 27001 controls demonstrate Article 32 compliance
- SOC 2 Security criteria
- Technical measures: [Security Architecture](../../ARCHITECTURE/security-architecture.md)

---

#### Principle 7: Accountability

**What**: Demonstrate compliance, not just "be" compliant

**Implementation**:
- Records of Processing Activities (ROPA) (Article 30)
- Data Protection Impact Assessments (DPIA) (Article 35)
- Privacy by Design and Default (Article 25)
- Data Protection Officer (if required)

---

### 5.2 Individual Rights Implementation (Articles 15-22)

#### Right of Access (Article 15)

**What**: Individuals can request copy of their personal data

**Implementation**:
- Self-service data export (recommended)
- Manual process:response within **1 month**
- Provide: Data categories, purposes, recipients, retention period, rights

**Technical**: Build data export API/feature

---

#### Right to Rectification (Article 16)

**What**: Correct inaccurate data

**Implementation**:
- Self-service profile editing
- Update request form
- Notify third parties if data shared

---

#### Right to Erasure (Article 17) - "Right to be Forgotten"

**What**: Delete personal data under certain conditions

**When Deletion NOT Required**:
- Legal obligation to retain (e.g., financial records)
- Legitimate interest outweighs individual rights
- Data necessary for contract performance

**Implementation**:
- Account deletion feature
- Data anonymization (if deletion not feasible)
- 30-day retention for recovery, then hard delete
- Notify processors to delete

---

#### Right to Data Portability (Article 20)

**What**: Receive data in machine-readable format and transmit to another controller

**Implementation**:
- Export in JSON/CSV format
- API for data portability
- Standard formats (e.g., Google Takeout model)

---

#### Right to Object (Article 21)

**What**: Object to processing, especially for direct marketing

**Implementation**:
- Unsubscribe links in all marketing emails
- Opt-out preference center
- Immediate cessation of processing upon objection

---

#### Automated Decision-Making and Profiling (Article 22)

**What**: Right not to be subject to solely automated decisions with significant effects

**Implementation**:
- Human review for significant automated decisions
- Disclosure of automated decision-making logic
- Right to contest and explanation

---

### 5.3 Organizational Requirements

#### Data Protection Officer (DPO) - Article 37

**When Required**:
- Public authority or body
- Core activities involve large-scale systematic monitoring
- Core activities involve large-scale processing of special categories

**Typical Tech Startups**: NOT required (but recommended)

**DPO Responsibilities**:
- Monitor GDPR compliance
- Conduct DPIAs
- Advise on privacy matters
- Contact point for supervisory authorities

---

#### Records of Processing Activities (ROPA) - Article 30

**What**: Document all data processing activities

**Required Information**:
- Purposes of processing
- Categories of data subjects and personal data
- Recipients of data (including third countries)
- Retention periods
- Security measures

**Format**: Spreadsheet or privacy management tool

**Template Example**:

| Processing Activity | Legal Basis | Data Categories | Recipients | Retention | Security |
|---------------------|-------------|-----------------|------------|-----------|----------|
| User Account Management | Contract | Name, email, password hash | None | Until deletion + 30 days | Encryption, access controls |
| Marketing | Consent | Email | Email provider (Mailchimp) | Until withdrawal | Encryption in transit |

---

#### Data Protection Impact Assessment (DPIA) - Article 35

**When Required**:
- High risk to individuals' rights and freedoms
- Large-scale processing of special categories
- Systematic monitoring (e.g., CCTV)
- Automated decision-making with significant effects
- New technologies

**Process**:
1. Describe processing and purposes
2. Assess necessity and proportionality
3. Identify risks to individuals
4. Mitigation measures
5. Consult DPO (if applicable)
6. Document outcome

**Example Triggers**:
- Launching AI-powered profiling feature
- Biometric authentication
- Large-scale health data processing

---

#### Privacy by Design and Default (Article 25)

**What**: Embed privacy into systems from design phase

**By Design**:
- Privacy features built-in, not bolted on
- Example: End-to-end encryption in messaging app

**By Default**:
- Most privacy-protective settings as default
- Example: Profiles private by default, user opts-in to public

**Implementation**:
- Privacy impact assessment in product design
- Security requirements in development lifecycle
- Data minimization by default

---

### 5.4 Cross-Border Data Transfers (Chapter V)

**Challenge**: Transferring personal data outside EU/EEA

**Mechanisms**:

**1. Adequacy Decisions** (Article 45):
- EU Commission deems country has adequate protection
- Adequate countries: UK, Japan, Switzerland, Israel (among others)
- India: NOT adequate (as of 2026)

**2. Standard Contractual Clauses (SCCs)** (Article 46):
- EU-approved contract templates
- Both parties (EU entity and non-EU entity) sign
- Commits non-EU entity to GDPR-level protection
- **Use Case**: EU customer data processed in India

**SCC Process**:
1. Conduct Transfer Impact Assessment (TIA)
2. Select appropriate SCC module:
   - Controller → Controller
   - Controller → Processor (most common for SaaS)
   - Processor → Processor
   - Processor → Controller
3. Append technical and organizational measures (Annex II)
4. Both parties sign
5. Maintain records

**3. Binding Corporate Rules (BCRs)**:
- For multinational companies
- Approved by supervisory authorities
- Complex, time-intensive

**4. Derogations** (Article 49):
- Explicit consent
- Contract necessity
- Legal claims
- **Use sparingly**: Not scalable for regular business

---

### 5.5 Breach Notification (Articles 33-34)

**Data Breach Definition**: Security incident leading to accidental or unlawful destruction, loss, alteration, unauthorized disclosure, or access

**Notification to Supervisory Authority** (Article 33):
- **Timeline**: Within **72 hours** of becoming aware
- **Content**:
  - Nature of breach
  - Categories and number of affected individuals
  - Likely consequences
  - Measures taken or proposed
- **Penalty**: Failure to notify = Tier 1 violation (up to €10M or 2%)

**Notification to Individuals** (Article 34):
- **When**: If breach results in high risk to rights and freedoms
- **Timeline**: Without undue delay
- **Content**: Clear, plain language explanation of breach, consequences, mitigation

**Exceptions to Individual Notification**:
- Data was encrypted (and key not compromised)
- Subsequent measures eliminate high risk
- Notification requires disproportionate effort (use public communication instead)

**Implementation**:
- Incident response plan: [Incident Response](../../ARCHITECTURE/incident-response-plan.md) (to be created)
- Breach notification templates
- Supervisory authority contact details
- 72-hour response capability

---

### 5.6 Using the GDPR Checklist

**Checklist File**: `GDPR CheckPoints.xlsx`

**How to Use**:

1. **Compliance Assessment**:
   - Review each GDPR requirement (Articles 5-34, key obligations)
   - Mark status:
     - ✅ Compliant
     - ⚠️ Partially Compliant
     - ❌ Non-Compliant
     - N/A - Not Applicable

2. **Documentation Review**:
   - Privacy Policy: Up-to-date, complete?
   - Cookie Policy: Consent mechanism compliant?
   - ROPA: All processing activities documented?
   - DPIAs: High-risk processing assessed?
   - SCCs: Signed for all international transfers?

3. **Rights Mechanism Testing**:
   - Test data subject rights workflows
   - Access request: Can user export data?
   - Deletion: Is data fully deleted?
   - Objection: Marketing opt-out functional?

4. **Breach Readiness**:
   - Incident response plan tested?
   - 72-hour notification capability?
   - Supervisory authority contact ready?

5. **Continuous Monitoring**:
   - Quarterly GDPR compliance reviews
   - Annual privacy policy updates
   - Regular DPIA reviews for high-risk processing

---

## 6. Who is Involved

### 6.1 Roles and Responsibilities

**Data Protection Officer (DPO)**:
- GDPR compliance oversight
- DPIAs and ROPAs
- Supervisory authority liaison
- **When Not Required**: CISO or Privacy Officer assumes responsibilities

**CISO / Security Team**:
- Article 32 security measures (encryption, access controls)
- Breach detection and response
- Security testing (penetration tests, vulnerability scans)

**Legal / Compliance**:
- Privacy policy and legal documentation
- SCCs and vendor agreements
- Supervisory authority correspondence
- Legal basis assessment

**Product / Engineering**:
- Privacy by design implementation
- Data subject rights features (export, delete)
- Consent management UI

**Marketing**:
- Consent collection for marketing
- Email opt-out mechanisms
- Cookie consent management

**Customer Support**:
- Data subject rights request handling
- Privacy inquiry responses
- Escalation to DPO/Legal

**All Staff**:
- Privacy awareness training
- Data breach reporting
- GDPR policy compliance

---

## 7. Compliance Mapping

### 7.1 GDPR ↔ ISO 27001

| GDPR Requirement | SO 27001 Control | Shared Implementation |
|------------------|------------------|-----------------------|
| Article 32 (Security) | A.8.24 (Cryptography), A.5.15 (Access control) | Encryption, access controls |
| Article 33 (Breach notification) | A.5.24-A.5.28 (Incident management) | Incident response plan |
| Article 25 (Privacy by design) | A.14.2 (Security in development) | Secure SDLC |
| Article 30 (ROPA) | Clause 7.5 (Documented information) | Documentation management |

**Benefit**: ISO 27001 demonstrates GDPR Article 32 compliance

---

### 7.2 GDPR ↔ SOC 2

| GDPR Requirement | SOC 2 Control | Alignment |
|------------------|---------------|-----------|
| Article 32 (Security) | CC6, CC7 (Security controls) | Technical measures |
| Article 33 (Breach notification) | CC7.4 (Incident response) | Incident handling |
| Data subject rights | Privacy criteria (if included) | Privacy controls |

**Benefit**: SOC 2 Privacy + Security substantially covers GDPR technical requirements

---

### 7.3 GDPR ↔ DPDPA

Both regulations share similar principles:
- **Consent**: Both require clear, informed consent
- **Purpose Limitation**: Data collected for specified purposes
- **Security**: Appropriate technical measures
- **Individual Rights**: Access, rectification, erasure
- **Breach Notification**: Both mandate timely notification

**Key Difference**: DPDPA applies to India data subjects, GDPR to EU/EEA

**Benefit**: GDPR compliance framework substantially addresses DPDPA

---

## 8. Supervisory Authorities

### 8.1 Lead Supervisory Authority

**One-Stop-Shop Mechanism**: Organization deals primarily with ONE supervisory authority (where main establishment is located)

**Common Supervisory Authorities**:
- **Ireland (DPC)**: Many US tech companies (e.g., Google, Facebook, Apple EU HQs)
- **Luxembourg (CNPD)**: Amazon, PayPal
- **Germany**: Various state authorities
- **France (CNIL)**: Active enforcement

### 8.2 Submitting Complaints

**Who Can Complain**: Any individual (lodging complaint is free)

**Where**: Supervisory authority in:
- Member state of individual's habitual residence
- Place of work
- Place of alleged infringement

**Process**:
1. Individual submits complaint form
2. Authority investigates
3. Authority may impose fines, corrective measures

---

## 9. Common Challenges and Solutions

### 9.1 Challenge: Obtaining Valid Consent

**Problem**: Pre-ticked boxes, bundled consent not GDPR-compliant

**Solution**:
- ✅ Opt-in checkboxes (not pre-ticked)
- ✅ Granular consent (separate for different purposes)
- ✅ Easy withdrawal ("unsubscribe" link)
- ✅ Clear language (no legalese)

---

### 9.2 Challenge: Data Subject Rights at Scale

**Problem**: Manual fulfillment of rights requests is time-consuming

**Solution**:
- Automated data export and deletion features
- Privacy management platforms (OneTrust, TrustArc, Securiti.ai)
- Self-service user portals

---

### 9.3 Challenge: International Data Transfers

**Problem**: India not an "adequate" country, SCCs complex

**Solution**:
- Use Standard Contractual Clauses (SCCs) - EU Commission templates
- Conduct Transfer Impact Assessment (TIA)
- Document in privacy policy
- Example: "We use SCCs approved by the EU Commission for data transfers to India"

---

### 9.4 Challenge: Cookie Consent Fatigue

**Problem**: Users annoyed by cookie banners

**Solution**:
- Minimize non-essential cookies
- Use compliant consent management platforms (Cookiebot, OneTrust)
- "Reject All" button equally prominent as "Accept All"
- Granular cookie categories

---

## 10. Resources and References

### 10.1 Official Resources

- **GDPR Full Text**: https://gdpr-info.eu/
- **European Data Protection Board (EDPB)**: https://edpb.europa.eu/ (Guidelines and opinions)
- **GDPR Checklist**: [GDPR CheckPoints.xlsx](GDPR%20compliance/GDPR%20CheckPoints%20(1).xlsx)

### 10.2 Tools and Platforms

**Privacy Management**:
- OneTrust, TrustArc, Securiti.ai (Enterprise)
- Osano, Termly (SMB)

**Cookie Consent**:
- Cookiebot, OneTrust, Termly

**Data Mapping**:
- BigID, Privitar, OneTrust

### 10.3 Training

- **IAPP (International Association of Privacy Professionals)**: CIPP/E certification
- **DPO Training**: Certified Data Protection Officer courses

---

## 11. Next Steps for This Organization

### 11.1 Current Status

- ✅ Security measures (Article 32) via ISO 27001 alignment
- ⏳ Privacy policy and cookie policy review needed
- ⏳ ROPA (Records of Processing Activities) to be created
- ⏳ Data subject rights mechanisms (export, delete) to be implemented

### 11.2 Immediate Actions (Next 90 Days)

1. **Privacy Policy Audit**:
   - Use [GDPR CheckPoints.xlsx](GDPR%20compliance/GDPR%20CheckPoints%20(1).xlsx)
   - Update privacy policy with all required disclosures
   - Add cookie policy

2. **Create ROPA**:
   - Document all processing activities
   - Identify legal basis for each
   - Map data flows

3. **Implement Data Subject Rights**:
   - Build data export feature
   - Account deletion workflow
   - Consent management system

4. **International Transfers**:
   - If EU customers: Sign SCCs with EU entities
   - Document in privacy policy

5. **Training**:
   - GDPR awareness training for all staff
   - Specialized training for support (handling rights requests)

### 11.3 Compliance Target

**Goal**: Full GDPR compliance within 6 months

- **Month 1**: Policy audit, ROPA creation
- **Month 2-3**: Data subject rights implementation
- **Month 4**: SCCs for international transfers
- **Month 5**: GDPR awareness training
- **Month 6**: Compliance audit, documentation finalization

---

## 12. Related Documents

- [DPDPA Compliance](dpdpa-compliance.md)
- [ISO 27001 Compliance](iso27001-compliance.md)
- [SOC 2 Compliance](soc2-compliance.md)
- [Information Security Policy](../../GOVERNANCE/security-policy.md)
- [Risk Register](../../../risk-management/risk-register.md)

---

**Document Owner**: DPO / CISO  
**Compliance Lead**: Legal / Compliance Officer  
**Last Updated**: January 2026  
**Next Review**: Quarterly or upon regulatory changes

---

**Compliance Status**: ⚠️ Partially Compliant - Active Implementation  
**Target**: Full Compliance Q2 2026  
**Applicability**: ✅ Yes (if EU/EEA customers or monitoring)
