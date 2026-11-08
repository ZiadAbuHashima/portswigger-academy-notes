# Lab: Username enumeration via account lock

**Official lab:** [Lab: Username enumeration via account lock](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-account-lock)

## Lab idea

This challenge focuses on an account-locking behavior that reveals whether a username exists. It practices identifying account-state side channels and assessing their impact on login security.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, investigate the login page and submit an invalid username and password.
2. Select Cluster bomb attack from the attack type drop-down menu.
3. In the Payloads side panel, add the list of usernames for the first payload position.
4. In the results, notice that the responses for one of the usernames were longer than responses when using other usernames.
5. Create a new Burp Intruder attack on the POST /login request, but this time select Sniper attack from the attack type drop-down menu.
6. Add the list of passwords to the payload set and create a grep extraction rule for the error message.
7. In the results, look at the grep extract column.
8. Wait for a minute to allow the account lock to reset.

## Payloads / key values
- `POST /login`
- `username`
- `username=§invalid-username§&password=example§§`
- `You have made too many incorrect login attempts.`
- `password`

## Official source
- [PortSwigger Academy: Lab: Username enumeration via account lock](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-account-lock)
