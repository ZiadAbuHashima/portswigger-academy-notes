# DOM-based vulnerabilities (DOM-based; DOM XSS is a common subtype)

## Overview

The Document Object Model (DOM) is the browser’s structured representation of a page and its elements. DOM manipulation is routine; vulnerabilities arise when client-side JavaScript takes attacker-controllable data from a **source** and passes it unsafely to a potentially dangerous **sink**. This topic is a family of client-side vulnerability classes, not a general learning or testing category. DOM-based cross-site scripting is commonly abbreviated **DOM XSS**. [1]

## Main concepts and impact

Taint flow is the key model: sources can include URL properties, referrers, cookies, web messages, browser storage, and other attacker-influenced values. Sinks include operations that interpret or apply data, such as HTML insertion, script evaluation, navigation, cookie writes, messaging, and storage APIs. The outcome depends on the sink and context: it can include client-side script execution, unintended redirection, manipulation of client-side state or links, unsafe requests, or denial of service. [1]

## High-level detection and assessment

For authorized testing, review client-side code and trace values from controllable sources through transformations and validation to their final sinks. Pay particular attention to URL query or fragment data, messages received by event listeners, referrers, and client-side cookies or storage. An indicator is data reaching an interpreting or security-sensitive sink without validation or context-appropriate handling. Assess relevant flows in the browser and confirm the observable effect without assuming that every source-to-sink path is exploitable. [1]

## Prevention

Avoid allowing untrusted data to dynamically alter values sent to sensitive sinks. Where that behavior is required, validate against an allowlist when feasible and apply sanitization or encoding suited to the exact destination context. HTML, JavaScript, and URL contexts can require different handling, so one generic escaping step is not sufficient. [1]

## Lab notes

- [Lab: DOM XSS using web messages](labs/lab-dom-xss-using-web-messages.md)
- [Lab: DOM XSS using web messages and a JavaScript URL](labs/lab-dom-xss-using-web-messages-and-a-javascript-url.md)
- [Lab: DOM XSS using web messages and JSON.parse](labs/lab-dom-xss-using-web-messages-and-json-parse.md)
- [Lab: DOM-based cookie manipulation](labs/lab-dom-cookie-manipulation.md)
- [Lab: Clobbering DOM attributes to bypass HTML filters](labs/lab-dom-clobbering-attributes-to-bypass-html-filters.md)
- [Lab: Exploiting DOM clobbering to enable XSS](labs/lab-dom-xss-exploiting-dom-clobbering.md)
- [Lab: DOM-based open redirection](labs/lab-dom-open-redirection.md)

## References

[1]: https://portswigger.net/web-security/dom-based "PortSwigger Web Security Academy: DOM-based vulnerabilities"
[2]: https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages "PortSwigger Web Security Academy: Lab: DOM XSS using web messages"
[3]: https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-a-javascript-url "PortSwigger Web Security Academy: Lab: DOM XSS using web messages and a JavaScript URL"
[4]: https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-json-parse "PortSwigger Web Security Academy: Lab: DOM XSS using web messages and JSON.parse"
[5]: https://portswigger.net/web-security/dom-based/cookie-manipulation/lab-dom-cookie-manipulation "PortSwigger Web Security Academy: Lab: DOM-based cookie manipulation"
[6]: https://portswigger.net/web-security/dom-based/dom-clobbering/lab-dom-clobbering-attributes-to-bypass-html-filters "PortSwigger Web Security Academy: Lab: Clobbering DOM attributes to bypass HTML filters"
[7]: https://portswigger.net/web-security/dom-based/dom-clobbering/lab-dom-xss-exploiting-dom-clobbering "PortSwigger Web Security Academy: Lab: Exploiting DOM clobbering to enable XSS"
[8]: https://portswigger.net/web-security/dom-based/open-redirection/lab-dom-open-redirection "PortSwigger Web Security Academy: Lab: DOM-based open redirection"
