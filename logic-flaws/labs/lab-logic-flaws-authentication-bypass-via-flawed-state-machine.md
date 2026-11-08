# Lab: Authentication bypass via flawed state machine

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-flawed-state-machine

**Lab idea:** The login process makes an unsafe assumption about the sequence of authentication events and role selection. The challenge practices assessing whether server-side authorization remains correct when a multi-stage workflow does not follow its expected path.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, complete the login process and notice that you need to select your role before you are taken to the home page.
2. Use the content discovery tool to identify the /admin path.
3. Try browsing to /admin directly from the role selection page and observe that this doesn't work.
4. Log out and then go back to the login page.
5. Forward the POST /login request.
6. Delete carlos to solve the lab.

## Payloads / key values
- `/admin`
- `POST /login`
- `GET /role-selector`
- `administrator`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Authentication bypass via flawed state machine](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-flawed-state-machine)
