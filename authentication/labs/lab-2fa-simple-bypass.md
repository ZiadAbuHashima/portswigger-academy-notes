# Lab: 2FA simple bypass

**Official lab:** [Lab: 2FA simple bypass](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass)

## Lab idea

This challenge explores whether a protected account page remains accessible when the second authentication step has not been completed. It practices checking that authorization to continue is contingent on successful multi-factor verification.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. Log in to your own account.
2. Go to your account page and make a note of the URL.
3. Log out of your account.
4. Log in using the victim's credentials.
5. When prompted for the verification code, manually change the URL to navigate to /my-account .

## Payloads / key values
- `/my-account`

## Official source
- [PortSwigger Academy: Lab: 2FA simple bypass](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass)
