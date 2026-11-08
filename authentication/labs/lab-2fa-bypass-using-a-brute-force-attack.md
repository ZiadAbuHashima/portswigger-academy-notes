# Lab: 2FA bypass using a brute-force attack

**Official lab:** [Lab: 2FA bypass using a brute-force attack](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-bypass-using-a-brute-force-attack)

## Lab idea

This challenge examines whether a short second-factor code can be guessed when protections are inadequate. It practices assessing verification-code strength together with rate limits, lockouts, and session handling.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, log in as carlos and investigate the 2FA verification process.
2. In Burp, click Settings to open the Settings dialog, then click Sessions .
3. In the dialog, go to the Scope tab.
4. Go back to the Details tab and under Rule Actions , click Add > Run a macro .
- …
6. Click on Resource pool to open the Resource pool side panel.
7. Start the attack.
8. Click My account to solve the lab.

## Payloads / key values
- `carlos`
- `GET /login POST /login GET /login2`
- `POST /login2`
- `mfa-code`
- `1`
- `302`

## Official source
- [PortSwigger Academy: Lab: 2FA bypass using a brute-force attack](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-bypass-using-a-brute-force-attack)
