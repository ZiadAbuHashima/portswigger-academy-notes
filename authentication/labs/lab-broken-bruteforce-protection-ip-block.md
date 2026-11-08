# Lab: Broken brute-force protection, IP block

**Official lab:** [Lab: Broken brute-force protection, IP block](https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block)

## Lab idea

This challenge examines whether IP-based login throttling can be undermined by flaws in how failed attempts and client identity are tracked. It practices evaluating the consistency and resilience of brute-force controls.

## Vulnerability in brief
Authentication, often abbreviated **AuthN**, is the process of verifying that a user or client is who they claim to be. It is distinct from authorization (AuthZ), which determines what an authenticated identity is allowed to do. This topic covers vulnerabilities in authentication mechanisms; it is a vulnerability-learning topic, not a general testing category.

## Solution idea
1. With Burp running, investigate the login page.
2. Enter an invalid username and password, then send the POST /login request to Burp Intruder.
3. Click Resource pool to open the Resource pool side panel, then add the attack to a resource pool with Maximum concurrent requests set to 1 .
4. Click Payloads to open the Payloads side panel, then select position 1 from the Payload position drop-down list.
5. Edit the list of candidate passwords and add your own password before each one.
6. Select position 2 from the Payload position drop-down list, then add the password list.
7. When the attack finishes, filter the results to hide responses with a 200 status code.
8. Log in to Carlos's account using the password that you identified and access his account page to solve the lab.

## Payloads / key values
- `POST /login`
- `username`
- `password`
- `1`
- `carlos`
- `2`
- `200`
- `302`

## Official source
- [PortSwigger Academy: Lab: Broken brute-force protection, IP block](https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block)
