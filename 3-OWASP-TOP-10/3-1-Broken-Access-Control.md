## To run juice shop on local as a docker container
docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
## juice shop git hub page
https://github.com/juice-shop/juice-shop

## Juice shop

Here is the transcript organized into sections without summarizing the original content:

---

### 1. **Introduction**
- **Welcome and Overview:**
  - "Hello security gurus, welcome to this new lecture."
  - In this lecture, we will do a deep dive into the OWASP Top Ten vulnerabilities, with hands-on demos using the OWASP Juice Shop application.
  - We will identify each vulnerability within the Juice Shop app, see how it looks in a web application, and learn remediation steps.

---

### 2. **Introduction to Broken Access Control**
- **Definition of Access Control:**
  - Access control is used to enforce policies ensuring users cannot perform actions outside their intended permission boundaries.
  - If access control is broken, it may lead to:
    - Unauthorized information disclosure.
    - Modification or destruction of data.
    - Performing business functions outside of the user's scope.
  - Example: If a normal user can perform actions of an admin, this is a broken access control scenario.

- **Common Examples of Broken Access Control:**
  - **S3 Bucket Access Control Leak:**
    - Instances where an S3 bucket containing sensitive data was made public when it should only be accessible to specific users.
  - **Elevation of Privilege:**
    - A user may access admin functions or another user’s data, which is also a broken access control example.

---

### 3. **Practical Example in OWASP Juice Shop**
- **Introduction to the OWASP Juice Shop:**
  - The demo will involve solving a broken access control challenge from the OWASP Juice Shop documentation.

- **Selecting the Challenge:**
  - On the OWASP Juice Shop documentation website, navigate to the "Broken Access Control" challenge.
  - The selected challenge is: "Post some feedback in another user's name."

- **Steps to Demonstrate Broken Access Control:**
  1. **Register a User:**
     - Register a new customer with a test email (`test@test.com`) and password.
     - Successful registration and login.
  2. **Submit Feedback as Another User:**
     - Go to the "Customer Feedback" section and notice that the current user’s email ID is pre-filled.
     - Use Burp Suite to intercept the request before submission.
     - Modify the user ID in the intercepted request (change it from `21` to `20`).
     - Submit feedback on behalf of another user.
     - Request is successfully processed despite the fact it was submitted under a different user ID.

- **Completion of the Challenge:**
  - Successfully posted feedback on behalf of another user, demonstrating the broken access control vulnerability.

---

### 4. **Explaining the Vulnerability**
- **Definition of Broken Access Control:**
  - Broken access control occurs when users can act outside the scope of their permissions.
  - Examples include:
    - Accessing the admin section.
    - Adding products to another user’s shopping cart.

- **Conclusion of Practical Example:**
  - The challenge of posting feedback on behalf of another user was successfully completed, demonstrating the presence of broken access control.

---

### 5. **Remediation Steps for Broken Access Control**
- **Prevention Steps:**
  1. **Deny by Default:**
     - Resources that are not public should be denied access by default. Only public resources should be openly accessible.
     - Specific access should be granted based on need.
  
  2. **Minimize Cross-origin Resource Sharing (CORS):**
     - Limit the use of CORS and ensure a consistent access control mechanism across the application.
  
  3. **Disable Web Server Directory Listing:**
     - Disable directory listing on the web server and avoid leaving backup files accessible.
  
  4. **Logging and Alerting on Access Control Failures:**
     - Log all access control failures and alert application admins when repeated failures occur.
  
  5. **Rate Limiting API:**
     - Limit API calls to prevent brute force attacks. Rate limiting can mitigate the impact of automated attacks and reduce the chances of exploitation.
  
  - **Additional Prevention Measures:**
    - Other prevention steps exist, but the above are some of the most effective and simplest.

---

### 6. **Conclusion**
- **Final Remarks:**
  - The lecture covered the OWASP Top Ten vulnerability of broken access control.
  - Demonstrated how a common vulnerability can be exploited in the Juice Shop app.
  - Provided remediation steps to prevent such vulnerabilities in real-world applications.
  - Stay tuned for more OWASP Top Ten vulnerabilities, with practical demos on the Juice Shop application.

- **Closing:**
  - "Thanks for watching. See you in the next lecture."

---

This organization keeps the original content intact and structures it for easier navigation.