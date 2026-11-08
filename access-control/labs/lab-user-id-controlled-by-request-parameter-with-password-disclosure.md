# Lab: User ID controlled by request parameter with password disclosure

**Official lab:** [https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure)

## Lab idea

A user account page includes password information and is vulnerable to unauthorized access to another account’s page. The challenge practices assessing object-level access checks and the handling of sensitive credentials.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Log in using the supplied credentials and access the user account page.
2. Change the "id" parameter in the URL to administrator .
3. View the response in Burp and observe that it contains the administrator's password.
4. Log in to the administrator account and delete carlos .

## Payloads / key values
- `administrator`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: User ID controlled by request parameter with password disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure)
