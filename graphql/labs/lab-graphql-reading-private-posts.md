# Lab: Accessing private GraphQL posts

**Official PortSwigger URL:** https://portswigger.net/web-security/graphql/lab-graphql-reading-private-posts

**Lab idea:** A hidden blog post is omitted from the normal list, while the GraphQL API makes it possible to investigate the post and a password field associated with it. The challenge practices noticing gaps in returned objects and assessing object- and field-level authorization for private content.

## Vulnerability in brief
GraphQL API vulnerabilities is a topic for learning how to assess GraphQL APIs, not one single vulnerability class. The Academy highlights implementation and design flaws: a GraphQL service commonly exposes multiple operations through one endpoint, while each client request selects fields and can invoke queries or state-changing mutations. If schema exposure, authorization, transport handling, or resource controls are weak, a request may reveal data or trigger actions the caller should not be allowed to perform.

## Solution idea
1. In Burp's browser, access the blog page.
2. In Burp, go to Proxy > HTTP history and notice the following:
3. Find the POST /graphql/v1 request.
4. In Repeater, right-click anywhere in the Request panel of the message editor and select GraphQL > Set introspection query to insert an introspection query into the request body.
- …
6. In Repeater, click on the GraphQL tab.
7. In the Query panel, add the postPassword field to the query.
8. Copy the contents of the response's postPassword field and paste them into the Submit solution dialog to solve the lab.

## Payloads / key values
- `id`
- `POST /graphql/v1`
- `BlogPost`
- `postPassword`

## Official source
- [PortSwigger Academy: Lab: Accessing private GraphQL posts](https://portswigger.net/web-security/graphql/lab-graphql-reading-private-posts)
