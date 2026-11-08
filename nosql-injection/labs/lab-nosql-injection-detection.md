# Lab: Detecting NoSQL injection

**Official PortSwigger URL:** https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-detection

**Lab idea:** The product category filter is backed by MongoDB and is vulnerable to NoSQL injection. The challenge is to recognize that supplied input can affect server-side query behavior and use that understanding to make unreleased products appear. It practices identifying syntax injection through observable response differences.

## Vulnerability in brief
NoSQL injection is a vulnerability in which untrusted input interferes with the queries an application sends to a NoSQL database. Unlike SQL databases, NoSQL systems do not share one query language or data model, so the exact syntax and behavior vary by database. PortSwigger's topic focuses on general testing concepts and MongoDB examples. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Solution idea
1. In Burp's browser, access the lab and click on a product category filter.
2. In Burp, go to Proxy > HTTP history .
3. In Repeater, submit a ' character in the category parameter.
4. Submit a valid JavaScript payload in the value of the category query parameter.
5. Identify whether you can inject boolean conditions to change the response:
6. Submit a boolean condition that always evaluates to true in the category parameter.
7. Right-click the response and select Show response in browser .
8. Copy the URL and load it in Burp's browser.

## Payloads / key values
- `'`
- `Gifts'+'`
- `Ctrl-U`
- `Gifts' && 0 && 'x`
- `Gifts' && 1 && 'x`
- `Gifts'||1||'`

## Official source
- [PortSwigger Academy: Lab: Detecting NoSQL injection](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-detection)
