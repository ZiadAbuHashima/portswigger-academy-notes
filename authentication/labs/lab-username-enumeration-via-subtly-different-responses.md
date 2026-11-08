# Lab: Username enumeration via subtly different responses

**Official lab:** [Lab: Username enumeration via subtly different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses)

## Lab idea

This challenge focuses on a small, easy-to-overlook difference in login responses that reveals valid usernames. It practices careful comparison of error behavior, not just obvious status or page changes.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, submit an invalid username and password.
2. Go to Intruder .
3. In the Payloads side panel, make sure that the Simple list payload type is selected and add the list of candidate usernames.
4. Click on the Settings tab to open the Settings side panel.
- …
6. In the Payloads side panel, clear the list of usernames and replace it with the list of passwords.
7. When the attack is finished, notice that one of the requests received a 302 response.
8. Log in using the username and password that you identified and access the user account page to solve the lab.

## Payloads / key values
- `username`
- `POST /login`
- `Invalid username or password.`
- `password`
- `username=identified-user&password=§invalid-password§`
- `302`

## Official source
- [PortSwigger Academy: Lab: Username enumeration via subtly different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses)
