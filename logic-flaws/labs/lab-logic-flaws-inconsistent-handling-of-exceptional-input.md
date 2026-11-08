# Lab: Inconsistent handling of exceptional input

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-handling-of-exceptional-input

**Lab idea:** Account registration processes an exceptionally long email address differently across application components, affecting the account's access. The challenge practices spotting inconsistent data handling and validation at component boundaries.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. While proxying traffic through Burp, open the lab and go to the "Target" > "Site map" tab.
2. Click "Session is not running" to start the content discovery.
3. Try to browse to /admin .
4. Go to the account registration page.
- …
6. Register a new account with another long email address, but this time include dontwannacry.com as a subdomain in your email address as follows…
7. Go to the email client and click the link in the confirmation email that you have received.
8. Go to the admin panel and delete carlos to solve the lab.

## Payloads / key values
- `/admin`
- `DontWannaCry`
- `@YOUR-EMAIL-ID.web-security-academy.net`
- `very-long-string@YOUR-EMAIL-ID.web-security-academy.net`
- `very-long-string`
- `dontwannacry.com`
- `very-long-string@dontwannacry.com.YOUR-EMAIL-ID.web-security-academy.net`
- `m`
- `@dontwannacry.com`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Inconsistent handling of exceptional input](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-handling-of-exceptional-input)
