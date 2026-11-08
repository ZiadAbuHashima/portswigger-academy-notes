# Lab: Basic password reset poisoning

**Official lab:** [Basic password reset poisoning](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-basic-password-reset-poisoning)

**Lab idea:** This challenge illustrates how password-reset emails can be affected when the application uses an untrusted Host header to form the reset link. It practices tracing how request-derived domain information flows into account-recovery messages and why those links need a trusted origin.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. Go to the login page and notice the "Forgot your password?" functionality.
2. Go to the exploit server and open the email client.
3. Click the link and observe that you are prompted to enter a new password.
4. In Burp, study the HTTP history.
- …
6. Go to your exploit server and open the access log.
7. Go to your email client and copy the genuine password reset URL from your first email.
8. Change Carlos's password to whatever you want, then log in as carlos to solve the lab.

## Payloads / key values
- `temp-forgot-password-token`
- `POST /forgot-password`
- `YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `username`
- `carlos`
- `GET /forgot-password`

## Official source
- [PortSwigger Academy: Lab: Basic password reset poisoning](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-basic-password-reset-poisoning)
