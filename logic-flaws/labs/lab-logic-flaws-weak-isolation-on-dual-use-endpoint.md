# Lab: Weak isolation on dual-use endpoint

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-weak-isolation-on-dual-use-endpoint

**Lab idea:** An account-management endpoint makes an unsafe assumption about a user's privilege level based on request input. This lab practices checking how a dual-use function isolates identity, authorization, and the account affected by a change.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, log in and access your account page.
2. Change your password.
3. Study the POST /my-account/change-password request in Burp Repeater.
4. Notice that if you remove the current-password parameter entirely, you are able to successfully change your password without providing your current one.
5. Observe that the user whose password is changed is determined by the username parameter.
6. Log out and notice that you can now successfully log in as the administrator using the password you just set.
7. Go to the admin panel and delete carlos to solve the lab.

## Payloads / key values
- `POST /my-account/change-password`
- `current-password`
- `username`
- `username=administrator`
- `administrator`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Weak isolation on dual-use endpoint](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-weak-isolation-on-dual-use-endpoint)
