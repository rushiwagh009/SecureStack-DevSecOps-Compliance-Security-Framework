# Security Architecture

> **Document Control**  
> Version: 1.0  
> Effective Date: January 2026  
> Review Cycle: Annual  
> Owner: Chief Information Security Officer (CISO)

---

## 1. What is Security Architecture?

### 1.1 Definition

Security Architecture is the **structured framework of security controls, technologies, processes, and principles** designed to protect organizational assets using a defense-in-depth approach.

### 1.2 Purpose

This document describes:
- Layered security model and controls
- Security domains and boundaries
- Technology stack and tool integration
- Data protection mechanisms
- Identity and access management
- Network segmentation strategy

---

## 2. Why This Architecture Exists

### 2.1 Strategic Objectives

**Primary Goals:**
1. **Prevent Unauthorized Access**: Multi-layer access controls
2. **Detect Security Incidents**: Comprehensive monitoring and logging
3. **Respond to Threats**: Incident response capabilities
4. **Ensure Compliance**: Meet ISO 27001, SOC 2, GDPR, DPDPA requirements
5. **Enable Secure Operations**: Security that enables, not blocks, business

### 2.2 Business Value

- **Risk Reduction**: Minimize attack surface and vulnerability exposure
- **Trust**: Demonstrate security maturity to customers and auditors
- **Operational Resilience**: Prevent and quickly recover from security incidents
- **Competitive Advantage**: Security as a business differentiator

### 2.3 Compliance Alignment

| Framework | Architectural Requirements |
|-----------|---------------------------|
| **ISO 27001:2022** | A.8.1 (User endpoint devices), A.8.20 (Networks security), A.8.22 (Segregation of networks) |
| **SOC 2** | CC6.6 (Logical access - network security), CC6.7 (Transmission of data), CC7.2 (Detection) |
| **GDPR** | Article 25 (Privacy by design), Article 32 (Security of processing) |
| **DPDPA** | Section 8 (Security safeguards - technical measures) |

---

## 3. When Security Architecture Applies

### 3.1 Lifecycle Coverage

**Continuous Protection:**
- Design phase: Security requirements definition
- Build phase: Secure development and configuration
- Deploy phase: Security validation before production
- Operate phase: Continuous monitoring and assessment
- Decommission phase: Secure data deletion

### 3.2 Critical Application Points

- New system deployment
- Architecture changes or migrations
- Third-party integrations
- Security incident response
- Compliance audits

---

## 4. Where Security Controls are Applied

### 4.1 Security Domains

```
┌─────────────────────────────────────────────────────────────┐
│                     ORGANIZATIONAL BOUNDARY                  │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              EXTERNAL PERIMETER                       │  │
│  │  ┌────────────────────────────────────────────────┐  │  │
│  │  │         DMZ / EDGE NETWORK                     │  │  │
│  │  │  • Web Application Firewalls (WAF)             │  │  │
│  │  │  • Load Balancers                              │  │  │
│  │  │  • Public-facing services                      │  │  │
│  │  └──────────────┬─────────────────────────────────┘  │  │
│  │                 │                                     │  │
│  │  ┌──────────────▼─────────────────────────────────┐  │  │
│  │  │         INTERNAL NETWORK                       │  │  │
│  │  │  • Application servers                         │  │  │
│  │  │  • Business logic tier                         │  │  │
│  │  │  • Internal services                           │  │  │
│  │  └──────────────┬─────────────────────────────────┘  │  │
│  │                 │                                     │  │
│  │  ┌──────────────▼─────────────────────────────────┐  │  │
│  │  │         DATA LAYER                             │  │  │
│  │  │  • Databases (encrypted at rest)               │  │  │
│  │  │  • File storage                                │  │  │
│  │  │  • Backup systems                              │  │  │
│  │  └────────────────────────────────────────────────┘  │  │
│  │                                                        │  │
│  │  ┌────────────────────────────────────────────────┐  │  │
│  │  │         SECURITY MANAGEMENT NETWORK            │  │  │
│  │  │  • SIEM / Logging infrastructure               │  │  │
│  │  │  • Security tools (scanners, VAPT)             │  │  │
│  │  │  • Jump boxes / Bastion hosts                  │  │  │
│  │  └────────────────────────────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### 4.2 Lab Environment Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              LAB SECURITY RESEARCH ENVIRONMENT               │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  HOST SYSTEM (Isolated from Production)              │  │
│  │  ┌────────────────────────────────────────────────┐  │  │
│  │  │  Kali Linux VM (Attacker Perspective)          │  │  │
│  │  │  • Burp Suite Professional                     │  │  │
│  │  │  • OWASP ZAP                                    │  │  │
│  │  │  • Nmap, OpenVAS, Metasploit                   │  │  │
│  │  │  • Custom exploit scripts                      │  │  │
│  │  └──────────────┬─────────────────────────────────┘  │  │
│  │                 │ NAT Network (Isolated)             │  │
│  │  ┌──────────────▼─────────────────────────────────┐  │  │
│  │  │  Docker Host                                   │  │  │
│  │  │  ┌──────────────────────────────────────────┐  │  │  │
│  │  │  │  DVWA Container (Vulnerable Target)      │  │  │  │
│  │  │  │  • Low / Medium / High Security Levels   │  │  │  │
│  │  │  │  • MariaDB backend                       │  │  │  │
│  │  │  └──────────────────────────────────────────┘  │  │  │
│  │  └────────────────────────────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                             │
│  NO EXTERNAL INTERNET ACCESS FOR VULNERABLE SYSTEMS         │
└─────────────────────────────────────────────────────────────┘
```

---

## 5. How Security is Architected (Defense-in-Depth)

### 5.1 Layered Security Model

#### Layer 1: Perimeter Security

**What**: External boundary protection  
**Why**: First line of defense against external threats  
**How**: 
- Firewalls (stateful packet inspection)
- Intrusion Detection/Prevention Systems (IDS/IPS)
- DDoS protection
- Web Application Firewall (WAF)

**Controls**:
- Deny-all, allow-by-exception rule sets
- Geographic IP filtering
- Rate limiting and throttling
- SSL/TLS termination and inspection

#### Layer 2: Network Security

**What**: Internal network segmentation and traffic control  
**Why**: Limit lateral movement after perimeter breach  
**How**:
- VLANs and network micro-segmentation
- Zero Trust Network Access (ZTNA) principles
- Network Access Control (NAC)
- Internal firewalls between security zones

**Controls**:
- East-West traffic filtering
- DMZ isolation
- Management network segregation
- Encrypted network tunnels (VPN, WireGuard)

**Compliance Mapping**:
- ISO 27001: A.8.20 (Networks security), A.8.22 (Segregation)
- SOC 2: CC6.6 (Network security)

#### Layer 3: Host Security

**What**: Endpoint and server hardening  
**Why**: Prevent compromise of individual systems  
**How**:
- Operating system hardening (CIS benchmarks)
- Endpoint Detection and Response (EDR)
- Host-based firewalls
- Application allow-listing

**Controls**:
- Minimal service installation (attack surface reduction)
- Automatic security patching
- Full-disk encryption (LUKS, BitLocker)
- Secure boot and measured boot

#### Layer 4: Application Security

**What**: Secure software development and deployment  
**Why**: Most attacks target application vulnerabilities  
**How**:
- Secure coding practices (OWASP Top 10)
- Input validation and output encoding
- Security testing (SAST, DAST, SCA)
- Runtime Application Self-Protection (RASP)

**Controls**:
- Parameterized queries (SQL injection prevention)
- Content Security Policy (CSP)
- Anti-CSRF tokens
- Security headers (HSTS, X-Frame-Options)

**DevSecOps Integration**:
- Pre-commit secret scanning
- Build-time SAST/SCA
- Deploy-time DAST
- Post-deploy penetration testing

#### Layer 5: Data Security

**What**: Protection of data at rest, in transit, and in use  
**Why**: Data is the ultimate target  
**How**:
- Encryption at rest (AES-256)
- Encryption in transit (TLS 1.3)
- Data classification and labeling
- Data Loss Prevention (DLP)

**Controls**:
- Database encryption (Transparent Data Encryption)
- Field-level encryption for sensitive data
- Key management (KMS, HSM)
- Secure data deletion

**Compliance Mapping**:
- GDPR: Article 32 (Encryption as security measure)
- DPDPA: Section 8 (Encryption of personal data)
- ISO 27001: A.8.24 (Use of cryptography)

#### Layer 6: Identity and Access Management (IAM)

**What**: Authentication and authorization controls  
**Why**: Ensure only authorized users access systems  
**How**:
- Multi-Factor Authentication (MFA)
- Single Sign-On (SSO)
- Role-Based Access Control (RBAC)
- Privileged Access Management (PAM)

**Controls**:
- Least privilege principle
- Just-In-Time (JIT) access
- Regular access reviews (quarterly)
- Strong password policies + passwordless options

**Compliance Mapping**:
- SOC 2: CC6.1 (Logical access controls)
- ISO 27001: A.5.15 (Access control), A.5.17 (Authentication)

#### Layer 7: Security Monitoring and Detection

**What**: Continuous visibility and threat detection  
**Why**: Assume breach—detect and respond quickly  
**How**:
- Security Information and Event Management (SIEM)
- Extended Detection and Response (XDR)
- Security Operations Center (SOC)
- User and Entity Behavior Analytics (UEBA)

**Controls**:
- Centralized log aggregation
- Real-time alerting on suspicious activity
- Threat intelligence integration
- Automated incident response playbooks

**Compliance Mapping**:
- SOC 2: CC7.2 (System monitoring and alerting)
- ISO 27001: A.8.15 (Logging), A.8.16 (Monitoring)

---

### 5.2 Security Architecture Principles

#### Principle 1: Defense-in-Depth
**What**: Multiple overlapping layers of security  
**Why**: Single point of failure avoidance

#### Principle 2: Least Privilege
**What**: Minimal access required for role  
**Why**: Reduces insider threat and lateral movement impact

#### Principle 3: Fail-Safe Defaults
**What**: Default deny for access and traffic  
**Why**: Secure unless explicitly permitted

#### Principle 4: Complete Mediation
**What**: Every access checked every time  
**Why**: Prevents privilege escalation

#### Principle 5: Separation of Duties
**What**: Critical operations require multiple parties  
**Why**: Prevents single-person compromise

#### Principle 6: Open Design
**What**: Security not reliant on obscurity  
**Why**: Cryptographic and architectural strength, not secrecy

#### Principle 7: Psychological Acceptability
**What**: Security usable by legitimate users  
**Why**: Bypassed security is ineffective security

---

## 6. Who is Responsible for Security Architecture

### 6.1 Architecture Governance

**Chief Information Security Officer (CISO)**
- Security architecture approval authority
- Architecture review oversight
- Strategic security technology decisions

**Security Architect**
- Architecture design and documentation
- Security requirements definition
- Technology evaluation and selection
- Architecture review and approval for new systems

**System Owners**
- Implementation of security controls
- Compliance with architectural standards
- Security configuration management

**DevOps / Engineering Teams**
- Secure deployment practices
- Infrastructure-as-Code (IaC) security
- Security automation implementation

---

## 7. Technology Stack

### 7.1 Security Tools Inventory

| Category | Tools | Purpose |
|----------|-------|---------|
| **VAPT** | Burp Suite, OWASP ZAP, Nmap, OpenVAS, Metasploit | Vulnerability assessment, penetration testing |
| **SAST** | SonarQube, Semgrep | Static code analysis |
| **DAST** | OWASP ZAP, Burp Suite | Dynamic application testing |
| **SCA** | Snyk, Dependabot | Dependency vulnerability scanning |
| **Container Security** | Trivy, Grype | Container image scanning |
| **IaC Security** | Checkov, tfsec | Infrastructure-as-code scanning |
| **Secrets Management** | HashiCorp Vault, Git-secrets | Credential protection |
| **SIEM/XDR** | Wazuh (roadmap) | Security monitoring and incident detection |
| **Encryption** | OpenSSL, Let's Encrypt | TLS/SSL certificate management |

### 7.2 Infrastructure Components

**Lab Environment**:
- **Hypervisor**: VirtualBox / VMware
- **Kali Linux VM**: 4 vCPU, 8GB RAM, 50GB storage
- **Docker Host**: Docker 24.x, Docker Compose
- **DVWA Target**: Official DVWA image with MariaDB
- **Network**: NAT network, isolated from production

**Production-Grade Components** (Design Reference):
- **Web Server**: Nginx with ModSecurity WAF
- **Application Server**: Node.js / Python / Java (business-dependent)
- **Database**: PostgreSQL with TDE
- **Load Balancer**: HAProxy / Nginx Plus
- **Firewall**: pfSense / OPNsense
- **VPN**: WireGuard / OpenVPN

---

## 8. Data Flow and Trust Boundaries

### 8.1 Data Flow Diagram

```
┌────────────┐         HTTPS (TLS 1.3)          ┌────────────┐
│   User     │───────────────────────────────────▶│    WAF     │
└────────────┘                                    │  (Edge)    │
                                                  └──────┬─────┘
                                                         │
                                                  Filter │ Validate │ Log
                                                         │
                                                  ┌──────▼─────┐
                                                  │   Load     │
                                                  │  Balancer  │
                                                  └──────┬─────┘
                                                         │
                                  ┌──────────────────────┼──────────────────────┐
                                  │                      │                      │
                           ┌──────▼─────┐        ┌──────▼─────┐        ┌──────▼─────┐
                           │  App       │        │  App       │        │  App       │
                           │  Server 1  │        │  Server 2  │        │  Server 3  │
                           └──────┬─────┘        └──────┬─────┘        └──────┬─────┘
                                  │                      │                      │
                                  └──────────────────────┼──────────────────────┘
                                                         │
                                                  ┌──────▼─────┐
                                                  │  Database  │
                                                  │ (Encrypted)│
                                                  └────────────┘
```

### 8.2 Trust Boundaries

| Boundary | Trust Level | Controls |
|----------|-------------|----------|
| **Internet → Edge** | Untrusted → Trusted Edge | WAF, firewall, DDoS protection, TLS |
| **Edge → Internal** | Trusted Edge → Internal | Internal firewall, authentication, authorization |
| **Internal → Data** | Internal → High Trust | Database authentication, encryption, query validation |
| **Management → All** | Administrative → All | MFA, jump boxes, audit logging, privileged access management |

---

## 9. Threat Model Summary

### 9.1 Top Threats Considered

1. **Web Application Attacks**: SQL injection, XSS, CSRF
2. **Network Intrusion**: Unauthorized access, lateral movement
3. **Data Breach**: Exfiltration of sensitive data
4. **Denial of Service**: Availability disruption
5. **Insider Threats**: Malicious or negligent insiders
6. **Supply Chain Attacks**: Third-party compromise

**Full Threat Model**: See [Threat Model Document](threat-model.md)

---

## 10. Compliance Control Mapping

### 10.1 Key Architectural Controls by Framework

**ISO 27001:2022:**
- **A.8.1**: User endpoint devices (EDR, full-disk encryption)
- **A.8.20**: Networks security (firewalls, segmentation)
- **A.8.22**: Segregation of networks (VLANs, DMZ)
- **A.8.24**: Use of cryptography (TLS 1.3, AES-256)

**SOC 2:**
- **CC6.6**: Logical and physical access - network security
- **CC6.7**: Transmission of data (encryption in transit)
- **CC7.2**: System monitoring (SIEM, logging)

**GDPR:**
- **Article 25**: Privacy by design and default
- **Article 32**: Security of processing (encryption, pseudonymization)

**DPDPA:**
- **Section 8**: Security safeguards (technical and organizational)

---

## 11. Related Documents

- [Lab Environment Setup](../INFRASTRUCTURE/kali-linux-setup.md)
- [Threat Model](threat-model.md)
- [Network Topology](../INFRASTRUCTURE/network-topology.md)
- [DevSecOps Architecture](../../devsecops/ci-cd-security-gates.md)

---

**Architecture Owner**: CISO / Security Architect  
**Last Updated**: January 2026  
**Next Review**: January 2027
