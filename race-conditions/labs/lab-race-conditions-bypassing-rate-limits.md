# Lab: Bypassing rate limits via race conditions

**Official lab:** [Lab: Bypassing rate limits via race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-bypassing-rate-limits)

**Lab idea:** The login flow applies a rate limit, but its handling of simultaneous attempts leaves a timing-related weakness. This challenge practices recognizing shared state in an authentication control and assessing how concurrency can affect enforcement of a limit. [1]

[1]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-bypassing-rate-limits "Lab: Bypassing rate limits via race conditions"

## Vulnerability in brief
Race conditions are a web vulnerability class closely related to business-logic flaws. They occur when concurrent requests interact with shared application data without adequate safeguards. If operations overlap while the data is in a temporary, incomplete state, they can collide and cause behavior that would not occur when requests run one at a time. The brief period in which this collision is possible is the **race window**. Limit-overrun cases are a form of time-of-check to time-of-use (TOCTOU) flaw: a check and the later state change are not protected as one operation.

## Solution idea
1. Experiment with the login function by intentionally submitting incorrect passwords for your own account.
2. Observe that if you enter the incorrect password more than three times, you're temporarily blocked from making any more login attempts for the same account.
3. Try logging in using another arbitrary username and observe that you see the normal Invalid username or password message.
4. Deduce that the number of failed attempts per username must be stored server-side.
- …
6. Launch the attack.
7. Wait for the account lock to reset, then log in as carlos using the identified password.
8. Access the admin panel and delete the user carlos to solve the lab.

## Payloads / key values
- `Invalid username or password`
- `POST /login`
- `Invalid username and password`
- `password`
- `%s`
- `username`
- `carlos`
- `examples/race-single-packet-attack.py`
- `wordlists.clipboard`

## Official source
- [PortSwigger Academy: Lab: Bypassing rate limits via race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-bypassing-rate-limits)
