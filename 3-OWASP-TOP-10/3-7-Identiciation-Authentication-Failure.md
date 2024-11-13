### 1. Introduction
- **Greeting and Lecture Introduction**  
  "Hello security gurus. Welcome to this new lecture. In this lecture we are going to learn about the seventh vulnerability in the OWASP top ten category, which is identification and authentication failures."

- **Previous Name and Position of the Vulnerability**  
  "Previously it was named as Broken Authentication and it was at the second position, but now it has been moved to the seventh position."

---

### 2. Understanding Identification and Authentication Failures
- **Definition of Authentication**  
  "Authentication is critical for protecting any application on the internet. Authentication is used to validate whether you can access an application on the internet or not."

- **Example of Authentication**  
  "For example, if you register for Facebook, your identity will be created in Facebook and you will be authenticated once you enter your username and password in Facebook."

- **Consequences of Authentication Failures**  
  "Identification and authentication failures can result in data loss, session hijacking, and many other critical vulnerabilities. Basically, authentication failure will result in compromising your data in that application, and it will also result in loss of your access to your account of that application."

---

### 3. Common Examples of Authentication Weaknesses
- **Brute Force Attacks**  
  "Suppose if an application permits brute force attacks. Now let's first understand what is a brute force attack. These are some of the automated attacks that are used to log in to the application with some leaked passwords. Nowadays, there have been instances where leaked list of passwords are made available on the internet. Hackers use those list to perform brute force attacks on multiple web applications, and if application is vulnerable to brute force attack, then your account will be compromised."

- **Weak or Default Passwords**  
  "Similarly, if the application uses weak or default passwords for example, if there is a default password implemented on SQL server database, or there is any default password left on a server login, then it means that application deployed on that web server is compromised."

- **Weak Forgot Password Processes**  
  "Then the application might use weak or forgotten password process. For example, if forgot password is knowledge based, it means that it asks you to answer a certain question which might be related to your age or related to your family, or related to your personal information. That information can get leaked and can be accessed by hackers. If hackers get that information, then they can use the forgot password functionality on that application to access your account."

- **Session Identifier Leaks**  
  "Then, if the application uses some kind of session identifier in the URL or reuse the session identifiers, then such applications are also susceptible to identification and authentication failures. Because such kind of session identifiers in the URLs can be leaked to the hackers or can be accessed by hackers, and you are then exposed to such hackers, or your account information will be exposed to such hackers."

- **Lack of Multi-factor Authentication (MFA)**  
  "And finally, which is very important, if the application is not implementing multi-factor authentication, then it is at risk as well. Simple example of multi-factor authentication is sending an OTP on your cell phone. So basically, if an application is implementing multi-factor authentication, a one time password will be sent to your cell phone so that application can verify that it is you who is trying to login into that application."

---

### 4. Practical Demonstration with OWASP Juice Shop
- **Introduction to OWASP Juice Shop**  
  "So now let's see this in practical by using OWASP Juice Shop application, I will switch to its documentation website and see one of the challenge related to this category."

- **Selecting a Challenge**  
  "Now this is OWASP Juice Shop documentation website where I have opened broken authentication challenges. As I mentioned, identification and authentication failures was previously named as Broken Authentication. The challenge is that are available in this category are all of these. I will select one of the challenge which is password strength."

- **Challenge Description**  
  "The description of this challenge is we need to log in with the administrator user credentials without previously changing them or applying SQL injection."

- **Setting Up Brute Force Attack**  
  "Now we will try to use burp in this case to log in with the admin credentials by using brute force attack. In order to use a brute force attack, we also need a leaked password list, which I have already identified and is available on GitHub."

- **GitHub Password List**  
  "So this is the Daniel Messler security list GitHub repo where he has provided some default passwords for testing. Now I will provide this URL in the resources section of this lecture, so that you can also use this list to break into admin account."

---

### 5. Brute Force Attack Setup in Burp Suite
- **Configuring Burp Suite**  
  "Let me switch to our OWASP Juice Shop web application that we have installed on our local system, and also configure Burp Suite for that. I will switch now to OS two shop."

- **Using Burp Proxy**  
  "Now this is OWASP Juice Shop website. Let's enable Toxiproxy extension. I will click on extensions link and then I will click on Foxy Proxy. Now let's use proxy defaults for all URLs which we have configured in the previous lectures."

- **Sending the Request to Burp Intruder**  
  "Now let's switch back to Burp Suite. Now. This is our Burp Suite. Let's go to proxy. As you can see, intercept is off. I will switch it on. Now let me switch back to OWASP Juice shop. I will click on account. Then I'll click on login."

- **Entering Dummy Credentials**  
  "Now within login I'll type admin at juice hyphen ssh dot op. And I'll type some password. And as you can see this is just dummy password. And I'll click on login."

- **Intercepting and Forwarding the Request**  
  "Let's switch back to Burp proxy. To intercept this request I'll just forward the existing request. As you can see, this is the login URL on which OWASP Juice Shop is sending the credentials that we have just entered."

---

### 6. Running the Brute Force Attack
- **Sending Request to Intruder**  
  "Now let's send this to intruder. I'll send this request to intruder. And I'll switch to intruder. Now what is intruder? Intruder is a service in burp, which lets you to enter some automated credentials at specific places in your request."

- **Marking Payload Position**  
  "I will just clear all the existing locations where it is automatically entering the credentials. We just need to identify the password of the admin. So I will select this dummy text that we entered in password and I'll click on Add Payload marker."

- **Selecting the Payload (Leaked Password List)**  
  "Now let's select the payload that we want to pass which is from the GitHub list that we just saw. I'll click on payload. Now we need to paste that list here. So I'll switch back to GitHub list. Let's copy this list I'll start copy from the top."

- **Paste and Start Attack**  
  "Now there are 1041 leaked passwords. I will right click on it and copy it. I'll switch back to Burpsuite. I'll paste it here. And as you can see, all the leaked passwords have been copied."

- **Waiting for Attack to Complete**  
  "Let's start the attack by clicking on Start Attack button. As you can see, burp has started sending the request by entering those leaked passwords at the payload marker. Let's wait for some time in order to verify if our request is successful or not."

---

### 7. Analyzing the Results
- **Identifying the Correct Password**  
  "We need to click on length column. If there is any change in length, you will see that particular request is successful. As of now, you can see that the length of the request is constant, which is 385. Let's wait for burp to complete all the request."

- **Password Identification**  
  "As the number of payloads are more and in community Edition, the speed of request will also be slow. I have optimized this list a bit. I have removed some of the extra passwords, because of which it was taking a lot of time to find the exact password which was working as of now for unsuccessful passwords, we were getting a length as 385 bytes, but if I click on this column, you will see that for one of the password, which is admin 123, we have received a different length in bytes, which is 1180 for the response."

- **Successful Login**  
  "In this case, if I see the response for this request, you will see that we have received an authentication token for the admin. It means that this password was successful."

---

### 8. Remediation and Prevention
- **Preventive Measures**  
  "Now let's see the remediation or prevention steps to avoid such failures in an application. The first important one is to implement multi-factor authentication to prevent brute force attacks for credentials."

- **Other Remediation Steps**  
  - "Avoid default credentials for applications, always reset the credentials once you install a new application or a service."
  - "Implement checks to avoid weak or insecure passwords, so policies should be implemented to make sure that all the users of that application should follow strong password policy, and should keep this check on a regular basis."
  - "Limit failed login attempts. If a user fails the number of login attempts, it can be 3 or 4, then its account should be locked and then a proper password reset mechanism should be followed."
  - "Random session user ID should be used and it should not be guessable. It should not be used within

 the URL. This is also called session IDs with high entropy applications, having session IDs with high entropy are less vulnerable to such kind of failures."

---

### 9. Conclusion
- **Summary and Closing**  
  "I hope you have now understood what is identification and authentication failures also called as broken authentication. I hope you have enjoyed the practical as well. Thanks for watching. See you in the next lecture."