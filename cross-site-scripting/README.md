# Cross-site scripting (XSS)

Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user. [1]

## Main concepts

XSS commonly results when untrusted data is inserted into a response or the browser document without handling it for the exact parsing context. The three main forms differ by where the data is introduced: reflected XSS returns request data in the immediate response; stored XSS saves untrusted data and serves it to users later; DOM-based XSS arises when client-side code processes a controllable source unsafely, often by writing data into the DOM. A flaw may involve HTML text, an attribute, a JavaScript string or template, a URL, a framework expression, or a DOM API. The context determines the risk and the necessary defense. [1]

Common causes include missing or incorrect context-sensitive output encoding, unsafe construction of HTML or script, placing untrusted values in executable attributes or script contexts, dangerous DOM sinks, and relying on incomplete character or tag blocklists. Encoding for one context does not automatically make data safe in another. [1]

## Potential impact

An attacker may impersonate a victim, perform actions with the victim’s privileges, read data available to the victim, capture credentials, or alter the appearance or behavior of the site. Severity depends on the application’s data and functions and the victim’s privileges; compromise of a privileged account can have especially serious consequences. [1]

## Authorized assessment context

Only test systems for which you have explicit authorization. At a high level, identify user-controllable inputs across requests, stored content, and browser-side sources; use harmless unique markers to see where values reappear in responses or the DOM; then determine the exact output or sink context and whether the browser interprets the data as active content. For DOM-based cases, trace sources to sinks and review client-side JavaScript where necessary. A reflected marker alone is not proof of XSS; context and execution matter. Use a scanner as an aid, not as a replacement for validating findings. [1]

## Prevention

Validate input against expected formats where appropriate, but rely primarily on context-appropriate output encoding at the point of rendering. Encode untrusted values for their destination context, including HTML, attributes, JavaScript, CSS, or URLs as applicable. Avoid unsafe HTML construction and dangerous DOM APIs when safer text-oriented alternatives are suitable; apply robust sanitization when users genuinely need to submit limited markup. Set accurate response content types and `X-Content-Type-Options` where relevant. Use a well-designed Content Security Policy as defense in depth, not as a substitute for fixing the underlying data flow. [1]

## Lab notes

Each note summarizes the challenge concept and practice objective without giving a solution or exploit steps.

- [Lab: Reflected XSS protected by CSP, with CSP bypass](labs/lab-csp-bypass.md)
- [Lab: Reflected XSS protected by very strict CSP, with dangling markup attack](labs/lab-very-strict-csp-with-dangling-markup-attack.md)
- [Lab: Reflected XSS with AngularJS sandbox escape and CSP](labs/lab-angular-sandbox-escape-and-csp.md)
- [Lab: Reflected XSS with AngularJS sandbox escape without strings](labs/lab-angular-sandbox-escape-without-strings.md)
- [Lab: Reflected XSS into attribute with angle brackets HTML-encoded](labs/lab-attribute-angle-brackets-html-encoded.md)
- [Lab: Reflected XSS in canonical link tag](labs/lab-canonical-link-tag.md)
- [Lab: Reflected XSS with event handlers and href attributes blocked](labs/lab-event-handlers-and-href-attributes-blocked.md)
- [Lab: Stored XSS into anchor href attribute with double quotes HTML-encoded](labs/lab-href-attribute-double-quotes-html-encoded.md)
- [Lab: Reflected XSS into HTML context with all tags blocked except custom ones](labs/lab-html-context-with-all-standard-tags-blocked.md)
- [Lab: Reflected XSS into HTML context with most tags and attributes blocked](labs/lab-html-context-with-most-tags-and-attributes-blocked.md)
- [Lab: Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped](labs/lab-javascript-string-angle-brackets-double-quotes-encoded-single-quotes-escaped.md)
- [Lab: Reflected XSS into a JavaScript string with angle brackets HTML encoded](labs/lab-javascript-string-angle-brackets-html-encoded.md)
- [Lab: Reflected XSS into a JavaScript string with single quote and backslash escaped](labs/lab-javascript-string-single-quote-backslash-escaped.md)
- [Lab: Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped](labs/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped.md)
- [Lab: Reflected XSS in a JavaScript URL with some characters blocked](labs/lab-javascript-url-some-characters-blocked.md)
- [Lab: Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped](labs/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped.md)
- [Lab: Reflected XSS with some SVG markup allowed](labs/lab-some-svg-markup-allowed.md)
- [Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded](labs/lab-angularjs-expression.md)
- [Lab: DOM XSS in document.write sink using source location.search](labs/lab-document-write-sink.md)
- [Lab: DOM XSS in document.write sink using source location.search inside a select element](labs/lab-document-write-sink-inside-select-element.md)
- [Lab: Reflected DOM XSS](labs/lab-dom-xss-reflected.md)
- [Lab: Stored DOM XSS](labs/lab-dom-xss-stored.md)
- [Lab: DOM XSS in innerHTML sink using source location.search](labs/lab-innerhtml-sink.md)
- [Lab: DOM XSS in jQuery anchor href attribute sink using location.search source](labs/lab-jquery-href-attribute-sink.md)
- [Lab: DOM XSS in jQuery selector sink using a hashchange event](labs/lab-jquery-selector-hash-change-event.md)
- [Lab: Exploiting cross-site scripting to capture passwords](labs/lab-capturing-passwords.md)
- [Lab: Exploiting XSS to bypass CSRF defenses](labs/lab-perform-csrf.md)
- [Lab: Exploiting cross-site scripting to steal cookies](labs/lab-stealing-cookies.md)
- [Lab: Reflected XSS into HTML context with nothing encoded](labs/lab-reflected-html-context-nothing-encoded.md)
- [Lab: Stored XSS into HTML context with nothing encoded](labs/lab-stored-html-context-nothing-encoded.md)

## References

- [1] [Official PortSwigger topic: Cross-site scripting](https://portswigger.net/web-security/cross-site-scripting)
- [2] [Lab: Reflected XSS protected by CSP, with CSP bypass](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-csp-bypass)
- [3] [Lab: Reflected XSS protected by very strict CSP, with dangling markup attack](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-very-strict-csp-with-dangling-markup-attack)
- [4] [Lab: Reflected XSS with AngularJS sandbox escape and CSP](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-and-csp)
- [5] [Lab: Reflected XSS with AngularJS sandbox escape without strings](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-without-strings)
- [6] [Lab: Reflected XSS into attribute with angle brackets HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-attribute-angle-brackets-html-encoded)
- [7] [Lab: Reflected XSS in canonical link tag](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-canonical-link-tag)
- [8] [Lab: Reflected XSS with event handlers and href attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked)
- [9] [Lab: Stored XSS into anchor href attribute with double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded)
- [10] [Lab: Reflected XSS into HTML context with all tags blocked except custom ones](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked)
- [11] [Lab: Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)
- [12] [Lab: Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-double-quotes-encoded-single-quotes-escaped)
- [13] [Lab: Reflected XSS into a JavaScript string with angle brackets HTML encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-html-encoded)
- [14] [Lab: Reflected XSS into a JavaScript string with single quote and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-single-quote-backslash-escaped)
- [15] [Lab: Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped)
- [16] [Lab: Reflected XSS in a JavaScript URL with some characters blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-url-some-characters-blocked)
- [17] [Lab: Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped)
- [18] [Lab: Reflected XSS with some SVG markup allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)
- [19] [Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression)
- [20] [Lab: DOM XSS in document.write sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)
- [21] [Lab: DOM XSS in document.write sink using source location.search inside a select element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element)
- [22] [Lab: Reflected DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected)
- [23] [Lab: Stored DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-stored)
- [24] [Lab: DOM XSS in innerHTML sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)
- [25] [Lab: DOM XSS in jQuery anchor href attribute sink using location.search source](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink)
- [26] [Lab: DOM XSS in jQuery selector sink using a hashchange event](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event)
- [27] [Lab: Exploiting cross-site scripting to capture passwords](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capturing-passwords)
- [28] [Lab: Exploiting XSS to bypass CSRF defenses](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-perform-csrf)
- [29] [Lab: Exploiting cross-site scripting to steal cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies)
- [30] [Lab: Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)
- [31] [Lab: Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)
