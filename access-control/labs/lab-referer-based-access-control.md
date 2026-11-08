# Lab: Referer-based access control

**Official lab:** [https://portswigger.net/web-security/access-control/lab-referer-based-access-control](https://portswigger.net/web-security/access-control/lab-referer-based-access-control)

## Lab idea

The application uses the Referer request header to gate administrative functionality. The challenge practices recognizing that request metadata supplied by a client is not a reliable authorization boundary.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Log in using the admin credentials.
2. Browse to the admin panel, promote carlos , and send the HTTP request to Burp Repeater.
3. Open a private/incognito browser window, and log in with the non-admin credentials.
4. Browse to /admin-roles?username=carlos&action=upgrade and observe that the request is treated as unauthorized due to the absent Referer header.
5. Copy the non-admin user's session cookie into the existing Burp Repeater request, change the username to yours, and replay it.

## Payloads / key values
- `carlos`
- `/admin-roles?username=carlos&action=upgrade`

## Official source
- [PortSwigger Academy: Lab: Referer-based access control](https://portswigger.net/web-security/access-control/lab-referer-based-access-control)
