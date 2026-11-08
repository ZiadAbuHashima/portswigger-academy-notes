# Lab: Limit overrun race conditions

**Official lab:** [Lab: Limit overrun race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-limit-overrun)

**Lab idea:** A purchasing flow can be affected by concurrent processing in a way that permits an unintended purchase price. This challenge practices identifying a business-rule limit and considering how overlapping requests may interact with its enforcement. [1]

[1]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-limit-overrun "Lab: Limit overrun race conditions"

## Vulnerability in brief
Race conditions are a web vulnerability class closely related to business-logic flaws. They occur when concurrent requests interact with shared application data without adequate safeguards. If operations overlap while the data is in a temporary, incomplete state, they can collide and cause behavior that would not occur when requests run one at a time. The brief period in which this collision is possible is the **race window**. Limit-overrun cases are a form of time-of-check to time-of-use (TOCTOU) flaw: a check and the later state change are not protected as one operation.

## Solution idea
1. Log in and buy the cheapest item possible, making sure to use the provided discount code so that you can study the purchasing flow.
2. Consider that the shopping cart mechanism and, in particular, the restrictions that determine what you are allowed to order, are worth trying to bypass.
3. In Burp, from the proxy history, identify all endpoints that enable you to interact with the cart.
4. Try to identify any restrictions that are in place on these endpoints.
- …
6. Remove the applied codes and the arbitrary item from your cart and add the leather jacket to your cart instead.
7. Resend the group of POST /cart/coupon requests in parallel.
8. Refresh the cart and check the order total:

## Payloads / key values
- `POST /cart`
- `POST /cart/coupon`
- `Coupon already applied`
- `GET /cart`

## Official source
- [PortSwigger Academy: Lab: Limit overrun race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-limit-overrun)
