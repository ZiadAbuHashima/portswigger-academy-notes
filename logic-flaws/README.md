# Business logic vulnerabilities (BLVs)

Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.[1]

## Main concepts

Common themes include inadequate validation of user-supplied or transaction-critical values; reliance on client-side controls; incorrect assumptions about the order or completion of workflow steps; and inconsistent treatment of the same data or user across components. Flaws may also emerge when separate features interact, such as account-management operations, authorization rules, or purchase processes. A value that appears acceptable to one component may be interpreted differently by another.[1]

## Impact

Impact depends on the affected feature. A flaw in authentication or authorization can expose sensitive accounts, data, or administrative functions. Transaction and purchasing defects can enable fraud or financial loss. Other logic flaws may allow unintended changes or business disruption, even when an attacker does not gain a direct benefit.[1]

## High-level detection and assessment

For authorized testing, first understand the intended rules, roles, and states in the application. Manually map important workflows, then assess whether the server enforces those rules when requests arrive with unexpected values, in unusual sequences, or through combinations of features. Pay attention to mismatches between what the interface permits and what the server accepts, repeated or out-of-order actions, and inconsistent validation across endpoints or components. Because these defects are application-specific and may not appear during normal use, human reasoning and domain knowledge are important; automated scanners can miss them.[1]

## Prevention

Make business rules and assumptions explicit, and ensure developers and testers understand the application domain and how components interact. Enforce sensible input constraints and authorization on the server, verify required state and workflow transitions before performing consequential actions, and do not rely on client-side checks. Keep transaction flows, data flows, dependencies, and side effects understandable and documented. Test realistic edge cases and cross-feature interactions, and use findings to improve design and review practices so similar assumptions are caught earlier.[1]

## Lab notes

- [Authentication bypass via encryption oracle](labs/lab-logic-flaws-authentication-bypass-via-encryption-oracle.md)
- [Authentication bypass via flawed state machine](labs/lab-logic-flaws-authentication-bypass-via-flawed-state-machine.md)
- [Bypassing access controls using email address parsing discrepancies](labs/lab-logic-flaws-bypassing-access-controls-using-email-address-parsing-discrepancies.md)
- [Excessive trust in client-side controls](labs/lab-logic-flaws-excessive-trust-in-client-side-controls.md)
- [Flawed enforcement of business rules](labs/lab-logic-flaws-flawed-enforcement-of-business-rules.md)
- [High-level logic vulnerability](labs/lab-logic-flaws-high-level.md)
- [Inconsistent handling of exceptional input](labs/lab-logic-flaws-inconsistent-handling-of-exceptional-input.md)
- [Inconsistent security controls](labs/lab-logic-flaws-inconsistent-security-controls.md)
- [Infinite money logic flaw](labs/lab-logic-flaws-infinite-money.md)
- [Insufficient workflow validation](labs/lab-logic-flaws-insufficient-workflow-validation.md)
- [Low-level logic flaw](labs/lab-logic-flaws-low-level.md)
- [Weak isolation on dual-use endpoint](labs/lab-logic-flaws-weak-isolation-on-dual-use-endpoint.md)

## References

[1]: https://portswigger.net/web-security/logic-flaws "Business logic vulnerabilities"
[2]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-encryption-oracle "Lab: Authentication bypass via encryption oracle"
[3]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-flawed-state-machine "Lab: Authentication bypass via flawed state machine"
[4]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-bypassing-access-controls-using-email-address-parsing-discrepancies "Lab: Bypassing access controls using email address parsing discrepancies"
[5]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-excessive-trust-in-client-side-controls "Lab: Excessive trust in client-side controls"
[6]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-flawed-enforcement-of-business-rules "Lab: Flawed enforcement of business rules"
[7]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-high-level "Lab: High-level logic vulnerability"
[8]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-handling-of-exceptional-input "Lab: Inconsistent handling of exceptional input"
[9]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-security-controls "Lab: Inconsistent security controls"
[10]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-infinite-money "Lab: Infinite money logic flaw"
[11]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-insufficient-workflow-validation "Lab: Insufficient workflow validation"
[12]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-low-level "Lab: Low-level logic flaw"
[13]: https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-weak-isolation-on-dual-use-endpoint "Lab: Weak isolation on dual-use endpoint"
