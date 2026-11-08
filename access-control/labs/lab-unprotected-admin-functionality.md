# Lab: Unprotected admin functionality

**Official lab:** [https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)

## Lab idea

An administrative panel is available without an effective authorization check, and its location is disclosed by the application. The challenge practices distinguishing hidden or undiscoverable navigation from actual access control.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Go to the lab and view robots.txt by appending /robots.txt to the lab URL.
2. In the URL bar, replace /robots.txt with /administrator-panel to load the admin panel.
3. Delete carlos .

## Payloads / key values
- `robots.txt`
- `/robots.txt`
- `Disallow`
- `/administrator-panel`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Unprotected admin functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)
