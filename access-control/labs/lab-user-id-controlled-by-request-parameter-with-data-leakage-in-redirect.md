# Lab: User ID controlled by request parameter with data leakage in redirect

**Official lab:** [https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect)

## Lab idea

Sensitive information appears in the body of a redirect response when access to another user’s data is attempted. The challenge practices examining complete responses, not only the redirect outcome, for unintended disclosure.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Log in using the supplied credentials and access your account page.
2. Send the request to Burp Repeater.
3. Change the "id" parameter to carlos .
4. Observe that although the response is now redirecting you to the home page, it has a body containing the API key belonging to carlos .
5. Submit the API key.

## Payloads / key values
- `carlos`

## Official source
- [PortSwigger Academy: Lab: User ID controlled by request parameter with data leakage in redirect](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect)
