# PortSwigger Web Security Academy Notes

A structured study reference for **PortSwigger Web Security Academy**. Each topic folder contains a standalone overview and a `labs/` folder. Each lab note gives a short general explanation of the vulnerability, the lab idea, concise steps from PortSwigger’s official solution when published, and the payloads or key values shown there.

This snapshot covers **31 Academy sections and 272 labs** listed in the official topic index and sitemap at the time of collection. Counts can change as PortSwigger adds or updates labs.

## Topics

| Topic | Labs | Notes |
|---|---:|---|
| SQL injection | 18 | [Overview](./sql-injection/README.md) · [Lab notes](./sql-injection/labs/) |
| Cross-site scripting | 30 | [Overview](./cross-site-scripting/README.md) · [Lab notes](./cross-site-scripting/labs/) |
| Cross-site request forgery (CSRF) | 11 | [Overview](./csrf/README.md) · [Lab notes](./csrf/labs/) |
| Clickjacking | 5 | [Overview](./clickjacking/README.md) · [Lab notes](./clickjacking/labs/) |
| DOM-based vulnerabilities | 7 | [Overview](./dom-based/README.md) · [Lab notes](./dom-based/labs/) |
| Cross-origin resource sharing (CORS) | 3 | [Overview](./cors/README.md) · [Lab notes](./cors/labs/) |
| XML external entity (XXE) injection | 9 | [Overview](./xxe/README.md) · [Lab notes](./xxe/labs/) |
| Server-side request forgery (SSRF) | 7 | [Overview](./ssrf/README.md) · [Lab notes](./ssrf/labs/) |
| HTTP request smuggling | 22 | [Overview](./request-smuggling/README.md) · [Lab notes](./request-smuggling/labs/) |
| OS command injection | 5 | [Overview](./os-command-injection/README.md) · [Lab notes](./os-command-injection/labs/) |
| Server-side template injection | 7 | [Overview](./server-side-template-injection/README.md) · [Lab notes](./server-side-template-injection/labs/) |
| Path traversal | 6 | [Overview](./file-path-traversal/README.md) · [Lab notes](./file-path-traversal/labs/) |
| Access control vulnerabilities | 13 | [Overview](./access-control/README.md) · [Lab notes](./access-control/labs/) |
| Authentication | 14 | [Overview](./authentication/README.md) · [Lab notes](./authentication/labs/) |
| WebSockets | 2 | [Overview](./websockets/README.md) · [Lab notes](./websockets/labs/) |
| Web cache poisoning | 13 | [Overview](./web-cache-poisoning/README.md) · [Lab notes](./web-cache-poisoning/labs/) |
| Insecure deserialization | 10 | [Overview](./deserialization/README.md) · [Lab notes](./deserialization/labs/) |
| Information disclosure | 5 | [Overview](./information-disclosure/README.md) · [Lab notes](./information-disclosure/labs/) |
| Business logic vulnerabilities | 12 | [Overview](./logic-flaws/README.md) · [Lab notes](./logic-flaws/labs/) |
| HTTP Host header attacks | 7 | [Overview](./host-header/README.md) · [Lab notes](./host-header/labs/) |
| OAuth authentication | 6 | [Overview](./oauth/README.md) · [Lab notes](./oauth/labs/) |
| File upload vulnerabilities | 7 | [Overview](./file-upload/README.md) · [Lab notes](./file-upload/labs/) |
| JWT | 8 | [Overview](./jwt/README.md) · [Lab notes](./jwt/labs/) |
| Essential skills | 2 | [Overview](./essential-skills/README.md) · [Lab notes](./essential-skills/labs/) |
| Prototype pollution | 10 | [Overview](./prototype-pollution/README.md) · [Lab notes](./prototype-pollution/labs/) |
| GraphQL API vulnerabilities | 5 | [Overview](./graphql/README.md) · [Lab notes](./graphql/labs/) |
| Race conditions | 6 | [Overview](./race-conditions/README.md) · [Lab notes](./race-conditions/labs/) |
| NoSQL injection | 4 | [Overview](./nosql-injection/README.md) · [Lab notes](./nosql-injection/labs/) |
| API testing | 5 | [Overview](./api-testing/README.md) · [Lab notes](./api-testing/labs/) |
| Web LLM attacks | 8 | [Overview](./llm-attacks/README.md) · [Lab notes](./llm-attacks/labs/) |
| Web cache deception | 5 | [Overview](./web-cache-deception/README.md) · [Lab notes](./web-cache-deception/labs/) |

## How to use these notes

Read the topic overview first, then open an individual file under that topic’s `labs/` folder before attempting the corresponding PortSwigger lab. **Essential skills** and **API testing** are learning categories rather than individual vulnerability classes.

## Official sources

- [All Web Security Academy topics](https://portswigger.net/web-security/all-topics)
- [All Web Security Academy labs](https://portswigger.net/web-security/all-labs)
- [Web Security Academy](https://portswigger.net/web-security)

## Scope

For educational use and authorized testing only. Use the payloads only in the corresponding Academy labs or on systems you are explicitly authorized to test. The solution notes are concise summaries of PortSwigger’s published walkthroughs; some newer labs do not yet have a written official solution. These notes are not official PortSwigger documentation.
