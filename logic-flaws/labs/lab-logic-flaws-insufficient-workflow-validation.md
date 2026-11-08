# Lab: Insufficient workflow validation

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-insufficient-workflow-validation

**Lab idea:** The purchasing process makes flawed assumptions about which steps have been completed before an order is finalized. This lab practices checking that server-side state and prerequisites are validated throughout a multi-step workflow.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, log in and buy any item that you can afford with your store credit.
2. Study the proxy history.
3. Add the leather jacket to your basket.
4. In Burp Repeater, resend the order confirmation request.

## Payloads / key values
- `POST /cart/checkout`
- `GET /cart/order-confirmation?order-confirmation=true`

## Official source
- [PortSwigger Academy: Lab: Insufficient workflow validation](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-insufficient-workflow-validation)
