# HTTP request smuggling (HTTP desynchronization)

HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request. [1]

## Main concepts

In HTTP/1, `Content-Length` and `Transfer-Encoding: chunked` can describe message boundaries. A mismatch in how the frontend and backend apply these rules can create **CL.TE** (frontend uses Content-Length; backend uses Transfer-Encoding) or **TE.CL** (the reverse) behavior. If both components support transfer encoding but parse an obfuscated or duplicate header differently, the issue is commonly described as **TE.TE**. [1]

HTTP/2 has a robust request-length mechanism when used end to end, but deployments that downgrade HTTP/2 at the frontend to HTTP/1 for a backend can introduce translation and header-validation risks. Related patterns include CL.0 behavior, client-side desynchronization, request tunnelling, request splitting, and response-queue poisoning. [1]

## Potential impact

Depending on the architecture and reachable application behavior, request smuggling can bypass frontend security controls, expose sensitive data, affect another user’s request or response, or contribute to unauthorized access and compromise of other users. Shared caches and browser-driven behavior can extend the impact to cache poisoning or deception and client-side attacks. The practical severity depends on the parsing discrepancy, connection handling, and application features reachable through the backend. [1]

## High-level detection and assessment

For authorized testing, first map the request path through proxies, load balancers, protocol translators, and application servers. Assess whether HTTP/1 framing is interpreted consistently and whether HTTP/2 is downgraded before reaching a backend. In a controlled environment, compare the behavior of a follow-up request or response for evidence of desynchronization; also consider endpoint-specific body handling, header normalization, connection reuse, and cache behavior. PortSwigger presents CL.TE and TE.CL confirmation using differential responses and describes additional browser-powered and HTTP/2 techniques. Avoid testing systems or shared connections without explicit authorization, since effects can spill over to other users. [1]

## Prevention principles

Prefer HTTP/2 end to end and disable HTTP downgrading where feasible. If downgrading is necessary, validate rewritten messages against HTTP/1.1 requirements and reject malformed or ambiguous request lines and headers. Normalize ambiguous requests at the frontend, and have the backend reject any ambiguity that remains while closing the affected connection. Do not assume that requests lack bodies; discard connections after server-level parsing exceptions. Disabling backend connection reuse can mitigate some patterns, but is not a complete defense against all request-tunnelling attacks. [1]

## Lab notes

Each lab note describes the learning objective at a high level and intentionally omits solutions and payloads.

- [Lab: 0.CL request smuggling](labs/lab-request-smuggling-0cl-request-smuggling.md)
- [Lab: H2.CL request smuggling](labs/lab-request-smuggling-h2-cl-request-smuggling.md)
- [Lab: HTTP/2 request smuggling via CRLF injection](labs/lab-request-smuggling-h2-request-smuggling-via-crlf-injection.md)
- [Lab: HTTP/2 request splitting via CRLF injection](labs/lab-request-smuggling-h2-request-splitting-via-crlf-injection.md)
- [Lab: Bypassing access controls via HTTP/2 request tunnelling](labs/lab-request-smuggling-h2-bypass-access-controls-via-request-tunnelling.md)
- [Lab: Web cache poisoning via HTTP/2 request tunnelling](labs/lab-request-smuggling-h2-web-cache-poisoning-via-request-tunnelling.md)
- [Lab: Response queue poisoning via H2.TE request smuggling](labs/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling.md)
- [Lab: CL.0 request smuggling](labs/lab-cl-0-request-smuggling.md)
- [Lab: Client-side desync](labs/lab-client-side-desync.md)
- [Lab: Server-side pause-based request smuggling](labs/lab-server-side-pause-based-request-smuggling.md)
- [Lab: Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability](labs/lab-bypass-front-end-controls-cl-te.md)
- [Lab: Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability](labs/lab-bypass-front-end-controls-te-cl.md)
- [Lab: Exploiting HTTP request smuggling to capture other users' requests](labs/lab-capture-other-users-requests.md)
- [Lab: Exploiting HTTP request smuggling to deliver reflected XSS](labs/lab-deliver-reflected-xss.md)
- [Lab: Exploiting HTTP request smuggling to perform web cache deception](labs/lab-perform-web-cache-deception.md)
- [Lab: Exploiting HTTP request smuggling to perform web cache poisoning](labs/lab-perform-web-cache-poisoning.md)
- [Lab: Exploiting HTTP request smuggling to reveal front-end request rewriting](labs/lab-reveal-front-end-request-rewriting.md)
- [Lab: HTTP request smuggling, confirming a CL.TE vulnerability via differential responses](labs/lab-confirming-cl-te-via-differential-responses.md)
- [Lab: HTTP request smuggling, confirming a TE.CL vulnerability via differential responses](labs/lab-confirming-te-cl-via-differential-responses.md)
- [Lab: HTTP request smuggling, basic CL.TE vulnerability](labs/lab-basic-cl-te.md)
- [Lab: HTTP request smuggling, basic TE.CL vulnerability](labs/lab-basic-te-cl.md)
- [Lab: HTTP request smuggling, obfuscating the TE header](labs/lab-obfuscating-te-header.md)

## References

[1]: https://portswigger.net/web-security/request-smuggling "PortSwigger Web Security Academy: HTTP request smuggling"
[2]: https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-0cl-request-smuggling "PortSwigger Web Security Academy: Lab: 0.CL request smuggling"
[3]: https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-cl-request-smuggling "PortSwigger Web Security Academy: Lab: H2.CL request smuggling"
[4]: https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-smuggling-via-crlf-injection "PortSwigger Web Security Academy: Lab: HTTP/2 request smuggling via CRLF injection"
[5]: https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-splitting-via-crlf-injection "PortSwigger Web Security Academy: Lab: HTTP/2 request splitting via CRLF injection"
[6]: https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-bypass-access-controls-via-request-tunnelling "PortSwigger Web Security Academy: Lab: Bypassing access controls via HTTP/2 request tunnelling"
[7]: https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-web-cache-poisoning-via-request-tunnelling "PortSwigger Web Security Academy: Lab: Web cache poisoning via HTTP/2 request tunnelling"
[8]: https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling "PortSwigger Web Security Academy: Lab: Response queue poisoning via H2.TE request smuggling"
[9]: https://portswigger.net/web-security/request-smuggling/browser/cl-0/lab-cl-0-request-smuggling "PortSwigger Web Security Academy: Lab: CL.0 request smuggling"
[10]: https://portswigger.net/web-security/request-smuggling/browser/client-side-desync/lab-client-side-desync "PortSwigger Web Security Academy: Lab: Client-side desync"
[11]: https://portswigger.net/web-security/request-smuggling/browser/pause-based-desync/lab-server-side-pause-based-request-smuggling "PortSwigger Web Security Academy: Lab: Server-side pause-based request smuggling"
[12]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-cl-te "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability"
[13]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-te-cl "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability"
[14]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-capture-other-users-requests "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to capture other users' requests"
[15]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-deliver-reflected-xss "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to deliver reflected XSS"
[16]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-deception "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to perform web cache deception"
[17]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-poisoning "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to perform web cache poisoning"
[18]: https://portswigger.net/web-security/request-smuggling/exploiting/lab-reveal-front-end-request-rewriting "PortSwigger Web Security Academy: Lab: Exploiting HTTP request smuggling to reveal front-end request rewriting"
[19]: https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-cl-te-via-differential-responses "PortSwigger Web Security Academy: Lab: HTTP request smuggling, confirming a CL.TE vulnerability via differential responses"
[20]: https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-te-cl-via-differential-responses "PortSwigger Web Security Academy: Lab: HTTP request smuggling, confirming a TE.CL vulnerability via differential responses"
[21]: https://portswigger.net/web-security/request-smuggling/lab-basic-cl-te "PortSwigger Web Security Academy: Lab: HTTP request smuggling, basic CL.TE vulnerability"
[22]: https://portswigger.net/web-security/request-smuggling/lab-basic-te-cl "PortSwigger Web Security Academy: Lab: HTTP request smuggling, basic TE.CL vulnerability"
[23]: https://portswigger.net/web-security/request-smuggling/lab-obfuscating-te-header "PortSwigger Web Security Academy: Lab: HTTP request smuggling, obfuscating the TE header"
