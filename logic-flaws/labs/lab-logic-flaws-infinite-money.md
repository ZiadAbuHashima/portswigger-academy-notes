# Lab: Infinite money logic flaw

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-infinite-money

**Lab idea:** This challenge concerns a logic flaw in a purchasing workflow and practices examining how its transaction rules can be abused to obtain an item despite normal store-credit constraints. The source description gives limited detail, so this note does not assume a more specific mechanism.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. With Burp running, log in and sign up for the newsletter to obtain a coupon code, SIGNUP30 .
2. Add a gift card to your basket and proceed to the checkout.
3. Go to your account page and redeem the gift card.
4. Study the proxy history and notice that you redeem your gift card by supplying the code in the gift-card parameter of the POST /gift-card request.
- …
6. In the Payloads side panel, under Payload configuration , select the payload type Null payloads .
7. Click on Resource pool to open the Resource pool side panel.
8. When the attack finishes, you will have enough store credit to buy the jacket and solve the lab.

## Payloads / key values
- `SIGNUP30`
- `gift-card`
- `POST /gift-card`
- `POST /cart POST /cart/coupon POST /cart/checkout GET /cart/order-confirmation?order-confirmed=true POST /gift-card`
- `GET /cart/order-confirmation?order-confirmed=true`
- `GET /cart/order-confirmation?order-confirmation=true`
- `302`
- `GET /my-account`
- `412`
- `1`

## Official source
- [PortSwigger Academy: Lab: Infinite money logic flaw](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-infinite-money)
