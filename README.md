# Web Security: Pen Testing Live Targets 

> Objective: Identify vulnerabilities in 3 different versions of a website: blue, green, and red.

This project documents web vulnerabilities, each originating from a different website, along with their corresponding exploitation techniques. Among the six potential exploits considered—Username Enumeration, Insecure Direct Object Reference (IDOR), SQL Injection (SQLi), Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), and Session Hijacking/Fixation—three were successfully identified. Despite the relative simplicity, this project serves as a compelling demonstration of how easily websites and web-based applications can be exploited.


## Blue

### Vulnerability: Session Hijacking

#### Exploitation Steps:
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

![Session Hijacking Blue](https://github.com/CyberDefender369/Pen-Testing-Live-Targets/assets/96165986/318f8e00-791d-4c62-88a6-23d4f4d70991)

#### Prevention: 
- Ensure the session ID is a long and unique number to eliminate random guessing.
- Confirm that the user-agent string used for a request matches the user-agent string at login.
- Determine if the origin of a request is coming from the source origin, as well as where the request is going.


## Green

### Vulnerability: Cross-Site Scripting (XSS)

#### Exploitation Steps: 
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

![XSS Green](https://github.com/CyberDefender369/Web-Security-Pen-Testing-Live-Targets/assets/96165986/43148303-e7ba-415e-8d42-17417af126fe)

#### Prevention:
- Validate user input.
- Sanitize data before output.
- Encode output.
- Apply allowlists and blocklists. 
  

## Red

### Vulnerability: Insecure Direct Object Reference (IDOR)

#### Exploitation Steps: 
- Change URL Parameter:
  - Change the URL parameter from ?id=1 to ?id=2.
- Increment the Number:
  - Increment the number by 1 until you reach 12.
- Identify Sensitive Information:
  - Note that ?id=10 and ?id=11 return sensitive information that was not intended for public disclosure.

![IDOR Red](https://github.com/CyberDefender369/Web-Security-Pen-Testing-Live-Targets/assets/96165986/76ad34dd-9987-404c-8012-4ecde7d2b1ec)

#### Prevention:
- Encrypt data at rest and data in motion.
- Employ strong ciphers.
- Only gather required data.
- Deny by default.
- Alerts.
