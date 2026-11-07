# Lab: Bypassing rate limits via race conditions

**Official lab:** [Lab: Bypassing rate limits via race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-bypassing-rate-limits)

**Lab idea:** The login flow applies a rate limit, but its handling of simultaneous attempts leaves a timing-related weakness. This challenge practices recognizing shared state in an authentication control and assessing how concurrency can affect enforcement of a limit. [1]

[1]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-bypassing-rate-limits "Lab: Bypassing rate limits via race conditions"
