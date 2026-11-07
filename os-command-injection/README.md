# OS command injection (shell injection)

OS command injection, also known as shell injection, is a vulnerability that lets an attacker cause an application server to run unintended operating-system commands. It commonly occurs when an application builds or invokes a shell command using user-controlled values without keeping those values safely separate from command syntax. Shell metacharacters or substitutions can then change how the command is interpreted. [1]

## Main concepts

The application may expose command output directly in its response, making the effect visible in-band. In a blind case, command output is not returned; a tester may instead observe a response-time change or a controlled out-of-band interaction. These different feedback channels affect how the issue is identified, but the underlying weakness is unsafe execution of a command containing untrusted input. [1]

## Impact

Successful injection can allow commands to run with the privileges of the application process. This can compromise the application and its data, affect the host or other infrastructure, and potentially enable movement to connected systems where trust relationships permit it. [1]

## Authorized assessment context

Assess only systems for which testing is explicitly authorized and within scope. At a high level, review features that pass request data to operating-system commands and look for unexpected command output or response changes. Where output is hidden, timing anomalies or a controlled out-of-band signal can indicate execution. A normal-looking response alone does not rule out a blind vulnerability. [1]

## Prevention

The strongest prevention is to avoid invoking operating-system commands from application code and use safer platform APIs instead. If a command is necessary, keep untrusted values out of shell-interpreted command strings and validate inputs against strict expectations, such as an allowlist or a required numeric format. Do not rely on escaping shell metacharacters as the sole defense; it is error-prone and may be bypassed. [1]

## Lab notes

- [Lab: Blind OS command injection with out-of-band interaction](labs/lab-blind-out-of-band.md) [2]
- [Lab: Blind OS command injection with out-of-band data exfiltration](labs/lab-blind-out-of-band-data-exfiltration.md) [3]
- [Lab: Blind OS command injection with output redirection](labs/lab-blind-output-redirection.md) [4]
- [Lab: Blind OS command injection with time delays](labs/lab-blind-time-delays.md) [5]
- [Lab: OS command injection, simple case](labs/lab-simple.md) [6]

## References

[1]: https://portswigger.net/web-security/os-command-injection "What is OS command injection, and how to prevent it?"
[2]: https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band "Lab: Blind OS command injection with out-of-band interaction"
[3]: https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band-data-exfiltration "Lab: Blind OS command injection with out-of-band data exfiltration"
[4]: https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection "Lab: Blind OS command injection with output redirection"
[5]: https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays "Lab: Blind OS command injection with time delays"
[6]: https://portswigger.net/web-security/os-command-injection/lab-simple "Lab: OS command injection, simple case"
