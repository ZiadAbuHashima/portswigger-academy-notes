# Lab: 2FA broken logic

**Official lab:** [Lab: 2FA broken logic](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-broken-logic)

## Lab idea

This challenge focuses on how flaws in the logic that connects a user identity to a second-factor check can undermine two-factor authentication. It practices reviewing the full verification flow and checking that each step stays bound to the intended account.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, log in to your own account and investigate the 2FA verification process.
2. Log out of your account.
3. Send the GET /login2 request to Burp Repeater.
4. Go to the login page and enter your username and password.
5. Send the POST /login2 request to Burp Intruder.
6. In Burp Intruder, set the verify parameter to carlos and add a payload position to the mfa-code parameter.
7. Load the 302 response in the browser.
8. Click My account to solve the lab.

## Payloads / key values
- `POST /login2`
- `verify`
- `GET /login2`
- `carlos`
- `mfa-code`

## Official source
- [PortSwigger Academy: Lab: 2FA broken logic](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-broken-logic)
