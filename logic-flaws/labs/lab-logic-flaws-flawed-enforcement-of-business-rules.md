# Lab: Flawed enforcement of business rules

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-flawed-enforcement-of-business-rules

**Lab idea:** The purchasing workflow applies coupon rules inconsistently, allowing discounts to be used in an unintended way. This lab practices examining how business constraints behave across repeated and combined operations.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. Log in and notice that there is a coupon code, NEWCUST5 .
2. At the bottom of the page, sign up to the newsletter.
3. Add the leather jacket to your cart.
4. Go to the checkout and apply both of the coupon codes to get a discount on your order.
5. Try applying the codes more than once.
6. Reuse the two codes enough times to reduce your order total to less than your remaining store credit.

## Payloads / key values
- `NEWCUST5`
- `SIGNUP30`

## Official source
- [PortSwigger Academy: Lab: Flawed enforcement of business rules](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-flawed-enforcement-of-business-rules)
