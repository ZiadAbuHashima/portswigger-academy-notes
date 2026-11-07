# Web LLM attacks (LLM attacks)

**Web LLM attacks** are security risks that arise when websites integrate large language models (LLMs) with user input, application data, or tools such as APIs. This is a broad attack category, not one single vulnerability class. An LLM can expose data or invoke capabilities that an attacker cannot access directly, so an unsafe integration can make the model an intermediary to protected systems. [Official topic](https://portswigger.net/web-security/llm-attacks)

## Main concepts

**Prompt injection** uses crafted instructions to influence an LLM’s output or actions. It can be direct, through a user’s prompt, or indirect, through content the model consumes from another source, such as a page, review, or API response. The risk increases when the model cannot reliably distinguish untrusted content from trusted instructions.

When an LLM can call application APIs, functions, or plugins, its **agency** becomes part of the attack surface. Excessive agency describes a model having access to sensitive capabilities that can be persuaded to act unsafely. Those APIs may expose weaknesses of their own, including secondary web vulnerabilities. **Insecure output handling** occurs when model-generated content is passed to another component without appropriate validation or sanitization. Other concerns include sensitive information leakage and attacks mediated by AI-powered scanners.

Common causes include granting a model broader data or API access than its task requires, relying on model instructions to enforce security boundaries, failing to apply authorization in the systems behind its tools, mixing untrusted content into model context, and trusting generated output when it is rendered or processed elsewhere.

## Potential impact

Depending on the integration, an attacker may retrieve sensitive information available to the model, cause unauthorized actions through connected APIs, or use the model to affect other users or systems. Chained weaknesses can include server-side request forgery, SQL or operating-system command injection, and cross-site scripting or cross-site request forgery caused by unsafe output handling.

## High-level assessment context

For authorized testing, identify direct and indirect inputs to the LLM, then establish what data sources and APIs it can access. Assess whether tool calls are constrained by server-side authorization and whether they can create meaningful side effects. Also examine how model output is validated before it is used by downstream systems or displayed in a browser. Use controlled tests and observe effects beyond the chat response; do not assume that a model’s refusal or prompt-level rule is an access-control boundary.

## Prevention principles

Treat every API available to the LLM as if it were publicly callable: enforce authentication, authorization, and privilege checks in the application that performs the operation, not in the model. Give the model only the capabilities and data required for its task, limit access to external data sources, and avoid supplying sensitive information where possible. Sanitize training data and test what the model can reveal. Validate model output before passing it to other components, using protections appropriate to the destination. For consequential API actions, provide an explicit confirmation step. Prompts can guide behavior, but should not be relied on as the security control.

## Lab notes

- [Bypassing AI scanner defenses to exfiltrate sensitive information](labs/lab-bypassing-ai-scanner-defenses-to-exfiltrate-sensitive-information.md)
- [Exploiting AI agents to trigger secondary vulnerabilities](labs/lab-exploiting-target-website-vulnerabilities-to-bypass-restrictions.md)
- [Exploiting AI agents to perform destructive actions](labs/lab-indirect-prompt-injection-via-ai-powered-scan.md)
- [Exploiting AI agents to exfiltrate sensitive information](labs/lab-sensitive-information-exfiltration.md)
- [Exploiting insecure output handling in LLMs](labs/lab-exploiting-insecure-output-handling-in-llms.md)
- [Exploiting LLM APIs with excessive agency](labs/lab-exploiting-llm-apis-with-excessive-agency.md)
- [Exploiting vulnerabilities in LLM APIs](labs/lab-exploiting-vulnerabilities-in-llm-apis.md)
- [Indirect prompt injection](labs/lab-indirect-prompt-injection.md)

## References

- [Web LLM attacks — Web Security Academy](https://portswigger.net/web-security/llm-attacks)
- [Lab: Bypassing AI scanner defenses to exfiltrate sensitive information](https://portswigger.net/web-security/llm-attacks/ai-powered-scanner-vulnerabilities/lab-bypassing-ai-scanner-defenses-to-exfiltrate-sensitive-information)
- [Lab: Exploiting AI agents to trigger secondary vulnerabilities](https://portswigger.net/web-security/llm-attacks/ai-powered-scanner-vulnerabilities/lab-exploiting-target-website-vulnerabilities-to-bypass-restrictions)
- [Lab: Exploiting AI agents to perform destructive actions](https://portswigger.net/web-security/llm-attacks/ai-powered-scanner-vulnerabilities/lab-indirect-prompt-injection-via-ai-powered-scan)
- [Lab: Exploiting AI agents to exfiltrate sensitive information](https://portswigger.net/web-security/llm-attacks/ai-powered-scanner-vulnerabilities/lab-sensitive-information-exfiltration)
- [Lab: Exploiting insecure output handling in LLMs](https://portswigger.net/web-security/llm-attacks/lab-exploiting-insecure-output-handling-in-llms)
- [Lab: Exploiting LLM APIs with excessive agency](https://portswigger.net/web-security/llm-attacks/lab-exploiting-llm-apis-with-excessive-agency)
- [Lab: Exploiting vulnerabilities in LLM APIs](https://portswigger.net/web-security/llm-attacks/lab-exploiting-vulnerabilities-in-llm-apis)
- [Lab: Indirect prompt injection](https://portswigger.net/web-security/llm-attacks/lab-indirect-prompt-injection)
