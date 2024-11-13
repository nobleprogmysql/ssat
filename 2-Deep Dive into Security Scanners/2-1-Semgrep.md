https://semgrep.dev/docs/getting-started/cli

## Install semgrep 
sudo snap install semgrep

## Run semgrep scan on an existing project
cd to code directory
semgrep scan --sarif --output=scan-results.sarif


Sure! Here's a structured 20-minute lecture on **Semgrep Static Security Scanning**, which you can use to demonstrate the tool to a class of students. The lecture covers the fundamentals of Semgrep, its features, and practical demonstrations on how to use it for static security scanning. The demonstration will focus on how Semgrep can be used to identify vulnerabilities and code quality issues in a sample codebase.

---

### **Lecture: Semgrep Static Security Scanning**

---

#### **Introduction (2 minutes)**

1. **Opening Question:**
   - Ask the class: "What is static code analysis, and why is it important in application security?"
   - (Expected Answer: Static code analysis involves analyzing source code for security vulnerabilities, bugs, or potential risks without executing the program. It helps identify issues early in the development process.)

2. **What is Semgrep?**
   - **Semgrep** is a powerful, open-source, static analysis tool that is used to detect security vulnerabilities, bugs, and code quality issues in source code. 
   - It works by applying pattern matching to the code and can be used across a variety of programming languages, including Python, JavaScript, Go, Java, and more.
   - **Key Advantage**: Unlike traditional static analysis tools, Semgrep allows for very **fine-grained control** over the patterns being searched, and it provides easy integration into developer workflows.
   
3. **Purpose of the Lecture:**
   - In this session, we will learn how Semgrep works, how it helps detect security vulnerabilities, and how to run it on a sample codebase.

---

#### **Section 1: Why Static Security Analysis is Important (3 minutes)**

1. **Why Analyze Code Statically?**
   - **Detect Vulnerabilities Early**: By analyzing the code for vulnerabilities before the software is even executed, we can prevent many types of security issues, such as injection attacks, insecure data handling, and XSS.
   - **Speed**: Static analysis allows you to identify problems without needing to run the application, which is much faster than dynamic analysis (e.g., penetration testing).
   - **Cost Savings**: Detecting vulnerabilities in the early stages of development is much cheaper than finding them after deployment.

2. **Common Vulnerabilities Detected in Static Analysis**:
   - SQL Injection
   - Cross-Site Scripting (XSS)
   - Command Injection
   - Improper Input Validation
   - Hardcoded Secrets
   - Insecure Cryptography Usage

---

#### **Section 2: Features of Semgrep (5 minutes)**

1. **Overview of Semgrep**:
   - **Pattern-based**: Semgrep uses patterns to scan code for specific issues. You can either use pre-defined patterns (rules) or create custom ones to detect vulnerabilities.
   - **Lightweight and Fast**: It is designed to be fast and easy to use, with no complicated setup.
   - **Language Support**: Semgrep supports multiple languages like Python, JavaScript, Go, Ruby, Java, PHP, etc.
   - **Easy Integration**: It integrates easily into CI/CD pipelines, making it useful for continuous security scanning.
   
2. **Pre-built Rules**:
   - Semgrep comes with a large collection of pre-built rules for common security and quality issues, contributed by the community.
   - **Example**: Detection of insecure `eval()` calls in JavaScript or hardcoded passwords in Python files.

3. **Custom Rules**:
   - Semgrep also allows users to write custom patterns to target specific security concerns relevant to their project or organization.
   - Writing custom rules is simple and doesn’t require deep knowledge of the tool—just basic understanding of pattern syntax.

4. **How Semgrep Works**:
   - Semgrep scans your source code and looks for patterns based on the rules you provide (either built-in or custom).
   - When a pattern match is found, it flags the issue with information about where the issue occurred, making it easy for developers to fix.

---

#### **Section 3: Demonstrating Semgrep (7 minutes)**

1. **Set Up Semgrep**:
   - **Installation**: 
     - You can install Semgrep using `pip`:
       ```bash
       pip install semgrep
       ```
     - Alternatively, you can use the online platform, **Semgrep Live**, to run Semgrep directly on your code without installation.

2. **Using Semgrep on a Codebase**:
   - Let’s assume we have a simple codebase that contains a security vulnerability, such as a hardcoded password.

   - **Example Code (Python)**:
     ```python
     # Example vulnerable code with hardcoded password
     def authenticate_user():
         password = 'mysecretpassword'  # Hardcoded password
         if user_input == password:
             return True
         else:
             return False
     ```

   - **Step-by-step demonstration**:
     - Run a pre-built rule to detect hardcoded passwords:
       ```bash
       semgrep --config=python/hardcoded-password <path-to-your-code>
       ```
     - **Output**: Semgrep will highlight the line where the hardcoded password is found, along with a description of the vulnerability.

     Example output:
     ```bash
     <path-to-your-code>/auth.py
     5:     password = 'mysecretpassword'  # Hardcoded password
         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
     Found: Hardcoded password found
     ```

3. **Interpreting Results**:
   - Semgrep will display the filename, line number, and a brief description of the issue. 
   - It also suggests actions or points out the relevant pattern that was matched, allowing developers to quickly locate and resolve security issues.

4. **Running Semgrep on Multiple Files**:
   - Semgrep can scan entire directories or specific files. Example:
     ```bash
     semgrep --config=python/hardcoded-password ./
     ```
     This command will scan all files in the current directory and subdirectories.

5. **Custom Rule Example**:
   - You can write your own rules to catch specific issues. For example, let’s create a rule to check for the usage of `eval()` (a common JavaScript security vulnerability).

   - **Custom Rule (YAML)**:
     ```yaml
     rules:
     - id: eval-detection
       pattern: eval($X)
       message: 'Avoid using eval()'
       severity: WARNING
     ```

   - **Running the custom rule**:
     ```bash
     semgrep --config=eval-detection <path-to-your-js-code>
     ```

6. **GitHub Integration**:
   - Semgrep can be integrated into your GitHub repository to automatically run scans on pull requests or code commits. This ensures that vulnerabilities are caught early.

---

#### **Section 4: Best Practices for Using Semgrep (3 minutes)**

1. **Integrate Semgrep into CI/CD Pipelines**:
   - Automating Semgrep scans as part of your build process ensures that every code change is checked for vulnerabilities before it reaches production.
   - Example integration with GitHub Actions or Jenkins can be done easily with available plugins.

2. **Regularly Update Rules**:
   - Static analysis tools, including Semgrep, are constantly evolving. Make sure you regularly update the rules to take advantage of new patterns and security best practices.
   
3. **Review Results Thoroughly**:
   - While Semgrep is very effective, not all matches will be critical. Developers should review the findings carefully to determine whether they represent actual vulnerabilities or false positives.

4. **Write Custom Rules for Specific Needs**:
   - As you gain experience with the tool, consider writing custom rules that match your organization's specific security policies or coding standards.

---

#### **Conclusion (2 minutes)**

1. **Summary**:
   - **Semgrep** is a powerful, lightweight, and easy-to-use static analysis tool that helps identify security vulnerabilities early in the development process.
   - By using **pre-built rules** or writing **custom rules**, Semgrep can scan code for common vulnerabilities like hardcoded passwords, unsafe eval usage, SQL injection, and more.
   - It integrates well with CI/CD pipelines and provides developers with actionable feedback to secure their code.

2. **Final Thought**:
   - **Security is a shared responsibility** in software development, and tools like Semgrep empower developers to proactively identify and fix issues, making applications more secure.

---

#### **Q&A (Optional)**

- Open the floor for any questions about Semgrep, its features, or how it can be applied in real-world development environments.

---

This structure provides a concise yet informative lecture on Semgrep, covering both the theory and practical use of the tool in real-world security scanning.


## Things to explore ##
# Visual studio extension for semgrep and sarif files
