# Lab: Exploiting NoSQL operator injection to bypass authentication

**Official PortSwigger URL:** https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-bypass-authentication

**Lab idea:** The login feature uses MongoDB and is vulnerable to operator injection. The challenge is to bypass the login checks and access the administrator account. It practices recognizing how query operators can change authentication query results.

## Vulnerability in brief
NoSQL injection is a vulnerability in which untrusted input interferes with the queries an application sends to a NoSQL database. Unlike SQL databases, NoSQL systems do not share one query language or data model, so the exact syntax and behavior vary by database. PortSwigger's topic focuses on general testing concepts and MongoDB examples. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Solution idea
1. In Burp's browser, log in to the application using the credentials wiener:peter .
2. In Burp, go to Proxy > HTTP history .
3. In Repeater, test the username and password parameters to determine whether they allow you to inject MongoDB operators:
4. With the password parameter set as {"$ne":""} , change the value of the username parameter to {"$regex":"admin.*"}, then send the request again.
5. Right-click the response, then select Show response in browser .
6. Paste the URL into Burp's browser to log in as the administrator user.

## Payloads / key values
- `wiener:peter`
- `POST /login`
- `username`
- `"wiener"`
- `{"$ne":""}`
- `{"$regex":"wien.*"}`
- `$regex`
- `"peter"`
- `{"$regex":"admin.*"},`
- `administrator`

## Official source
- [PortSwigger Academy: Lab: Exploiting NoSQL operator injection to bypass authentication](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-bypass-authentication)
