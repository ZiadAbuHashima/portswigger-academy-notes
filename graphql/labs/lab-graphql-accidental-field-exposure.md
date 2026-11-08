# Lab: Accidental exposure of private GraphQL fields

**Official PortSwigger URL:** https://portswigger.net/web-security/graphql/lab-graphql-accidental-field-exposure

**Lab idea:** The challenge centers on a GraphQL user-management API that exposes credential-related fields through an access-control weakness. It practices recognizing how field selection and object access can reveal information that should remain private, and understanding the security impact of inadequate authorization.

## Vulnerability in brief
GraphQL API vulnerabilities is a topic for learning how to assess GraphQL APIs, not one single vulnerability class. The Academy highlights implementation and design flaws: a GraphQL service commonly exposes multiple operations through one endpoint, while each client request selects fields and can invoke queries or state-changing mutations. If schema exposure, authorization, transport handling, or resource controls are weak, a request may reveal data or trigger actions the caller should not be allowed to perform.

## Solution idea
1. In Burp's browser, access the lab and select My account .
2. Attempt to log in to the site.
3. In Burp, go to Proxy > HTTP history and notice that the login attempt is sent as a GraphQL mutation containing a username and password.
4. Right-click the login request and select Send to Repeater .
- …
6. In Repeater, click Send .
7. Select the GraphQL tab and test alternative values for the id variable until the API returns the administrator's credentials.
8. Log in to the site as the administrator, go to the Admin panel, and delete carlos to solve the lab.

## Payloads / key values
- `getUser`
- `id`
- `0`
- `1`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Accidental exposure of private GraphQL fields](https://portswigger.net/web-security/graphql/lab-graphql-accidental-field-exposure)
