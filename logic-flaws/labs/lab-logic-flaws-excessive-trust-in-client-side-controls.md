# Lab: Excessive trust in client-side controls

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-excessive-trust-in-client-side-controls

**Lab idea:** A purchasing workflow inadequately validates a user-supplied value that affects the item price. The challenge practices assessing whether transaction-critical values are independently validated by the server rather than trusted from the client.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, log in and attempt to buy the leather jacket.
2. In Burp, go to "Proxy" > "HTTP history" and study the order process.
3. In Burp Repeater, change the price to an arbitrary integer and send the request.
4. Repeat this process to set the price to any amount less than your available store credit.
5. Complete the order to solve the lab.

## Payloads / key values
- `price`
- `POST /cart`

## Official source
- [PortSwigger Academy: Lab: Excessive trust in client-side controls](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-excessive-trust-in-client-side-controls)
