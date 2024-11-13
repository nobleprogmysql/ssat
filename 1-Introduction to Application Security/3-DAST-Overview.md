https://owasp.org/www-community/Vulnerability_Scanning_Tools

### 1. **Introduction to DAST**

- **What is DAST?**
  - **DAST** stands for **Dynamic Application Security Testing**.
  - Unlike **SAST (Static Application Security Testing)**, which tests the source code, DAST tests the **running application**.
  - DAST is used to identify vulnerabilities in the application while it is running, whether accessed through a **UI (User Interface)** or via an **API**.

### 2. **How DAST Works**

- **Testing the Running Application**
  - DAST works by interacting with the **running application**, either through the **UI** (which may be accessed on a workstation) or directly through the **command line**.
  
- **Common Vulnerabilities Detected**
  - DAST can identify common vulnerabilities such as **SQL injection** and **buffer overflows**.

### 3. **Integration with CI/CD Pipelines**

- **DAST in Pipelines**
  - DAST tools can be integrated into CI/CD pipelines, but they are generally **better suited for manual testing**.
  - They are more accurate when used as part of a **dedicated penetration test**, and the tooling tends to be aimed primarily at **manual testing**.
  
- **Automation Support**
  - Some DAST tools support automation, especially through the command line or within pipelines, but **full automation** is not as prevalent as with SAST tools.
  - Currently, there is not as much **support** for DAST tools in automated pipelines, as they are mainly designed for manual penetration testing.

### 4. **DAST Tools and Commercial vs. Open Source**

- **Lack of Open-Source Options**
  - There is limited open-source support for DAST, and many of the prominent tools are **commercial** offerings.
  
- **Popular DAST Tools**
  - A well-known commercial tool for DAST is **Burp Suite**, which offers a free version, but some functionalities are restricted to the commercial version.
  - An **open-source alternative** is **OWASP ZAP** (Zed Attack Proxy), which is fully functional as it is open-source and also provides **containers** that are well-suited for use in **CI/CD pipelines**.

### 5. **Black Box Testing**

- **DAST as Black Box Testing**
  - DAST is a **black box testing** method, meaning it can only see what is exposed or running in the application.
  - Unlike **SAST**, which is white box testing, DAST cannot see the inner workings or source code of the application and can only test what is accessible via the user interface or API.

### 6. **External Resources and DAST Tools**

- **Resources**
  - A list of **DAST tools** and their features is provided in the external resources section.
  - Most of the prominent tools are **commercial** only, though open-source alternatives such as **OWASP ZAP** are available.

### 7. **Hands-On Demo**

- **DAST Demo**
  - A **hands-on demo** will be conducted to walk through one of the DAST tools, such as **OWASP ZAP**, and demonstrate its use in testing a running application.

---

This organization breaks down the content into sections for easier understanding while keeping all of the original details intact.

