# Lab: OS command injection, simple case

**Official PortSwigger URL:** https://portswigger.net/web-security/os-command-injection/lab-simple

## Lab idea

The product stock checker includes user-supplied identifiers in a shell command and returns command output in its response. The challenge practices recognizing a direct, in-band command-injection signal and determining the server's current user. [1]

[1]: https://portswigger.net/web-security/os-command-injection/lab-simple "Lab: OS command injection, simple case"

## Vulnerability in brief
OS command injection, also known as shell injection, is a vulnerability that lets an attacker cause an application server to run unintended operating-system commands. It commonly occurs when an application builds or invokes a shell command using user-controlled values without keeping those values safely separate from command syntax. Shell metacharacters or substitutions can then change how the command is interpreted.

## Solution idea
1. Use Burp Suite to intercept and modify a request that checks the stock level.
2. Modify the storeID parameter, giving it the value 1|whoami .
3. Observe that the response contains the name of the current user.

## Payloads / key values
- `storeID`
- `1|whoami`

## Official source
- [PortSwigger Academy: Lab: OS command injection, simple case](https://portswigger.net/web-security/os-command-injection/lab-simple)
