# Lab: Password brute-force via password change

**Official lab:** [Lab: Password brute-force via password change](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-brute-force-via-password-change)

## Lab idea

This challenge focuses on a password-change workflow that can disclose whether a candidate current password is correct. It practices assessing authentication-related account-management features for information leaks and guessing risks.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, log in and experiment with the password change functionality.
2. Notice the behavior when you enter the wrong current password.
3. Enter your correct current password and two new passwords that do not match.
4. In Burp Intruder, change the username parameter to carlos and add a payload position to the current-password parameter.
- …
6. When the attack finished, notice that one response was found that contains the New passwords do not match message.
7. In the browser, log out of your own account and lock back in with the username carlos and the password that you just identified.
8. Click My account to solve the lab.

## Payloads / key values
- `Current password is incorrect`
- `New passwords do not match`
- `POST /my-account/change-password`
- `username`
- `carlos`
- `current-password`
- `username=carlos&current-password=§incorrect-password§&new-password-1=123&new-password-2=abc`

## Official source
- [PortSwigger Academy: Lab: Password brute-force via password change](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-brute-force-via-password-change)
