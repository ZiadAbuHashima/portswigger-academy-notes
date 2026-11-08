# Lab: Broken brute-force protection, multiple credentials per request

**Official lab:** [Lab: Broken brute-force protection, multiple credentials per request](https://portswigger.net/web-security/authentication/password-based/lab-broken-brute-force-protection-multiple-credentials-per-request)

## Lab idea

This challenge tests a logic flaw in brute-force defenses when a login request accepts credentials in an unexpected multi-value form. It practices checking that authentication and attempt limits consistently validate the request’s data structure.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, investigate the login page.
2. In Burp Repeater, replace the single string value of the password with an array of strings containing all of the candidate passwords.
3. Send the request.
4. Right-click on this request and select Show response in browser .
5. Click My account to access Carlos's account page and solve the lab.

## Payloads / key values
- `POST /login`
- `JSON`
- `"username" : "carlos", "password" : [ "123456", "password", "qwerty" ... ]`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Broken brute-force protection, multiple credentials per request](https://portswigger.net/web-security/authentication/password-based/lab-broken-brute-force-protection-multiple-credentials-per-request)
