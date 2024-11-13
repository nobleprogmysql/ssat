Course Outline:

1. Introduction to Application Security:

The evolving threat environment for cloud applications
Importance of secure coding practices
Introduction to security testing types:
DAST:Dynamic Analysis Security Testing
SAST:Static Analysis Security Testing
SCA: Software Composition Analysis

2. Deep Dive into Security Scanners:

SAST Tools: Tool Introductions
Semgrep - Rule-based static analysis for vulnerabilities and code quality
Checkov - Framework-agnostic infrastructure as code (IaC) security scanner
SonarQube - Static code analysis platform for security, quality, and code smells
Case Study: Analyzing real-world JavaScript/TypeScript code for vulnerabilities

SCA Tools:
Grype - Vulnerable package detection
Trivy - Vulnerability Scanning
Dependency Track - security platform for package management

3. Scan Reports Analysis and Prioritization:

Understanding scan reports:
Severity levels (Critical, High, Medium, Low)
False positives and how to identify them
Contextualizing vulnerabilities based on code location (test vs production)
Prioritization of vulnerabilities based on risk factors

4. Addressing Security Findings:
Remediation strategies for common vulnerabilities identified by SAST and SCA scans (e.g., XSS, SQL Injection, insecure library versions)
Secure coding best practices in JavaScript/TypeScript
Using Shellcheck to scan shell scripts for security vulnerabilities
Lab: Resolving identified vulnerabilities in sample code and understanding the remediation process

5. Utilizing Security Scanners in CI/CD pipelines:
Integrating SAST and SCA scans into continuous integration/continuous delivery (CI/CD) workflows
Automating vulnerability detection and remediation

