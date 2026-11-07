# API Testing

**API** means *application programming interface*. API testing is a general learning and security-testing category, not a single vulnerability class. It examines how an application’s APIs expose and process data and operations, including functionality that may not be used by the visible front end. PortSwigger’s topic focuses on API reconnaissance, especially RESTful and JSON APIs, and server-side parameter pollution that can affect internal APIs. [1]

## Main concepts

API reconnaissance maps the attack surface: identify endpoints, supported HTTP methods, request formats, parameters, authentication expectations, and rate limits. Documentation may be human-readable or machine-readable, and it may reveal intended endpoints and operations. Browsing the application and its client-side JavaScript can reveal endpoints that documentation or the visible interface does not make apparent. Errors and response differences can help a tester understand how an API processes requests. [1]

Two specific issues covered here are **mass assignment** and **server-side parameter pollution**. Mass assignment can occur when a framework automatically binds request fields to an internal object, allowing unintended properties to be accepted. Server-side parameter pollution occurs when user input is incorporated into a server-side API request without being handled safely, potentially affecting its query string or URL path. [1]

## Potential impact

API vulnerabilities can undermine confidentiality, integrity, and availability. Depending on the exposed operation and the strength of server-side controls, they may disclose sensitive data, permit unauthorized changes or actions, or allow unintended access to privileged functionality. Unexpectedly accepted fields or manipulated internal requests can alter application behavior. [1]

## High-level detection and assessment

Test only systems and functions you are authorized to assess. Begin by reviewing available API documentation and mapping endpoints observed in application traffic and client-side code. Compare behavior across supported methods, content types, parameters, and authentication states, while noting response changes and error messages. Treat these observations as leads to validate safely; avoid disruptive operations and follow the engagement’s scope and rate limits. [1]

## Prevention

Design API security in from the start. Keep documentation accurate, and restrict access to it when the API is not intended to be public. Allowlist permitted HTTP methods and validate expected content types. Use generic error messages, and apply protective measures to every API version, including older versions that remain reachable. For mass assignment, explicitly allowlist user-updatable properties and prevent sensitive properties from being changed through user input. [1]

## Lab notes

- [Exploiting an API endpoint using documentation](labs/lab-exploiting-api-endpoint-using-documentation.md)
- [Exploiting a mass assignment vulnerability](labs/lab-exploiting-mass-assignment-vulnerability.md)
- [Finding and exploiting an unused API endpoint](labs/lab-exploiting-unused-api-endpoint.md)
- [Exploiting server-side parameter pollution in a query string](labs/lab-exploiting-server-side-parameter-pollution-in-query-string.md)
- [Exploiting server-side parameter pollution in a REST URL](labs/lab-exploiting-server-side-parameter-pollution-in-rest-url.md)

## References

[1]: https://portswigger.net/web-security/api-testing "API testing | Web Security Academy"
[2]: https://portswigger.net/web-security/api-testing/lab-exploiting-api-endpoint-using-documentation "Lab: Exploiting an API endpoint using documentation"
[3]: https://portswigger.net/web-security/api-testing/lab-exploiting-mass-assignment-vulnerability "Lab: Exploiting a mass assignment vulnerability"
[4]: https://portswigger.net/web-security/api-testing/lab-exploiting-unused-api-endpoint "Lab: Finding and exploiting an unused API endpoint"
[5]: https://portswigger.net/web-security/api-testing/server-side-parameter-pollution/lab-exploiting-server-side-parameter-pollution-in-query-string "Lab: Exploiting server-side parameter pollution in a query string"
[6]: https://portswigger.net/web-security/api-testing/server-side-parameter-pollution/lab-exploiting-server-side-parameter-pollution-in-rest-url "Lab: Exploiting server-side parameter pollution in a REST URL"
