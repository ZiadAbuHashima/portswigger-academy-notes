# Lab: High-level logic vulnerability

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-high-level

**Lab idea:** The purchase flow fails to validate an unexpected quantity in a way that affects the final order total. It practices reasoning about the semantics of transaction inputs and their effect on related cart calculations.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, log in and add a cheap item to your cart.
2. In Burp, go to "Proxy" > "HTTP history" and study the corresponding HTTP messages.
3. Go to the "Intercept" tab and turn on interception.
4. Change the quantity parameter to an arbitrary integer, then forward any remaining requests.
5. Repeat this process, but request a negative quantity this time.
6. Request a suitable negative quantity to remove more units from the cart than it currently contains.
7. Add the leather jacket to your cart as normal.
8. Place the order to solve the lab.

## Payloads / key values
- `POST /cart`
- `quantity`

## Official source
- [PortSwigger Academy: Lab: High-level logic vulnerability](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-high-level)
