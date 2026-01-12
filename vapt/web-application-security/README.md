# Web Application Security - DVWA VAPT

> **Testing Scope**: Damn Vulnerable Web Application (DVWA)  
> **Environment**: Kali Linux → DVWA Docker Container  
> **Methodology**: OWASP Testing Guide v4.2 Alignment

---

## 1. What is Web Application Security Testing?

### 1.1 Definition

Web Application Security Testing is the systematic evaluation of web applications to **identify vulnerabilities, assess security posture, and validate security controls** before exploitation by malicious actors.

### 1.2 Scope

**Target Application**: Damn Vulnerable Web Application (DVWA)
- Intentionally vulnerable PHP/MySQL web application
- Security levels: Low, Medium, High
- Covers OWASP Top 10 vulnerabilities

**Testing Coverage**:
- SQL Injection (SQLi)
- Cross-Site Scripting (XSS - Stored & Reflected)
- Cross-Site Request Forgery (CSRF)
- Command Injection
- File Inclusion (LFI/RFI)
- File Upload vulnerabilities
- Authentication bypass
- Session management flaws
- Security misconfiguration

---

## 2. Why Web Application Security Testing is Critical

### 2.1 Threat Landscape

**Statistics**:
- 90%+ of security breaches involve web applications (Verizon DBIR)
- OWASP Top 10 vulnerabilities responsible for majority of web attacks
- SQL Injection remains #1 attack vector for data breaches

**Business Impact**:
- Data breaches → regulatory fines (GDPR: up to €20M or 4% revenue)
- Reputational damage
- Customer trust erosion
- Legal liabilities (DPDPA: penalties for non-compliance)

### 2.2 Compliance Requirements

| Framework | Web Security Requirements |
|-----------|--------------------------|
| **ISO 27001:2022** | A.8.8 (Management of technical vulnerabilities), A.14.2 (Security in development and support processes) |
| **SOC 2** | CC6.1 (Logical access), CC7.1 (Quality monitoring) |
| **GDPR** | Article 32 (Security of processing - technical measures) |
| **DPDPA** | Section 8 (Security safeguards for data protection) |

---

## 3. When Testing is Performed

### 3.1 Testing Frequency

**Continuous Testing Cadence**:
- **Weekly**: Automated vulnerability scans
- **Monthly**: Manual penetration testing of new features
- **Quarterly**: Comprehensive VAPT assessment
- **Ad-Hoc**: Before major releases, after security incidents

### 3.2 SDLC Integration

```
Design → Build → Test → Deploy
  ↓        ↓       ↓       ↓
Threat   SAST    DAST   Pen Test
Model    SCA     IAST   (Manual)
```

---

## 4. Where Testing is Conducted

### 4.1 Test Environment

**Infrastructure**:
- **Attacker Machine**: Kali Linux VM (4 vCPU, 8GB RAM)
- **Target Application**: DVWA in Docker container
- **Network**: Isolated NAT network (no external internet)
- **Data**: Test data only, no production data

**Network Topology**:
```
┌────────────────────────────────────┐
│  Kali Linux (192.168.56.10)        │
│  • Burp Suite Professional         │
│  • OWASP ZAP                        │
│  • SQLMap, XSS Hunter               │
└───────────┬────────────────────────┘
            │ NAT Network
            │ (Isolated)
┌───────────▼────────────────────────┐
│  Docker Host (192.168.56.11)       │
│  ┌──────────────────────────────┐  │
│  │ DVWA Container               │  │
│  │ • Low Security Level         │  │
│  │ • MariaDB backend            │  │
│  │ • Port 80/443 exposed        │  │
│  └──────────────────────────────┘  │
└────────────────────────────────────┘
```

### 4.2 Authorization

**Explicit Authorization**: Self-owned lab environment, authorized testing

**Out of Scope** (Zero Tolerance):
- ❌ Production systems
- ❌ Third-party websites
- ❌ Unauthorized penetration testing
- ❌ Real user data

---

## 5. How Testing is Conducted

### 5.1 Testing Methodology

Based on **OWASP Web Security Testing Guide v4.2**:

#### Phase 1: Information Gathering (Passive Reconnaissance)
**What**: Collect publicly available information without active probing  
**How**:
- Technology stack identification (Wappalyzer, WhatWeb)
- robots.txt and sitemap.xml review
- Search engine reconnaissance
- Public vulnerability databases (CVE, ExploitDB)

**Tools**: curl, WhatWeb, Wappalyzer

#### Phase 2: Configuration and Deployment Testing
**What**: Assess security configuration and deployment practices  
**How**:
- HTTP security headers analysis
- SSL/TLS configuration testing
- Directory listing and file exposure
- Error handling and information disclosure
- Default credentials testing

**Tools**: testssl.sh, Nikto, Burp Suite Scanner

#### Phase 3: Identity Management Testing
**What**: Evaluate authentication and session management  
**How**:
- Credential enumeration
- Brute force protection testing
- Password policy validation
- Session fixation and hijacking tests
- Logout and timeout testing

**Tools**: Burp Suite Intruder, Hydra, custom scripts

#### Phase 4: Authentication Testing
**What**: Validate strength of authentication mechanisms  
**How**:
- Bypass techniques (SQL injection auth bypass)
- Weak password recovery mechanisms
- Multi-factor authentication validation
- CAPTCHA bypass testing

#### Phase 5: Authorization Testing
**What**: Test access control enforcement  
**How**:
- Horizontal privilege escalation
- Vertical privilege escalation
- Insecure Direct Object References (IDOR)
- Path traversal

**Tools**: Burp Suite Repeater, manual testing

#### Phase 6: Session Management Testing
**What**: Assess session handling security  
**How**:
- Session token randomness analysis
- Cookie security flags (HttpOnly, Secure, SameSite)
- Session fixation vulnerabilities
- CSRF token validation

**Tools**: Burp Suite, custom scripts for token entropy analysis

#### Phase 7: Input Validation Testing
**What**: Identify injection vulnerabilities  
**How**:
- **SQL Injection**: Error-based, union-based, blind, time-based
- **XSS**: Reflected, stored, DOM-based
- **Command Injection**: OS command execution
- **File Inclusion**: LFI, RFI
- **XXE**: XML External Entity injection
- **Template Injection**: SSTI

**Tools**: SQLMap, XSS Hunter, Burp Suite, manual payloads

#### Phase 8: Error Handling Testing
**What**: Verify secure error processing  
**How**:
- Information disclosure in error messages
- Stack trace exposure
- Debug mode detection

#### Phase 9: Cryptography Testing
**What**: Validate encryption implementation  
**How**:
- Weak encryption algorithms
- Insecure SSL/TLS configurations
- Sensitive data in clear text

**Tools**: testssl.sh, Burp Suite, manual traffic analysis

#### Phase 10: Business Logic Testing
**What**: Identify application-specific logical flaws  
**How**:
- Workflow bypass
- Price manipulation
- Insufficient process validation

**Manual testing required**

#### Phase 11: Client-Side Testing
**What**: Browser-side vulnerability assessment  
**How**:
- DOM-based XSS
- JavaScript security issues
- Resource manipulation
- Clickjacking

**Tools**: Burp Suite, Browser DevTools

---

### 5.2 Testing Approach: Active vs. Passive

| Approach | Description | Usage |
|----------|-------------|-------|
| **Passive** | Observation without active exploitation | Initial reconnaissance, traffic analysis |
| **Active** | Direct interaction and exploitation attempts | Vulnerability validation, penetration testing |

**This project uses**: Active testing in controlled lab environment

---

### 5.3 Tools and Technology

| Tool | Purpose | Usage |
|------|---------|-------|
| **Burp Suite Professional** | Intercepting proxy, scanner, intruder | Primary VAPT platform |
| **OWASP ZAP** | Open-source web app scanner | Automated scanning, spidering |
| **SQLMap** | Automated SQL injection testing | Database fingerprinting, data extraction |
| **XSStrike** | XSS vulnerability scanner | Context-aware XSS payloads |
| **Nikto** | Web server vulnerability scanner | Configuration issues, known vulnerabilities |
| **Dirb / Gobuster** | Directory brute-forcing | Hidden file/directory discovery |
| **WhatWeb** | Technology fingerprinting | Stack identification |
| **Custom Python/Bash Scripts** | Tailored exploit development | Proof-of-concept automation |

---

## 6. Who is Involved

### 6.1 Roles and Responsibilities

**Security Researcher / Penetration Tester**
- Execute testing methodology
- Document findings with evidence
- Develop exploit proof-of-concepts
- Recommend remediation

**CISO / Security Manager**
- Approve testing scope
- Review findings for risk prioritization
- Coordinate remediation efforts

**Development Team**
- Remediate identified vulnerabilities
- Implement secure coding practices
- Validate fixes

---

## 7. Findings Documentation Structure

Each vulnerability finding includes:

### 7.1 Standard Finding Template

```markdown
## Vulnerability: [Name]

### What (Description)
- Technical description of the vulnerability
- Affected component/parameter
- Vulnerability type (OWASP classification)

### Why (Impact & Risk)
- Confidentiality impact
- Integrity impact
- Availability impact
- Business risk translation

### When (Discovery)
- Date discovered
- Detection method
- Affected DVWA security level

### Where (Location)
- URL/endpoint
- Parameter name
- Code location (if applicable)

### How (Exploitation)
- Attack vector
- **Real exploit code** (Python/Bash/SQL/JS)
- Step-by-step reproduction
- Proof-of-concept demonstration

### Who (Affected Parties)
- User roles impacted
- Data exposed

### Severity
- CVSS v3.1 score breakdown
- Risk rating: Critical/High/Medium/Low

### Evidence
- Request/response captures
- Screenshots
- PoC code output

### Remediation
- Specific fix recommendations
- Secure code examples
- Configuration changes

### Compliance Mapping
- ISO 27001 control references
- SOC 2 criteria mapping
- GDPR/DPDPA requirements
```

---

## 8. DVWA Vulnerability Coverage

### 8.1 Planned Testing Modules

| DVWA Module | Vulnerability Type | Testing Priority |
|-------------|-------------------|------------------|
| **SQL Injection** | Injection | Critical |
| **XSS (Reflected)** | Cross-Site Scripting | Critical |
| **XSS (Stored)** | Cross-Site Scripting | Critical |
| **CSRF** | Session Management | High |
| **File Inclusion** | Path Traversal | High |
| **File Upload** | Unrestricted Upload | High |
| **Command Injection** | OS Injection | Critical |
| **Brute Force** | Authentication | Medium |
| **Weak Session IDs** | Session Management | Medium |
| **SQL Injection (Blind)** | Injection | High |
| **JavaScript** | Client-Side | Low |
| **CSP Bypass** | Content Security Policy | Medium |

### 8.2 Testing by Security Level

**Low Security**: 
- Basic exploitation techniques
- No input validation
- Direct vulnerability demonstration

**Medium Security**:
- Bypass basic protections
- More sophisticated payloads
- Filter evasion techniques

**High Security**:
- Advanced bypass methods
- Demonstrates real-world attack complexity
- Multi-step exploitation chains

---

## 9. Ethical and Legal Compliance

### 9.1 Ethical Guidelines

**Adhered Principles**:
- ✅ Testing ONLY on authorized systems (self-owned DVWA lab)
- ✅ No malicious intent—research and learning purposes
- ✅ Responsible disclosure (if findings applicable to real-world)
- ✅ Data privacy—no testing with real user data

**Prohibited Actions**:
- ❌ Unauthorized system access
- ❌ Testing third-party applications without permission
- ❌ Denial of service attacks (even in lab)
- ❌ Data destruction or modification beyond test scope

---

## 10. Reporting

### 10.1 Deliverables

1. **Executive Summary**: Non-technical overview for leadership
2. **Technical Report**: Detailed findings with evidence
3. **Exploit Scripts Repository**: Organized PoC code
4. **Remediation Roadmap**: Prioritized fix timeline
5. **Compliance Gap Analysis**: Control mapping

### 10.2 Report Structure

See: [VAPT Report Template](../../docs/REPORTING/vapt-report-template.md)

---

## 11. Vulnerability Findings

Documented findings organized by vulnerability type:

- [SQL Injection](findings/01-sql-injection.md)
- [Cross-Site Scripting (Reflected)](findings/02-xss-reflected.md)
- [Cross-Site Scripting (Stored)](findings/03-xss-stored.md)
- [Cross-Site Request Forgery](findings/04-csrf.md)
- [Command Injection](findings/05-command-injection.md)
- [File Inclusion](findings/06-file-inclusion.md)
- [File Upload](findings/07-file-upload.md)
- [Authentication Bypass](findings/08-authentication-bypass.md)

---

## 12. Exploit Scripts

Real proof-of-concept code organized by attack type:

- [SQL Injection Exploits](exploits/sqli/)
- [XSS Payloads](exploits/xss/)
- [CSRF PoCs](exploits/csrf/)
- [Command Injection Scripts](exploits/command-injection/)
- [Automation Tools](exploits/automation/)

---

## 13. Related Documents

- [Testing Methodology](methodology.md)
- [Mitigations and Secure Coding](mitigations.md)
- [OWASP Top 10 Mapping](owasp-top10-mapping.md)
- [Compliance Control Mapping](compliance-mapping.md)

---

**Test Lead**: Security Researcher  
**Test Environment Owner**: CISO  
**Last Updated**: January 2026  
**Next Assessment**: Quarterly
