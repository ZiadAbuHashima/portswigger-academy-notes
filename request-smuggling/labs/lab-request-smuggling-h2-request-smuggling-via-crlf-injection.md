# Lab: HTTP/2 request smuggling via CRLF injection

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-smuggling-via-crlf-injection](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-smuggling-via-crlf-injection)

## Lab idea

The challenge centers on HTTP/2 downgrading and insufficient sanitization of incoming headers. It practices identifying how this combination can disrupt request boundaries and lead to another user’s account being exposed.
