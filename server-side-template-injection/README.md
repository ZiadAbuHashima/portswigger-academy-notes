# Server-side template injection (SSTI)

Server-side template injection (SSTI) is a vulnerability in which untrusted input is interpreted as template-language syntax and evaluated by a server-side template engine. Template engines normally combine fixed templates with changing data to render pages. The vulnerability arises when applications construct template source by concatenating user input into it instead of supplying that input strictly as data. This may happen accidentally through unsafe template design or intentionally when an application permits users to submit or modify templates. [1]

## Main concepts

The key distinction is whether user input is inserted into an existing template as a value or becomes part of the template source itself. SSTI may occur in plain-text template content or within a template expression, and the context affects how the issue appears. Different engines use different syntax and capabilities, so identifying the engine and context matters during assessment. Errors, unexpected rendering, or evidence that a benign expression is evaluated on the server can indicate a problem; a single matching response is not conclusive because syntax can overlap between engines. [1]

## Impact

The consequences depend on the template engine, the application's configuration, and what objects and functions are exposed to templates. SSTI can enable disclosure of sensitive data or server-side files. In severe cases, it can lead to remote code execution, compromise of the back-end host, or attacks against internal infrastructure. A sandbox may limit access, but a poorly designed or bypassable sandbox should not be treated as a reliable boundary. [1]

## High-level detection and assessment

During authorized testing, examine features that place user-controlled values into rendered content, including customizable text and user-editable templates. Look for template-like input that produces unexpected server-side evaluation, distinguishable error behavior, or other rendering changes. Assess plain-text and expression contexts, and use only harmless, controlled checks on systems within scope. If a signal appears, determine the likely engine from reliable behavior and error information rather than assuming it from one response. [1]

## Prevention

Prefer fixed templates with untrusted values passed in as data; do not concatenate user input into template source. Avoid allowing users to modify or submit executable templates unless this is essential. Where feasible, use a logic-less template engine and keep presentation separate from application logic. If untrusted template execution is unavoidable, restrict available modules and functions with a carefully designed sandbox, and isolate the rendering environment with least privilege and strong containment. Sandboxing is difficult and can be bypassed, so it should complement—not replace—safe template construction. [1]

## Lab notes

- [Basic server-side template injection](labs/lab-server-side-template-injection-basic.md)
- [Basic server-side template injection (code context)](labs/lab-server-side-template-injection-basic-code-context.md)
- [Server-side template injection in a sandboxed environment](labs/lab-server-side-template-injection-in-a-sandboxed-environment.md)
- [Server-side template injection in an unknown language with a documented exploit](labs/lab-server-side-template-injection-in-an-unknown-language-with-a-documented-exploit.md)
- [Server-side template injection using documentation](labs/lab-server-side-template-injection-using-documentation.md)
- [Server-side template injection with a custom exploit](labs/lab-server-side-template-injection-with-a-custom-exploit.md)
- [Server-side template injection with information disclosure via user-supplied objects](labs/lab-server-side-template-injection-with-information-disclosure-via-user-supplied-objects.md)

## References

[1]: https://portswigger.net/web-security/server-side-template-injection "Server-side template injection"

- [Lab: Basic server-side template injection](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic)
- [Lab: Basic server-side template injection (code context)](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic-code-context)
- [Lab: Server-side template injection in a sandboxed environment](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-in-a-sandboxed-environment)
- [Lab: Server-side template injection in an unknown language with a documented exploit](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-in-an-unknown-language-with-a-documented-exploit)
- [Lab: Server-side template injection using documentation](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-using-documentation)
- [Lab: Server-side template injection with a custom exploit](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-with-a-custom-exploit)
- [Lab: Server-side template injection with information disclosure via user-supplied objects](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-with-information-disclosure-via-user-supplied-objects)
