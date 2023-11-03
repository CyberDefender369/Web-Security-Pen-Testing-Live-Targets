# Pen Testing Live Targets

Time spent: 4 hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation


## Blue

Vulnerability #1: Session Hijacking

Description: Two different browsers (Firefox is target and Edge is attacker) on the same webpage -> login with credentials on Firefox -> change URL on Firefox from https://35.184.88.145/blue/public/staff/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php to get current session ID -> go to Edge -> change URL from https://35.184.88.145/blue/public/index.php to https://35.184.88.145/blue/public/hacktools/change_session_id.php and change the session ID to the session ID we got from Firefox browser -> change URL on Edge back to https://35.184.88.145/blue/public/index.php -> the Edge browser does not need login credentials to be logged on

<img src="Session Hijacking Blue.gif">


## Green

Vulnerability #1: Cross-Site Scripting (XSS)

Description: Go to contact page -> enter and submit name, email, and script (<script>alert('Graciano found the XSS!');</script>) -> login with credentials -> click the feedback tab in the menu page -> playload is displayed 

<img src="XSS Green.gif">


## Red

Vulnerability #1: Insecure Direct Object Reference (IDOR)

Description: Not logged in changed ?id=1 to ?id=2 and increased number by 1 until 12 is reached -> Blue and Green versions of the website return the same results as the Red version until ?id=10 and ?id=11 are entered -> only the Red version returned sensitive information that was not intended for public disclosure

<img src="IDOR Red.gif">


## Notes

IDOR was tricky. At first, I did not notice that on the Green and Blue version of the Globitek website changing id to id=10 and id=11 would return me back to the salesperson page.  
