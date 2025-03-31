# OWASP Top 10 (2021) – Web Application Security Risks
The OWASP Top 10 is **a standard awareness document for developers and security professionals**. It **represents the most critical web application security risks**, updated periodically by the OWASP (Open Worldwide Application Security Project).

## 1. The OWASP Top 10 List

| Rank | Category | Core Risk | Description |
| ---- | -------- | --------- | ----------- |
| A01 | Broken Access Control | Unauthorized access to data or actions | Restrictions on what authenticated users are allowed to do are not properly enforced. Users can act as admins, access others’ data, or perform unauthorized actions. |
| A02 | Cryptographic Failures | Inadequate protection of sensitive data | Formerly “Sensitive Data Exposure”. Weak or missing encryption leads to data leaks, such as passwords, credit card numbers, or personal data. |
| A03 | Injection | User input executing unintended code | Unsanitized input is interpreted as code/command by the server (e.g., SQL Injection, Command Injection). |
| A04 | Insecure Design | Flaws from poor architectural decisions | Security flaws built into the application’s design (e.g., lack of threat modeling, missing secure design patterns). |
| A05 | Security Misconfiguration | Incorrect or default security settings | Insecure default settings, unnecessary features, verbose error messages, or unpatched flaws in web servers or frameworks. |
| A06 | Vulnerable and Outdated Components | Use of unsafe or outdated libraries | Using libraries or components with known vulnerabilities or that are no longer maintained (e.g., Log4j, old jQuery). |
| A07 | Identification and Authentication Failures | Broken login/session management | Weak authentication mechanisms (e.g., no MFA, predictable passwords, or broken session handling). |
| A08 | Software and Data Integrity Failures | No trust verification of code/data | The application does not verify the integrity of code or data (e.g., unsigned updates, CI/CD pipeline attacks). |
| A09 | Security Logging and Monitoring Failures | No visibility or delayed incident response | Insufficient logs or monitoring delays detection of attacks or breaches. |
| A10 | Server-Side Request Forgery (SSRF) | Server used to reach internal systems | The application can be tricked into making requests to internal or unintended external systems. |  

<br>

## 2. Why Is the OWASP Top 10 Important?
  - It’s recognized globally as a **baseline for web security**.
  - Used in **secure coding** training, **penetration testing**, and **compliance audits**.
  - Helps teams **prioritize efforts and adopt secure development practices**.  
<br>

## 3. How to Use It
  - Developers: Design and code with these risks in mind.
  - Security teams: Test and validate apps against these categories.
  -	Managers: Use it to plan security education and investment.
  - CI/CD: Integrate automated scanners (e.g., OWASP ZAP, Burp Suite) into pipelines to catch issues early.  
<br>
