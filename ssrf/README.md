# Server-side request forgery (SSRF)

Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page. [1]

## Main concepts

SSRF can target the vulnerable application itself through its local interface, or other backend systems reachable from the server. These risks are amplified when internal services trust requests based on their network location or provide access to sensitive functions. Input filters can also fail when validation and the server’s URL parser interpret destinations differently, or when a permitted destination redirects elsewhere. Blind SSRF remains relevant even when the fetched response is not visible; a server-side request may still be observable through an authorized out-of-band test. [1]

Potential attack surfaces include features that accept full or partial URLs, data formats that cause URL retrieval during parsing, and analytics or logging components that act on values such as a Referer header. [1]

## Impact

A successful SSRF may expose sensitive information or enable unauthorized actions in the application or other backend systems. In some cases it can contribute to command execution on the server or a backend component. Requests to external third parties can also be made to appear to originate from the vulnerable organization. [1]

## High-level detection and assessment

During authorized testing, inventory application features and auxiliary components that cause server-side fetching. Review inputs that may influence a destination, including complete URLs, hostnames, path fragments, and request metadata. Assess whether behavior suggests access to local or internal services, whether validation remains consistent across URL parsing and redirects, and whether an outbound request occurs even when its response is not reflected. Use only approved test systems and destinations, and avoid accessing data or changing state beyond the agreed scope. [1]

## Prevention

Prefer fixed, application-defined destinations over arbitrary user-provided URLs. Where user-selected destinations are required, parse them with a well-tested URL library and enforce a narrow allowlist of schemes, hosts, and ports after canonicalization. Resolve and validate destination addresses against loopback, private, link-local, and other prohibited network ranges, and repeat validation after redirects and DNS resolution. Keep URL validation and request handling consistent to avoid parser discrepancies. Apply network egress controls and segmentation so application servers cannot reach unnecessary internal services, and require independent authentication and authorization for sensitive backend functions rather than trusting that a request came from the local network. These controls address the trust relationships and validation weaknesses described in the topic. [1]

## Lab notes

- [Blind SSRF with out-of-band detection](labs/lab-out-of-band-detection.md)
- [Blind SSRF with Shellshock exploitation](labs/lab-shellshock-exploitation.md)
- [Basic SSRF against another back-end system](labs/lab-basic-ssrf-against-backend-system.md)
- [Basic SSRF against the local server](labs/lab-basic-ssrf-against-localhost.md)
- [SSRF with filter bypass via open redirection vulnerability](labs/lab-ssrf-filter-bypass-via-open-redirection.md)
- [SSRF with blacklist-based input filter](labs/lab-ssrf-with-blacklist-filter.md)
- [SSRF with whitelist-based input filter](labs/lab-ssrf-with-whitelist-filter.md)

## References

[1]: https://portswigger.net/web-security/ssrf "PortSwigger Web Security Academy: Server-side request forgery"
[2]: https://portswigger.net/web-security/ssrf/blind/lab-out-of-band-detection "Lab: Blind SSRF with out-of-band detection"
[3]: https://portswigger.net/web-security/ssrf/blind/lab-shellshock-exploitation "Lab: Blind SSRF with Shellshock exploitation"
[4]: https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-backend-system "Lab: Basic SSRF against another back-end system"
[5]: https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-localhost "Lab: Basic SSRF against the local server"
[6]: https://portswigger.net/web-security/ssrf/lab-ssrf-filter-bypass-via-open-redirection "Lab: SSRF with filter bypass via open redirection vulnerability"
[7]: https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter "Lab: SSRF with blacklist-based input filter"
[8]: https://portswigger.net/web-security/ssrf/lab-ssrf-with-whitelist-filter "Lab: SSRF with whitelist-based input filter"
