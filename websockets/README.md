# WebSockets security

**WebSockets** (often abbreviated **WS**; secure WebSockets use **WSS**) are long-lived, bidirectional connections initiated through an HTTP handshake. This Academy section is a general learning and security-testing topic, not a single vulnerability class: established web vulnerability types can also occur in WebSocket message handling and connection setup. [1]

## Main concepts

A WebSocket application exchanges messages asynchronously in both directions after the handshake. Message content may carry user input to server-side processing or be relayed to other users and rendered in their browsers. Unsafe processing can therefore expose familiar input-based flaws, including injection and cross-site scripting (XSS). Some vulnerabilities depend instead on handshake behavior, such as misplaced trust in HTTP headers, session handling flaws, or custom headers that expand the attack surface. Cross-site WebSocket hijacking can arise when a handshake is vulnerable to cross-site request forgery (CSRF). [1]

Testing considers both traffic and connection establishment. In an authorized assessment, identify application functions that use WebSockets, observe handshake and message behavior, and assess whether input is safely processed in each direction. Review whether identity, authorization, origin, session context, and security-relevant headers are handled consistently. Where responses do not reveal a result directly, some issues may require out-of-band assessment techniques. Use an approved test scope and avoid affecting other users or systems. [1]

## Potential impact

Impact depends on the flaw and the data or actions exposed. Unsafe message processing may enable server-side injection or client-side attacks against users receiving rendered content. Handshake and session weaknesses can undermine connection controls; cross-site WebSocket hijacking may let an attacker perform privileged actions as a victim or access sensitive information available to that user. [1]

## Prevention

Use `wss://` to protect connections in transit. Hard-code the WebSocket endpoint rather than incorporating user-controlled data into its URL. Protect the handshake against CSRF and validate security-relevant connection context rather than trusting unverified headers. Treat data received over WebSockets as untrusted on both server and client, and apply context-appropriate validation, encoding, and safe handling. [1]

## Lab notes

- [Manipulating the WebSocket handshake to exploit vulnerabilities](labs/lab-manipulating-handshake-to-exploit-vulnerabilities.md)
- [Manipulating WebSocket messages to exploit vulnerabilities](labs/lab-manipulating-messages-to-exploit-vulnerabilities.md)

## References

[1] [PortSwigger Web Security Academy: WebSockets](https://portswigger.net/web-security/websockets)

[2] [Lab: Manipulating the WebSocket handshake to exploit vulnerabilities](https://portswigger.net/web-security/websockets/lab-manipulating-handshake-to-exploit-vulnerabilities)

[3] [Lab: Manipulating WebSocket messages to exploit vulnerabilities](https://portswigger.net/web-security/websockets/lab-manipulating-messages-to-exploit-vulnerabilities)
