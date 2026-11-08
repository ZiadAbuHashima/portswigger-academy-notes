# Lab: User role can be modified in user profile

**Official lab:** [https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile)

## Lab idea

A profile-update function exposes a role value that affects access to administration. The challenge practices assessing whether user-editable profile changes can improperly influence authorization privileges.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Log in using the supplied credentials and access your account page.
2. Use the provided feature to update the email address associated with your account.
3. Observe that the response contains your role ID.
4. Send the email submission request to Burp Repeater, add "roleid":2 into the JSON in the request body, and resend it.
5. Observe that the response shows your roleid has changed to 2.
6. Browse to /admin and delete carlos .

## Payloads / key values
- `"roleid":2`
- `roleid`
- `/admin`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: User role can be modified in user profile](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile)
