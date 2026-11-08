# Lab: Blind OS command injection with time delays

**Official PortSwigger URL:** https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays

## Lab idea

This challenge hides command output and asks the learner to recognize blind command execution through a deliberate delay in the application's response. It practices using timing as a high-level signal when direct output is unavailable. [1]

[1]: https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays "Lab: Blind OS command injection with time delays"

## Vulnerability in brief
OS command injection, also known as shell injection, is a vulnerability that lets an attacker cause an application server to run unintended operating-system commands. It commonly occurs when an application builds or invokes a shell command using user-controlled values without keeping those values safely separate from command syntax. Shell metacharacters or substitutions can then change how the command is interpreted.

## Solution idea
1. Use Burp Suite to intercept and modify the request that submits feedback.
2. Modify the email parameter, changing it to: email=x||ping+-c+10+127.0.0.1||
3. Observe that the response takes 10 seconds to return.

## Payloads / key values
- `email`
- `email=x||ping+-c+10+127.0.0.1||`

## Official source
- [PortSwigger Academy: Lab: Blind OS command injection with time delays](https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays)
