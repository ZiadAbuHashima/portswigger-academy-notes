# Lab: Username enumeration via different responses

**Official lab:** [Lab: Username enumeration via different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses)

## Lab idea

This challenge uses distinguishable login outcomes to reveal valid usernames before password guessing. It practices comparing response behavior and understanding how enumeration increases risk.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, investigate the login page and submit an invalid username and password.
2. In Burp, go to Proxy > HTTP history and find the POST /login request.
3. In Burp Intruder, notice that the username parameter is automatically set as a payload position.
4. Make sure that Sniper attack is selected.
- …
6. In the Payloads side panel, clear the list of usernames and replace it with the list of candidate passwords.
7. When the attack is finished, look at the Status column.
8. Log in using the username and password that you identified and access the user account page to solve the lab.

## Payloads / key values
- `POST /login`
- `username`
- `§`
- `username=§invalid-username§`
- `Invalid username`
- `Incorrect password`
- `password`
- `username=identified-user&password=§invalid-password§`
- `200`
- `302`

## Official source
- [PortSwigger Academy: Lab: Username enumeration via different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses)
