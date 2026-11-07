# Lab: Broken brute-force protection, multiple credentials per request

**Official lab:** [Lab: Broken brute-force protection, multiple credentials per request](https://portswigger.net/web-security/authentication/password-based/lab-broken-brute-force-protection-multiple-credentials-per-request)

## Lab idea

This challenge tests a logic flaw in brute-force defenses when a login request accepts credentials in an unexpected multi-value form. It practices checking that authentication and attempt limits consistently validate the request’s data structure.
