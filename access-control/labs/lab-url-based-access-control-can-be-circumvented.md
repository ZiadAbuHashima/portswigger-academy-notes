# Lab: URL-based access control can be circumvented

**Official lab:** [https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented)

## Lab idea

A front-end restriction on an administrative route does not align with how the back end interprets a request. The challenge practices assessing authorization consistency across URL handling layers.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Try to load /admin and observe that you get blocked.
2. Send the request to Burp Repeater.
3. Change the value of the X-Original-URL header to /admin .
4. To delete carlos , add ?username=carlos to the real query string, and change the X-Original-URL path to /admin/delete .

## Payloads / key values
- `/admin`
- `/`
- `X-Original-URL: /invalid`
- `X-Original-URL`
- `carlos`
- `?username=carlos`
- `/admin/delete`

## Official source
- [PortSwigger Academy: Lab: URL-based access control can be circumvented](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented)
