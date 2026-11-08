# Lab: Username enumeration via response timing

**Official lab:** [Lab: Username enumeration via response timing](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing)

## Lab idea

This challenge explores response-time differences that can disclose whether a username is valid. It practices assessing timing as an information leak in authentication flows.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, submit an invalid username and password, then send the POST /login request to Burp Repeater.
2. Identify that the X-Forwarded-For header is supported, which allows you to spoof your IP address and bypass the IP-based brute-force protection.
3. Continue experimenting with usernames and passwords.
4. Send this request to Burp Intruder and select Pitchfork attack from the attack type drop-down menu.
- …
6. In the Payloads side panel, add the list of numbers to payload position 1 and add the list of passwords to payload position 2.
7. When the attack is finished, find the response with a 302 status.
8. Log in using the username and password that you identified and access the user account page to solve the lab.

## Payloads / key values
- `POST /login`
- `X-Forwarded-For`
- `username`
- `1`
- `2`
- `password`
- `302`

## Official source
- [PortSwigger Academy: Lab: Username enumeration via response timing](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing)
