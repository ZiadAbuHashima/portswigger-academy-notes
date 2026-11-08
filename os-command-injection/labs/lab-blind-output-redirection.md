# Lab: Blind OS command injection with output redirection

**Official PortSwigger URL:** https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection

## Lab idea

The application does not return command output in its response, but the challenge provides a way for output to be written to an accessible location and retrieved through the application. It practices reasoning about output recovery in a blind command-injection scenario. [1]

[1]: https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection "Lab: Blind OS command injection with output redirection"

## Vulnerability in brief
OS command injection, also known as shell injection, is a vulnerability that lets an attacker cause an application server to run unintended operating-system commands. It commonly occurs when an application builds or invokes a shell command using user-controlled values without keeping those values safely separate from command syntax. Shell metacharacters or substitutions can then change how the command is interpreted.

## Solution idea
1. Use Burp Suite to intercept and modify the request that submits feedback.
2. Modify the email parameter, changing it to: email=||whoami>/var/www/images/output.txt||
3. Now use Burp Suite to intercept and modify the request that loads an image of a product.
4. Modify the filename parameter, changing the value to the name of the file you specified for the output of the injected command: filename=output.txt
5. Observe that the response contains the output from the injected command.

## Payloads / key values
- `email`
- `email=||whoami>/var/www/images/output.txt||`
- `filename`
- `filename=output.txt`

## Official source
- [PortSwigger Academy: Lab: Blind OS command injection with output redirection](https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection)
