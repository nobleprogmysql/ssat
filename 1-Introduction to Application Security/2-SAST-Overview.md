https://owasp.org/www-community/Source_Code_Analysis_Tools

### 1. **Introduction to SAST**

- **What is SAST?**
  - **SAST** stands for **Static Application Security Testing**.
  - It is a method used to review the **source code** of software in order to identify potential vulnerabilities.
  - SAST tests the **actual source code** by reviewing each line to detect security issues.

### 2. **How SAST Works**

- **Languages and Tools**
  - SAST can be applied to a variety of programming languages, with different tools supporting different languages.
  - A link to a list of SAST tools and the languages they support is referenced (Nixon Resources).
  
- **Integration with CI/CD Pipelines**
  - SAST is well-suited for integration into **CI/CD pipelines** (Continuous Integration and Continuous Delivery).
  - This allows the testing to be run repeatedly and automatically without affecting the development process or requiring downtime.

- **Static Nature of SAST**
  - As a static testing method, SAST does not require the application to be running for the tests to be executed.
  - This means that SAST tools can test the code at any point in the development process, even when the application isn’t active.

### 3. **Practical Example of SAST Usage**

- **Commit Pipeline Example**
  - A developer commits code into a pipeline, and SAST tools can be implemented to test the commit for vulnerabilities immediately.
  - The **SAST tooling** will check the committed code for vulnerabilities as part of the DevSecOps pipeline.

- **Common Vulnerabilities Detected**
  - SAST can identify common vulnerabilities like **SQL injection** and **buffer overflows**.
  - The goal is to catch vulnerabilities early in the development cycle to prevent them from making it into production.

### 4. **Limitations of SAST**

- **Difficult-to-Test Issues**
  - While SAST is effective for many vulnerabilities, it has limitations:
    - **Access control** issues and **logic flaws** can be difficult to test with SAST tools.
    - These issues typically require **manual testing** to catch more thoroughly.
  
- **False Positives**
  - SAST tools can generate **false positives**, which means they might flag issues that are not actually vulnerabilities.
  - False positives require investigation and can lead to tuning the tools before they are fully deployed in production.

### 5. **Type of Testing: White Box vs Black Box**

- **White Box Testing**
  - SAST is considered **white box testing**, meaning the tester has full visibility into the inner workings of the application, including the source code.
  
- **Black Box Testing**
  - This contrasts with **black box testing**, where the tester does not have access to the inner code of the application and can only test what is exposed to the user (the front-end).

---

This structure maintains the original content while organizing the information into clear sections for easier understanding and reference.