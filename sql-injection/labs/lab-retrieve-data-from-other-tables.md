# Lab: SQL injection UNION attack, retrieving data from other tables

**Official lab:** [Lab: SQL injection UNION attack, retrieving data from other tables](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables)

## Lab idea

Practices combining UNION-style SQLi concepts to retrieve records from another database table in an authorized lab environment.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Determine the number of columns that are being returned by the query and which columns contain text data .
3. Use the following payload to retrieve the contents of the users table: '+UNION+SELECT+username,+password+FROM+users--
4. Verify that the application's response contains usernames and passwords.

## Payloads / key values
- `'+UNION+SELECT+'abc','def'--`
- `users`
- `'+UNION+SELECT+username,+password+FROM+users--`

## Official source
- [PortSwigger Academy: Lab: SQL injection UNION attack, retrieving data from other tables](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables)
