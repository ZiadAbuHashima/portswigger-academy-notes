# Lab: Insecure direct object references

**Official lab:** [https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references](https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references)

## Lab idea

The challenge centers on chat transcripts stored as server-side files and exposed through static references. It practices recognizing how direct object references can expose another user’s data when access is not properly tied to ownership.

## Vulnerability in brief
Access control decides whether an authenticated user may perform a requested action or access a particular resource. It is distinct from authentication, which establishes identity, and session management, which associates requests with that identity. Broken access control occurs when an application lets a user access a resource or perform an action outside their authorization. Insecure direct object reference (IDOR) is a familiar subcategory, not a synonym for every access-control flaw.

## Solution idea
1. Select the Live chat tab.
2. Send a message and then select View transcript .
3. Review the URL and observe that the transcripts are text files assigned a filename containing an incrementing number.
4. Change the filename to 1.txt and review the text.
5. Return to the main lab page and log in using the stolen credentials.

## Payloads / key values
- `1.txt`

## Official source
- [PortSwigger Academy: Lab: Insecure direct object references](https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references)
