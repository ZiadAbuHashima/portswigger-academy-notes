# Race conditions (TOCTOU)

Race conditions are a web vulnerability class closely related to business-logic flaws. They occur when concurrent requests interact with shared application data without adequate safeguards. If operations overlap while the data is in a temporary, incomplete state, they can collide and cause behavior that would not occur when requests run one at a time. The brief period in which this collision is possible is the **race window**. Limit-overrun cases are a form of time-of-check to time-of-use (TOCTOU) flaw: a check and the later state change are not protected as one operation. [1]

## Main concepts

A limit-overrun flaw can arise when an application checks whether an action is allowed, performs it, and only afterward records that the one-time or limited action has been used. Concurrent requests may all pass the check before the record changes. Race conditions can also occur in hidden multi-step sequences, including sequences within one request, or when different endpoints operate on the same record. The key prerequisite is collision potential: requests must affect shared state, rather than unrelated records. [1]

## Impact

Impact depends on the affected feature. Examples include repeated redemption of a single-use benefit, exceeding a balance or purchase limit, bypassing rate limits, and unintended account or workflow state changes. In sensitive authentication, registration, or payment flows, the result can undermine access controls or business rules. [1]

## High-level detection and assessment

For authorized testing, map the application and prioritize security-critical endpoints that enforce one-time actions, quotas, balances, or multi-step account changes. Identify requests that can touch the same data, establish how the feature behaves sequentially, then compare the result when relevant requests are sent concurrently. Look for deviations in responses and second-order effects, such as unexpected email contents or a changed state after the requests. Timing jitter and very short race windows can make results inconsistent, so findings should be confirmed carefully within the approved test scope. [1]

## Prevention

Make sensitive state transitions atomic using the datastore's concurrency controls. For example, validate payment against the cart value and confirm the order within one database transaction. Avoid mixing state from different storage layers for a security decision, and use integrity constraints such as uniqueness constraints as defense in depth. Keep session state internally consistent, and do not rely on one storage layer, such as sessions, to enforce limits stored in another. [1]

## Lab notes

- [Bypassing rate limits via race conditions](labs/lab-race-conditions-bypassing-rate-limits.md) ([official source][2])
- [Exploiting time-sensitive vulnerabilities](labs/lab-race-conditions-exploiting-time-sensitive-vulnerabilities.md) ([official source][3])
- [Limit overrun race conditions](labs/lab-race-conditions-limit-overrun.md) ([official source][4])
- [Multi-endpoint race conditions](labs/lab-race-conditions-multi-endpoint.md) ([official source][5])
- [Partial construction race conditions](labs/lab-race-conditions-partial-construction.md) ([official source][6])
- [Single-endpoint race conditions](labs/lab-race-conditions-single-endpoint.md) ([official source][7])

The Academy also places a time-sensitive password-reset challenge in this section. Its official description states that the issue is broken cryptography exploited with carefully timed requests, not a race condition itself. [3]

## References

[1]: https://portswigger.net/web-security/race-conditions "Race conditions"
[2]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-bypassing-rate-limits "Lab: Bypassing rate limits via race conditions"
[3]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-exploiting-time-sensitive-vulnerabilities "Lab: Exploiting time-sensitive vulnerabilities"
[4]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-limit-overrun "Lab: Limit overrun race conditions"
[5]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-multi-endpoint "Lab: Multi-endpoint race conditions"
[6]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-partial-construction "Lab: Partial construction race conditions"
[7]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-single-endpoint "Lab: Single-endpoint race conditions"
