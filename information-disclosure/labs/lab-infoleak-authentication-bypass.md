# Lab: Authentication bypass via information disclosure

**Official URL:** https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass

**Lab idea:** The administration interface relies on a custom HTTP header whose name is not initially known. The challenge practices recognizing how request-handling behavior can disclose that missing implementation detail, then understanding its relationship to an authentication bypass.

## Vulnerability in brief
Information disclosure is a vulnerability class in which a website unintentionally exposes sensitive information. The leaked content can include personal or business data, or technical details about the application and its infrastructure. Unlike a general learning category, this topic covers a distinct security weakness: unintended disclosure through application responses or exposed resources.

## Solution idea
1. In Burp Repeater, browse to GET /admin .
2. Send the request again, but this time use the TRACE method: TRACE /admin
3. Study the response.
4. Go to Proxy > Match and replace .
- …
6. Under Auto-modified request , notice that Burp has added the X-Custom-IP-Authorization header to the modified request.
7. Click OK .
8. Browse to the home page.

## Payloads / key values
- `GET /admin`
- `TRACE`
- `TRACE /admin`
- `X-Custom-IP-Authorization`
- `localhost`
- `X-Custom-IP-Authorization: 127.0.0.1`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Authentication bypass via information disclosure](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass)
