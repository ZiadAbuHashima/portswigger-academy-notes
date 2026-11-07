# Prototype pollution (PP)

Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages. [1]

## Main concepts

A **source** is an input path that can influence a prototype. A **gadget** is an inherited property that application code uses unsafely. A **sink** is the operation or element that turns the gadget's value into an effect, such as executing JavaScript or a system command. A pollution source alone may not be exploitable; impact depends on whether the application has a reachable gadget and sink. [1]

## Impact

In client-side code, prototype pollution can lead to DOM-based cross-site scripting (DOM XSS). On the server, it can affect application behavior and, in some configurations, contribute to privilege escalation or remote code execution (RCE). The severity depends on the available gadgets, sinks, and application context. [1]

## High-level detection and assessment

During authorized testing, review how URL parameters, fragments, JSON bodies, and web messages are parsed and merged into JavaScript objects. Look for changes that appear as inherited properties or cause consistent behavioral differences, then assess whether application code consumes the affected property in an unsafe way. A missing reflected property does not by itself rule out server-side pollution; controlled, non-destructive behavior changes can also be informative. Prototype changes can disrupt or crash an application, so use cautious, low-impact checks and stay within scope. [1]

## Prevention

Prefer allowlists of accepted property keys and safe merge approaches over relying on a denylist alone; incomplete filters can miss alternate paths or obfuscations. Where appropriate, prevent changes to prototypes, create objects with a `null` prototype to remove inherited properties, or use `Map` and `Set` for collections. Patch identified pollution flaws even when no current gadget is known, because later application or library changes may introduce one. [2]

## Lab notes

- [Client-side prototype pollution via browser APIs](labs/lab-prototype-pollution-client-side-prototype-pollution-via-browser-apis.md)
- [Client-side prototype pollution in third-party libraries](labs/lab-prototype-pollution-client-side-prototype-pollution-in-third-party-libraries.md)
- [Client-side prototype pollution via flawed sanitization](labs/lab-prototype-pollution-client-side-prototype-pollution-via-flawed-sanitization.md)
- [DOM XSS via an alternative prototype pollution vector](labs/lab-prototype-pollution-dom-xss-via-an-alternative-prototype-pollution-vector.md)
- [DOM XSS via client-side prototype pollution](labs/lab-prototype-pollution-dom-xss-via-client-side-prototype-pollution.md)
- [Bypassing flawed input filters for server-side prototype pollution](labs/lab-bypassing-flawed-input-filters-for-server-side-prototype-pollution.md)
- [Detecting server-side prototype pollution without polluted property reflection](labs/lab-detecting-server-side-prototype-pollution-without-polluted-property-reflection.md)
- [Exfiltrating sensitive data via server-side prototype pollution](labs/lab-exfiltrating-sensitive-data-via-server-side-prototype-pollution.md)
- [Privilege escalation via server-side prototype pollution](labs/lab-privilege-escalation-via-server-side-prototype-pollution.md)
- [Remote code execution via server-side prototype pollution](labs/lab-remote-code-execution-via-server-side-prototype-pollution.md)

## References

[1]: https://portswigger.net/web-security/prototype-pollution "PortSwigger Web Security Academy: Prototype pollution"
[2]: https://portswigger.net/web-security/prototype-pollution/preventing "PortSwigger Web Security Academy: Preventing prototype pollution vulnerabilities"
