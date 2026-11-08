# Lab: Multi-endpoint race conditions

**Official lab:** [Lab: Multi-endpoint race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-multi-endpoint)

**Lab idea:** The purchasing flow contains a race condition involving operations across endpoints and can lead to an unintended price. This challenge practices considering how separate requests that affect related purchase state may overlap. [1]

[1]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-multi-endpoint "Lab: Multi-endpoint race conditions"

## Vulnerability in brief
Race conditions are a web vulnerability class closely related to business-logic flaws. They occur when concurrent requests interact with shared application data without adequate safeguards. If operations overlap while the data is in a temporary, incomplete state, they can collide and cause behavior that would not occur when requests run one at a time. The brief period in which this collision is possible is the **race window**. Limit-overrun cases are a form of time-of-check to time-of-use (TOCTOU) flaw: a check and the later state change are not protected as one operation.

## Solution idea
1. Log in and purchase a gift card so you can study the purchasing flow.
2. Consider that the shopping cart mechanism and, in particular, the restrictions that determine what you are allowed to order, are worth trying to bypass.
3. From the proxy history, identify all endpoints that enable you to interact with the cart.
4. Add another gift card to your cart, then send the GET /cart request to Burp Repeater.
- …
6. Remove the jacket from your cart and add another gift card.
7. In Repeater, try sending the requests again, but this time in parallel.
8. Look at the response to the POST /cart/checkout request:

## Payloads / key values
- `POST /cart`
- `POST /cart/checkout`
- `GET /cart`
- `GET`
- `productId`
- `1`

## Official source
- [PortSwigger Academy: Lab: Multi-endpoint race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-multi-endpoint)
