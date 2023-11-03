# Pen Testing Live Targets

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

## Notes

IDOR was tricky. At first, I did not notice that changing ?id to ?id=10 and ?id=11 on the Green and Blue versions of the Globitek website would return me to the salesperson page.  


## Blue

Vulnerability: Session Hijacking

Description: Two different browsers (Firefox is target and Edge is attacker) on the same webpage. Login with credentials on Firefox. Change URL on Firefox from https://35.184.88.145/blue/public/staff/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php to obtain current session ID. Go to Edge and change URL from https://35.184.88.145/blue/public/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php. Change the session ID on Edge to the session ID we got from Firefox. Change URL on Edge back to https://35.184.88.145/blue/public/index.php. Edge no longer needs login credentials to be logged on. 

<img src="Session Hijacking Blue.gif">


## Green

Vulnerability: Cross-Site Scripting (XSS)

Description: Go to the Globitek contact page. Enter and submit name, email, and script (<script>alert('Graciano found the XSS!');</script>
). Login with credentials. Click the feedback tab in the menu page and playload is displayed.
<img src="XSS Green.gif">


## Red

Vulnerability: Insecure Direct Object Reference (IDOR)

Description: Not being logged in, change ?id=1 to ?id=2 and increase number by 1 until 12 is reached. Blue and Green versions of the Globitek website return the same results as the Red version until ?id=10 and ?id=11 are entered. Only the Red version returned sensitive information that was not intended for public disclosure.

<img src="IDOR Red.gif">
