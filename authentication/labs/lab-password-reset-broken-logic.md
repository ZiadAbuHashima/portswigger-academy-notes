# Lab: Password reset broken logic

**Official lab:** [Lab: Password reset broken logic](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic)

## Lab idea

This challenge examines whether a password reset properly validates and associates its reset token with the requested account and operation. It practices reviewing reset-state transitions and the integrity of recovery checks.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, click the Forgot your password?
2. Click the Email client button to view the password reset email that was sent.
3. In Burp, go to Proxy > HTTP history and study the requests and responses for the password reset functionality.
4. In Burp Repeater, observe that the password reset functionality still works even if you delete the value of the temp-forgot-password-token parameter in both the URL and request body.
5. In the browser, request a new password reset and change your password again.
6. In Burp Repeater, delete the value of the temp-forgot-password-token parameter in both the URL and request body.
7. In the browser, log in to Carlos's account using the new password you just set.

## Payloads / key values
- `POST /forgot-password?temp-forgot-password-token`
- `temp-forgot-password-token`
- `username`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Password reset broken logic](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic)
