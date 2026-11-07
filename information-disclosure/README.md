# Information disclosure (information leakage, or an info leak)

Information disclosure is a vulnerability class in which a website unintentionally exposes sensitive information. The leaked content can include personal or business data, or technical details about the application and its infrastructure. Unlike a general learning category, this topic covers a distinct security weakness: unintended disclosure through application responses or exposed resources. [1]

## Main concepts and common causes

Disclosure can be direct, such as a response revealing private records, or indirect, such as errors or behavioral differences that let a visitor infer hidden facts. Technical clues can also help identify attack surface or support further attacks. Common examples include exposed source or backup files, version-control data, developer comments, debug output, secrets embedded in code, and detailed error messages. [1]

The Academy groups common causes into internal content left in public material, insecure configuration of the application or its supporting technologies, and flawed application design or behavior. Debug and diagnostic features left enabled, overly verbose errors, and distinguishable responses for different states are representative examples. [1]

## Impact

Impact depends on what is disclosed. Exposure of sensitive user or commercial data can cause direct harm on its own. Technical information may have limited direct impact, but can reveal useful attack surface or enable other weaknesses to be exploited. Assessment should therefore consider the sensitivity of the information and what a realistic attacker could do with it, rather than treating every technical detail as equally severe. [1]

## High-level detection and assessment

During authorized testing, review normal responses and error paths for excessive detail, and look for publicly reachable development artifacts, backup material, debug or diagnostic output, and accidental source or configuration exposure. Notice whether response differences reveal the existence of resources or account states. Confirm the security relevance and likely consequences of any finding while staying within the agreed scope; do not infer high severity from a technical detail alone. [1]

## Prevention

Identify and classify sensitive information so it is handled consistently. Include disclosure checks in code review, QA, and build processes, including removal of developer comments and accidental artifacts. Use generic errors that avoid unnecessary internal detail. Disable debug and diagnostic features in production, and review the security implications of third-party technology settings while disabling features that are not needed. If secrets are exposed, treat them as compromised and replace them. [1]

## Lab notes

- [Authentication bypass via information disclosure](./labs/lab-infoleak-authentication-bypass.md)
- [Information disclosure in error messages](./labs/lab-infoleak-in-error-messages.md)
- [Information disclosure in version control history](./labs/lab-infoleak-in-version-control-history.md)
- [Information disclosure on debug page](./labs/lab-infoleak-on-debug-page.md)
- [Source code disclosure via backup files](./labs/lab-infoleak-via-backup-files.md)

## References

[1]: https://portswigger.net/web-security/information-disclosure "PortSwigger Web Security Academy: Information disclosure"
[2]: https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass "Lab: Authentication bypass via information disclosure"
[3]: https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages "Lab: Information disclosure in error messages"
[4]: https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history "Lab: Information disclosure in version control history"
[5]: https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page "Lab: Information disclosure on debug page"
[6]: https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files "Lab: Source code disclosure via backup files"
