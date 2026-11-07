# Authentication (AuthN)

Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category. [1]

Authentication may rely on something a person knows, has, or is. In web applications, common mechanisms include password-based login, multi-factor authentication (MFA, including two-factor authentication or 2FA), and supporting features such as persistent login and password recovery. Weaknesses can arise from inadequate protection against guessing or from implementation and logic flaws that let checks be bypassed. [1]

## Main concepts and common causes

Password-based systems can expose valid usernames through different messages, response details, account-lock behavior, or timing. Weak brute-force protections can let attackers make too many guesses, while careless handling of credential formats or client identity can make protections ineffective. Multi-factor flows can fail when verification is not correctly bound to the account or is not consistently required. Password-change, reset, and stay-logged-in features are also part of the authentication attack surface; broken validation, token handling, or token construction can weaken the entire system. [1]

## Potential impact

A successful bypass or credential compromise can give access to the data and functionality of the affected account. Compromise of a privileged account may expose the whole application or internal infrastructure. Even a lower-privilege account can reveal sensitive information or provide access to further attack surface. [1]

## High-level detection and assessment context

In an authorized assessment, review the complete lifecycle: login, second-factor verification, session persistence, password change, and account recovery. Compare responses for valid and invalid identities, including status, content, and timing; check whether attempt limits and lockouts behave consistently; and verify that protected functionality remains unavailable until all required checks have succeeded. Assess reset and persistent-login tokens for sound validation, account binding, and safe handling. Use test accounts and approved scope, and avoid accessing real users’ credentials or data.

## Prevention principles

Enforce HTTPS for authentication traffic and avoid disclosing usernames or email addresses. Use indistinguishable, generic login errors with consistent status codes and response timing. Apply robust rate limiting that cannot be trivially bypassed by spoofed client identity, and consider additional challenges after repeated failures. Thoroughly review verification logic, including MFA and recovery flows. Treat password change and reset as security-critical authentication paths. Use strong password guidance and implement MFA with sound factor and verification design. [2]

## Lab notes

The following notes summarize the concepts practiced by every lab listed for this topic in the supplied manifest. They intentionally omit solutions and exploit instructions.

- [Lab: 2FA broken logic](labs/lab-2fa-broken-logic.md)
- [Lab: 2FA bypass using a brute-force attack](labs/lab-2fa-bypass-using-a-brute-force-attack.md)
- [Lab: 2FA simple bypass](labs/lab-2fa-simple-bypass.md)
- [Lab: Brute-forcing a stay-logged-in cookie](labs/lab-brute-forcing-a-stay-logged-in-cookie.md)
- [Lab: Offline password cracking](labs/lab-offline-password-cracking.md)
- [Lab: Password brute-force via password change](labs/lab-password-brute-force-via-password-change.md)
- [Lab: Password reset broken logic](labs/lab-password-reset-broken-logic.md)
- [Lab: Password reset poisoning via middleware](labs/lab-password-reset-poisoning-via-middleware.md)
- [Lab: Broken brute-force protection, multiple credentials per request](labs/lab-broken-brute-force-protection-multiple-credentials-per-request.md)
- [Lab: Broken brute-force protection, IP block](labs/lab-broken-bruteforce-protection-ip-block.md)
- [Lab: Username enumeration via account lock](labs/lab-username-enumeration-via-account-lock.md)
- [Lab: Username enumeration via different responses](labs/lab-username-enumeration-via-different-responses.md)
- [Lab: Username enumeration via response timing](labs/lab-username-enumeration-via-response-timing.md)
- [Lab: Username enumeration via subtly different responses](labs/lab-username-enumeration-via-subtly-different-responses.md)

## References

[1]: https://portswigger.net/web-security/authentication "PortSwigger Web Security Academy: Authentication vulnerabilities"
[2]: https://portswigger.net/web-security/authentication/securing "PortSwigger Web Security Academy: How to secure your authentication mechanisms"
[3]: https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-broken-logic "Lab: 2FA broken logic"
[4]: https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-bypass-using-a-brute-force-attack "Lab: 2FA bypass using a brute-force attack"
[5]: https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass "Lab: 2FA simple bypass"
[6]: https://portswigger.net/web-security/authentication/other-mechanisms/lab-brute-forcing-a-stay-logged-in-cookie "Lab: Brute-forcing a stay-logged-in cookie"
[7]: https://portswigger.net/web-security/authentication/other-mechanisms/lab-offline-password-cracking "Lab: Offline password cracking"
[8]: https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-brute-force-via-password-change "Lab: Password brute-force via password change"
[9]: https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic "Lab: Password reset broken logic"
[10]: https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-poisoning-via-middleware "Lab: Password reset poisoning via middleware"
[11]: https://portswigger.net/web-security/authentication/password-based/lab-broken-brute-force-protection-multiple-credentials-per-request "Lab: Broken brute-force protection, multiple credentials per request"
[12]: https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block "Lab: Broken brute-force protection, IP block"
[13]: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-account-lock "Lab: Username enumeration via account lock"
[14]: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses "Lab: Username enumeration via different responses"
[15]: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing "Lab: Username enumeration via response timing"
[16]: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses "Lab: Username enumeration via subtly different responses"
