# Web Security: Pen Testing Live Targets 

> Objective: Identify vulnerabilities in 3 different versions of a website: blue, green, and red.

This project documents web vulnerabilities, each originating from a different website, along with their corresponding exploitation techniques. Among the six potential exploits considered—Username Enumeration, Insecure Direct Object Reference (IDOR), SQL Injection (SQLi), Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), and Session Hijacking/Fixation—three were successfully identified. Despite the relative simplicity, this project serves as a compelling demonstration of how easily websites and web-based applications can be exploited.


## Blue

Vulnerability: Session Hijacking

Exploitation Steps:
- Two different web browsers are used (Firefox is the target and Edge is attacker).
- Login with credentials on Firefox.
- Change URL on Firefox from https://35.184.88.145/blue/public/staff/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php to obtain current session ID.
- Go to Edge and change URL from https://35.184.88.145/blue/public/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php.
- Change the session ID on Edge to the session ID obtained from Firefox.
- Change URL on Edge back to https://35.184.88.145/blue/public/index.php.
- No credentials were needed to login. 

![Session Hijacking Blue](https://github.com/CyberDefender369/Pen-Testing-Live-Targets/assets/96165986/318f8e00-791d-4c62-88a6-23d4f4d70991)

Prevention: 
- Session ID should be a long and unique number to eliminate random guessing.
- Confirm that the user-agent string used for a request matches the user-agent string at login.
- Determine if the origin of request is coming from source origin, as well as where the request is going. 


## Green

Vulnerability: Cross-Site Scripting (XSS)

Exploitation Steps: 
- Go to the Globitek contact page.
- Enter name, email, and script (<script>alert('Graciano found the XSS!');</script>).
- Login with credentials.
- Click the feedback tab in the menu page.
- Payload is displayed.

![XSS Green](https://github.com/CyberDefender369/Web-Security-Pen-Testing-Live-Targets/assets/96165986/43148303-e7ba-415e-8d42-17417af126fe)

Prevention:
- Validate user input.
- Sanitize data before output.
- Encode output
- Apply allowlists and blocklists. 
  

## Red

Vulnerability: Insecure Direct Object Reference (IDOR)

Exploitation Steps: 
- Change ?id=1 to ?id=2.
- Increase number by 1 until 12 is reached.
- ?id=10 and ?id=11 return senstive information that was not intended for public disclosure.

![IDOR Red](https://github.com/CyberDefender369/Web-Security-Pen-Testing-Live-Targets/assets/96165986/76ad34dd-9987-404c-8012-4ecde7d2b1ec)

Prevention:
- Encrypt data at rest and data in motion.
- Employ strong ciphers.
- Only gather reuqired data.
- Deny by default.
- Alerts.
