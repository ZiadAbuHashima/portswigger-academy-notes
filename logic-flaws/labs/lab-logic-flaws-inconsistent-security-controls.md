# Lab: Inconsistent security controls

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-security-controls

**Lab idea:** Different account features enforce company-employee restrictions inconsistently. This lab practices comparing how an application's controls treat a user's identity and privileges across related account-management functions.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. Open the lab then go to the "Target" > "Site map" tab in Burp.
2. Click "Session is not running" to start the content discovery.
3. Try and browse to /admin .
4. Go to the account registration page.
5. Go to the email client and click the link in the confirmation email to complete the registration.
6. Log in using your new account and go to the "My account" page.
7. Notice that you now have access to the admin panel, where you can delete carlos to solve the lab.

## Payloads / key values
- `/admin`
- `DontWannaCry`
- `anything@your-email-id.web-security-academy.net`
- `@dontwannacry.com`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Inconsistent security controls](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-security-controls)
