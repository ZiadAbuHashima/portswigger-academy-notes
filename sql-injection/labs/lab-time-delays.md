# Lab: Blind SQL injection with time delays

**Official lab:** [Lab: Blind SQL injection with time delays](https://portswigger.net/web-security/sql-injection/blind/lab-time-delays)

## Lab idea

Practices identifying a blind SQLi condition through a controlled difference in response time when content and error messages do not reveal the query outcome.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Visit the front page of the shop, and use Burp Suite to intercept and modify the request containing the TrackingId cookie.
2. Modify the TrackingId cookie, changing it to: TrackingId=x'||pg_sleep(10)--
3. Submit the request and observe that the application takes 10 seconds to respond.

## Payloads / key values
- `TrackingId`
- `TrackingId=x'||pg_sleep(10)--`

## Official source
- [PortSwigger Academy: Lab: Blind SQL injection with time delays](https://portswigger.net/web-security/sql-injection/blind/lab-time-delays)
