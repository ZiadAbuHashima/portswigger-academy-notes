# Lab: Low-level logic flaw

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-low-level

**Lab idea:** This purchasing challenge involves price and quantity calculations that encounter numeric bounds in the back-end. It practices considering integer limits and arithmetic behavior when validating transaction inputs.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, log in and attempt to buy the leather jacket.
2. In Burp Repeater, notice that you can only add a 2-digit quantity with each request.
3. Go to Intruder and set the quantity parameter to 99 .
4. In the Payloads side panel, select the payload type Null payloads .
- …
6. When the Intruder attack finishes, go to the POST /cart request in Burp Repeater and send a single request for 47 jackets.
7. Use Burp Repeater to add a suitable quantity of another item to your cart so that the total falls between $0 and $100.
8. Place the order to solve the lab.

## Payloads / key values
- `POST /cart`
- `quantity`
- `99`
- `323`
- `1`
- `47`
- `-$1221.96`

## Official source
- [PortSwigger Academy: Lab: Low-level logic flaw](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-low-level)
