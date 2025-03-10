# Web Security: Pen Testing Live Targets 

> Objective: Identify vulnerabilities in 3 different versions of a website: blue, green, and red.

This project documents web vulnerabilities, each originating from a different website, along with their corresponding exploitation techniques. Among the six potential exploits considered—Username Enumeration, Insecure Direct Object Reference (IDOR), SQL Injection (SQLi), Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), and Session Hijacking/Fixation—three were successfully identified. Despite the relative simplicity, this project serves as a compelling demonstration of how easily websites and web-based applications can be exploited.

## Blue

### Vulnerability: Session Hijacking

#### Exploitation Steps
- Open Browsers:
  - Launch Firefox (target browser) and Edge (attacker browser).
- Login on Firefox:
  - In Firefox, log in with your credentials.
- Obtain Session ID on Firefox:
  - Change the URL in Firefox from https://35.184.88.145/blue/public/staff/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php.
  - Note down the current session ID.
- Access Change Session ID on Edge:
  - In Edge, change the URL from https://35.184.88.145/blue/public/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php.
- Update Session ID on Edge:
  - In Edge, input the session ID obtained from Firefox.
- Access Target Page on Edge:
  - In Edge, change the URL back to https://35.184.88.145/blue/public/index.php.
- Check Login:
  - Verify that no credentials are needed to log in.

![Session Hijacking Blue](https://github.com/user-attachments/assets/6d65d72a-68fa-4066-a234-1a53a3317002)

#### Prevention
- Generate a Secure Session ID:
  - Make sure the session ID is a long and unique number to eliminate random guessing.
- Verify User-Agent String:
  - Ensure that the user-agent string used for a request matches the user-agent string at login.
- Verify Request Origin:
  - Ensure that the origin of a request is coming from the source origin, as well as where the request is going.

## Green

### Vulnerability: Cross-Site Scripting (XSS)

#### Exploitation Steps
- Go to the Globitek Contact Page:
  - Navigate to the Globitek contact page.
- Enter Details and Script:
  - Enter your name, email, and the script: <script>alert('Graciano found the XSS!');</script>.
- Login with Credentials:
  - Log in with your credentials.
- Click Feedback Tab:
  - Click the feedback tab in the menu page.
- Verify Payload:
  - Verify that the payload is displayed.

![Green](https://github.com/user-attachments/assets/7fe92aaf-79d8-4f63-ac89-a586cf7e8cc3)

#### Prevention
- Validate User Input:
  - Ensure that all user input is validated to prevent unauthorized access to sensitive information.
- Sanitize Data Before Output:
  - Sanitize the data before output to remove any malicious input.
- Encode Output:
  - Encode the output to ensure it is properly formatted.

## Red

### Vulnerability: Insecure Direct Object Reference (IDOR)

#### Exploitation Steps
- Change URL Parameter:
  - Change the URL parameter from ?id=1 to ?id=2.
- Increment the Number:
  - Increment the number by 1 until you reach 12.
- Identify Sensitive Information:
  - Note that ?id=10 and ?id=11 return sensitive information that was not intended for public disclosure.

![Red](https://github.com/user-attachments/assets/814f7627-0be7-4fba-86a6-d453a2b02803)

#### Prevention
- Encrypt Data:
  - Encrypt data both at rest and in motion to ensure its confidentiality.
- Employ Strong Ciphers:
  - Use robust encryption ciphers to ensure data integrity.
- Deny by Default:
  - Implement a default-deny policy to restrict unauthorized access.
