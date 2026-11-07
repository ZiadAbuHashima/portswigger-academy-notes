# HTTP Host header attacks (Host header attacks)

HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category. [1]

## Main concepts

The header is important in shared hosting and intermediary-based architectures, where several sites or back ends may share an IP address. An application might also use it to construct links, including password-reset links, or pass it between infrastructure components. Host-related flaws can arise from implicit trust, weak validation, unsafe reflection, conflicting interpretations between a cache and an application, or inconsistent handling of headers and connection state. Configuration mistakes in proxies and other infrastructure can be as important as application code. [1]

Related patterns include Host header injection, authentication or business-logic bypasses, password-reset poisoning, web-cache poisoning, routing-based server-side request forgery (SSRF), virtual-host discovery, and exploitation of other server-side flaws. The Academy also covers connection-state attacks in which assumptions about a request connection contribute to routing behavior. [1]

## Potential impact

Depending on where the value is consumed, an attacker may influence links sent to users, cause cached responses to be served with attacker-controlled content, bypass access controls, or induce requests to internal systems. Other server-side vulnerabilities may become reachable through unsafe use of the header. Outcomes can include account compromise, exposure of internal services, or delivery of malicious content to site visitors. Actual impact depends on the vulnerable component and its context. [1]

## High-level detection and assessment

For authorized testing, map how the application and its infrastructure treat the intended host: assess whether host values are validated, whether host-related information is reflected in generated content, and whether intermediary, cache, and back-end behavior agree. Observe differences in responses and routing behavior while staying within the approved scope. Consider supported host-override headers and connection-level assumptions as part of the assessment. A changed response alone is not proof of a vulnerability; establish a safe, reproducible effect and its security impact. [1]

## Prevention

Prefer relative URLs and avoid deriving server-side absolute URLs from request headers. Where absolute URLs are required, use a configured canonical domain rather than request-supplied data. If the Host header must be used, validate it against an explicit allowlist and reject unrecognized values. Review whether proxy-related host-override headers are enabled or trusted, and apply equivalent validation throughout the request path. Configure reverse proxies and load balancers to route only to permitted domains, and avoid placing internal-only virtual hosts alongside public-facing content where host manipulation could expose them. [1]

## Lab notes

- [Host header authentication bypass](labs/lab-host-header-authentication-bypass.md)
- [Host validation bypass via connection state attack](labs/lab-host-header-host-validation-bypass-via-connection-state-attack.md)
- [Routing-based SSRF](labs/lab-host-header-routing-based-ssrf.md)
- [SSRF via flawed request parsing](labs/lab-host-header-ssrf-via-flawed-request-parsing.md)
- [Web cache poisoning via ambiguous requests](labs/lab-host-header-web-cache-poisoning-via-ambiguous-requests.md)
- [Basic password reset poisoning](labs/lab-host-header-basic-password-reset-poisoning.md)
- [Password reset poisoning via dangling markup](labs/lab-host-header-password-reset-poisoning-via-dangling-markup.md)

## References

[1]: https://portswigger.net/web-security/host-header "PortSwigger Web Security Academy: HTTP Host header attacks"
[2]: https://portswigger.net/web-security/host-header/exploiting/lab-host-header-authentication-bypass "PortSwigger lab: Host header authentication bypass"
[3]: https://portswigger.net/web-security/host-header/exploiting/lab-host-header-host-validation-bypass-via-connection-state-attack "PortSwigger lab: Host validation bypass via connection state attack"
[4]: https://portswigger.net/web-security/host-header/exploiting/lab-host-header-routing-based-ssrf "PortSwigger lab: Routing-based SSRF"
[5]: https://portswigger.net/web-security/host-header/exploiting/lab-host-header-ssrf-via-flawed-request-parsing "PortSwigger lab: SSRF via flawed request parsing"
[6]: https://portswigger.net/web-security/host-header/exploiting/lab-host-header-web-cache-poisoning-via-ambiguous-requests "PortSwigger lab: Web cache poisoning via ambiguous requests"
[7]: https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-basic-password-reset-poisoning "PortSwigger lab: Basic password reset poisoning"
[8]: https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-password-reset-poisoning-via-dangling-markup "PortSwigger lab: Password reset poisoning via dangling markup"
