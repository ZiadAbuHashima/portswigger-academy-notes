# Lab: Multi-step process with no access control on one step

**Official lab:** [https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)

## Lab idea

A role-change workflow has multiple stages, but one stage is missing an access check. The challenge practices verifying authorization throughout a workflow rather than assuming earlier checks protect later stages.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Log in using the admin credentials.
2. Browse to the admin panel, promote carlos , and send the confirmation HTTP request to Burp Repeater.
3. Open a private/incognito browser window, and log in with the non-admin credentials.
4. Copy the non-admin user's session cookie into the existing Repeater request, change the username to yours, and replay it.

## Payloads / key values
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Multi-step process with no access control on one step](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)
