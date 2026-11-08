# Lab: Brute-forcing a stay-logged-in cookie

**Official lab:** [Lab: Brute-forcing a stay-logged-in cookie](https://portswigger.net/web-security/authentication/other-mechanisms/lab-brute-forcing-a-stay-logged-in-cookie)

## Lab idea

This challenge examines a persistent-login cookie whose construction makes it susceptible to guessing. It practices assessing the security and entropy of long-lived authentication tokens, not just the primary login form.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, log in to your own account with the Stay logged in option selected.
2. Examine this cookie in the Inspector panel and notice that it is Base64-encoded.
3. Log out of your account.
4. In the most recent GET /my-account?id=wiener request highlight the stay-logged-in cookie parameter and send the request to Burp Intruder.
- …
6. Notice that the generated payload was used to successfully load your own account page.
7. Make the following adjustments and then repeat this attack:
8. When the attack is finished, the lab will be solved.

## Payloads / key values
- `stay-logged-in`
- `wiener:51dc30ddc473d43a6011e9ebba6ca770`
- `base64(username+':'+md5HashOfPassword)`
- `GET /my-account?id=wiener`
- `MD5`
- `wiener:`
- `Base64-encode`
- `Update email`
- `id`
- `carlos`
- `wiener`
- `carlos:`

## Official source
- [PortSwigger Academy: Lab: Brute-forcing a stay-logged-in cookie](https://portswigger.net/web-security/authentication/other-mechanisms/lab-brute-forcing-a-stay-logged-in-cookie)
