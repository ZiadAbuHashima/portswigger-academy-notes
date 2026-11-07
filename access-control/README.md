# Access control vulnerabilities (broken access control; IDOR)

Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw. [1]

## Main concepts

**Vertical access control** limits sensitive functionality to particular roles, such as administrators. **Horizontal access control** limits resources to their owners or other authorized users at the same privilege level. **Context-dependent access control** restricts actions according to workflow or application state. Failures can therefore enable vertical privilege escalation, horizontal access to another user's data, or escalation from horizontal access to a more privileged account. [1]

Common weaknesses include missing checks on sensitive functionality, trusting role or identity values controlled by a user, inconsistent authorization across HTTP methods or URL interpretation layers, incomplete checks across multi-step workflows, and relying on request headers such as `Referer`. IDORs occur when user-supplied identifiers select objects without a correct authorization check. Hiding an endpoint or making an identifier hard to guess does not itself enforce access control. [1]

## Impact

Depending on the affected resource and action, a flaw can expose another user's private records or credentials, disclose sensitive data in an otherwise denied or redirected response, permit unauthorized account changes, or grant administrative capabilities. Horizontal access to a privileged user's account can also lead to vertical privilege escalation. [1]

## High-level detection and assessment

In an authorized test, identify representative roles, resources, and sensitive actions, then compare what each role is permitted to do. Check whether object access is tied to the authenticated user's authorization rather than merely to a supplied identifier. Assess access checks consistently across relevant routes, request methods, workflow stages, and responses, including redirects. Treat client-controlled fields and headers as untrusted. Use only systems and accounts within the test's authorization scope. [1]

## Prevention

Use defense in depth: deny access by default, enforce authorization for every protected resource and action, and prefer one consistent application-wide mechanism. Make permitted access explicit in code and base decisions on trusted identity, role, ownership, and workflow state rather than user-editable values or obscured URLs. Apply checks to every stage and route, and thoroughly audit and test that the implemented rules match the intended policy. [1]

## Lab notes

- [Insecure direct object references](labs/lab-insecure-direct-object-references.md)
- [Method-based access control can be circumvented](labs/lab-method-based-access-control-can-be-circumvented.md)
- [Multi-step process with no access control on one step](labs/lab-multi-step-process-with-no-access-control-on-one-step.md)
- [Referer-based access control](labs/lab-referer-based-access-control.md)
- [Unprotected admin functionality](labs/lab-unprotected-admin-functionality.md)
- [Unprotected admin functionality with unpredictable URL](labs/lab-unprotected-admin-functionality-with-unpredictable-url.md)
- [URL-based access control can be circumvented](labs/lab-url-based-access-control-can-be-circumvented.md)
- [User ID controlled by request parameter](labs/lab-user-id-controlled-by-request-parameter.md)
- [User ID controlled by request parameter with data leakage in redirect](labs/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect.md)
- [User ID controlled by request parameter with password disclosure](labs/lab-user-id-controlled-by-request-parameter-with-password-disclosure.md)
- [User ID controlled by request parameter, with unpredictable user IDs](labs/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids.md)
- [User role can be modified in user profile](labs/lab-user-role-can-be-modified-in-user-profile.md)
- [User role controlled by request parameter](labs/lab-user-role-controlled-by-request-parameter.md)

## References

[1]: https://portswigger.net/web-security/access-control "Access control vulnerabilities and privilege escalation"
[2]: https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references "Lab: Insecure direct object references"
[3]: https://portswigger.net/web-security/access-control/lab-method-based-access-control-can-be-circumvented "Lab: Method-based access control can be circumvented"
[4]: https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step "Lab: Multi-step process with no access control on one step"
[5]: https://portswigger.net/web-security/access-control/lab-referer-based-access-control "Lab: Referer-based access control"
[6]: https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality "Lab: Unprotected admin functionality"
[7]: https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url "Lab: Unprotected admin functionality with unpredictable URL"
[8]: https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented "Lab: URL-based access control can be circumvented"
[9]: https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter "Lab: User ID controlled by request parameter"
[10]: https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect "Lab: User ID controlled by request parameter with data leakage in redirect"
[11]: https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure "Lab: User ID controlled by request parameter with password disclosure"
[12]: https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids "Lab: User ID controlled by request parameter, with unpredictable user IDs"
[13]: https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile "Lab: User role can be modified in user profile"
[14]: https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter "Lab: User role controlled by request parameter"
