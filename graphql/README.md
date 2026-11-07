# GraphQL API vulnerabilities (GraphQL)

GraphQL API vulnerabilities is a topic for learning how to assess GraphQL APIs, not one single vulnerability class. The Academy highlights implementation and design flaws: a GraphQL service commonly exposes multiple operations through one endpoint, while each client request selects fields and can invoke queries or state-changing mutations. If schema exposure, authorization, transport handling, or resource controls are weak, a request may reveal data or trigger actions the caller should not be allowed to perform. [1]

## Main concepts

- **Endpoint and schema discovery:** A hidden or unfamiliar endpoint may be overlooked. Introspection can reveal available types, fields, queries, and mutations; error suggestions may disclose schema names even when introspection is disabled. Schema visibility can reveal sensitive fields or operations. [1]
- **Field- and object-level authorization:** Direct object arguments, such as IDs, must be checked against the caller's permissions. Returning a private field or object merely because it is selectable in a query can expose data across authorization boundaries. [1]
- **Aliases and resource controls:** GraphQL aliases can request repeated operations in one HTTP request. A limiter that counts only HTTP requests may therefore fail to constrain repeated login attempts or other costly work. Deep, large, or complex queries can also consume excessive resources. [1]
- **CSRF and request handling:** If a browser can send an authenticated GraphQL mutation cross-site—for example, because the endpoint accepts form-encoded requests or GET—and the application lacks effective CSRF defenses, an attacker may induce an unwanted action. [1]

## Potential impact

Depending on the exposed operations and data, these flaws can disclose private records or credentials, allow unauthorized account or administrative actions, weaken brute-force protections, or consume server resources. CSRF can cause an authenticated user's browser to perform changes without their intent. [1]

## High-level assessment context

For authorized testing, identify GraphQL endpoints and review normal application traffic to understand the operations in use. Assess what schema and error details are exposed, then check whether object IDs and individually selectable fields are authorized for the current user. Review whether limits account for aliases, operation count, query depth, size, and computational cost. For state-changing operations, verify accepted HTTP methods and content types and assess the application's CSRF protections. Keep testing within the agreed scope. [1]

## Prevention

Apply authorization in resolvers to every requested object and sensitive field; do not rely on obscurity of IDs or on clients omitting private fields. Remove unintended fields from the schema. Disable introspection and schema suggestions in production when they are not needed; where a public API requires schema discovery, review carefully what it exposes. [1]

Use limits that consider query depth, aliases, root fields, operation count, request size, and estimated execution cost, alongside rate limits that account for work performed rather than only HTTP request totals. For CSRF defense, accept only JSON-encoded POST requests where appropriate, validate that the body matches the declared content type, and use a secure CSRF token mechanism. [1]

## Lab notes

- [Accidental exposure of private GraphQL fields](labs/lab-graphql-accidental-field-exposure.md)
- [Bypassing GraphQL brute force protections](labs/lab-graphql-brute-force-protection-bypass.md)
- [Performing CSRF exploits over GraphQL](labs/lab-graphql-csrf-via-graphql-api.md)
- [Finding a hidden GraphQL endpoint](labs/lab-graphql-find-the-endpoint.md)
- [Accessing private GraphQL posts](labs/lab-graphql-reading-private-posts.md)

## References

[1]: https://portswigger.net/web-security/graphql "GraphQL API vulnerabilities"
[2]: https://portswigger.net/web-security/graphql/lab-graphql-accidental-field-exposure "Lab: Accidental exposure of private GraphQL fields"
[3]: https://portswigger.net/web-security/graphql/lab-graphql-brute-force-protection-bypass "Lab: Bypassing GraphQL brute force protections"
[4]: https://portswigger.net/web-security/graphql/lab-graphql-csrf-via-graphql-api "Lab: Performing CSRF exploits over GraphQL"
[5]: https://portswigger.net/web-security/graphql/lab-graphql-find-the-endpoint "Lab: Finding a hidden GraphQL endpoint"
[6]: https://portswigger.net/web-security/graphql/lab-graphql-reading-private-posts "Lab: Accessing private GraphQL posts"
