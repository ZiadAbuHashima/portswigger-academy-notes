# Lab: Partial construction race conditions

**Official lab:** [Lab: Partial construction race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-partial-construction)

**Lab idea:** During account registration, a race condition in the construction of user state can undermine email verification and allow registration with an email address the registrant does not own. This challenge practices analyzing partially initialized state in a multi-step registration workflow. [1]

[1]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-partial-construction "Lab: Partial construction race conditions"

## Vulnerability in brief
Race conditions are a web vulnerability class closely related to business-logic flaws. They occur when concurrent requests interact with shared application data without adequate safeguards. If operations overlap while the data is in a temporary, incomplete state, they can collide and cause behavior that would not occur when requests run one at a time. The brief period in which this collision is possible is the **race window**. Limit-overrun cases are a form of time-of-check to time-of-use (TOCTOU) flaw: a check and the later state change are not protected as one operation.

## Solution idea
1. Study the user registration mechanism.
2. In Burp, from the proxy history, notice that there is a request to fetch /resources/static/users.js .
3. Study the JavaScript and notice that this dynamically generates a form for the confirmation page, which is presumably linked from the confirmation email.
4. In Burp Repeater, create an equivalent request to what your browser might send when clicking the confirmation link.
- …
6. Make a note of the username from one of these responses.
7. In the browser, log in using this username and the static password you used in the registration request.
8. Access the admin panel and delete carlos to solve the lab.

## Payloads / key values
- `@ginandjuice.shop`
- `/resources/static/users.js`
- `POST`
- `/confirm`
- `POST /confirm?token=1 HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: x-www-form-urlencoded Content-Length: 0`
- `token`
- `Incorrect token: <YOUR-TOKEN>`
- `Missing parameter: token`
- `Forbidden`
- `null`
- `POST /confirm?token[]=`
- `Invalid token: Array`
- `POST /register`
- `POST /confirm?token=1 HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Cookie: phpsessionid=YOUR-SESSION-ID Content-Type: application/x-www-form-urlencoded Content-Length: 0`
- `Account already exists with this name`
- `username`
- `%s`
- `email`
- `password`
- `examples/race-single-packet-attack.py`
- `gate`
- `Account registration for user <USERNAME> successful`
- `User4`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Partial construction race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-partial-construction)
