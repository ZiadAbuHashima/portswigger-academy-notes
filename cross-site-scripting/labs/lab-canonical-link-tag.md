# Lab: Reflected XSS in canonical link tag

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-canonical-link-tag](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-canonical-link-tag)

## Lab idea

User input is reflected in a canonical link element while angle brackets are escaped. The challenge practices inspecting less-obvious HTML attribute contexts and assessing whether the remaining context permits unsafe interpretation.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Visit the following URL, replacing YOUR-LAB-ID with your lab ID: https://YOUR-LAB-ID.web-security-academy.net/?%27accesskey=%27x%27onclick=%27alert(1) This sets the X key as an access key…
2. To trigger the exploit on yourself, press one of the following key combinations:

## Payloads / key values
- `YOUR-LAB-ID`
- `https://YOUR-LAB-ID.web-security-academy.net/?%27accesskey=%27x%27onclick=%27alert(1)`
- `X`
- `alert`
- `ALT+SHIFT+X`
- `CTRL+ALT+X`
- `Alt+X`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS in canonical link tag](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-canonical-link-tag)
