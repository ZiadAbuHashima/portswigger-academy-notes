# Lab: Information disclosure in error messages

**Official URL:** https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages

**Lab idea:** Verbose errors expose details about a third-party framework and its version. The challenge practices assessing error responses as a source of technical information and recognizing when exposed version information may be security-relevant.

## Vulnerability in brief
Information disclosure is a vulnerability class in which a website unintentionally exposes sensitive information. The leaked content can include personal or business data, or technical details about the application and its infrastructure. Unlike a general learning category, this topic covers a distinct security weakness: unintended disclosure through application responses or exposed resources.

## Solution idea
1. With Burp running, open one of the product pages.
2. In Burp, go to "Proxy" > "HTTP history" and notice that the GET request for product pages contains a productID parameter.
3. In Burp Repeater, change the value of the productId parameter to a non-integer data type, such as a string.
4. The unexpected data type causes an exception, and a full stack trace is displayed in the response.
5. Go back to the lab, click "Submit solution", and enter 2 2.3.31 to solve the lab.

## Payloads / key values
- `GET`
- `productID`
- `GET /product?productId=1`
- `productId`
- `GET /product?productId="example"`

## Official source
- [PortSwigger Academy: Lab: Information disclosure in error messages](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages)
