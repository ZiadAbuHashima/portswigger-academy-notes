# Lab: SQL injection UNION attack, finding a column containing text

**Official lab:** [Lab: SQL injection UNION attack, finding a column containing text](https://portswigger.net/web-security/sql-injection/union-attacks/lab-find-column-containing-text)

## Lab idea

Practices determining which result column can display text when constructing a UNION-style SQLi assessment.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Determine the number of columns that are being returned by the query .
3. Try replacing each null with the random value provided by the lab, for example: '+UNION+SELECT+'abcdef',NULL,NULL--
4. If an error occurs, move on to the next null and try that instead.

## Payloads / key values
- `category`
- `'+UNION+SELECT+NULL,NULL,NULL--`
- `'+UNION+SELECT+'abcdef',NULL,NULL--`

## Official source
- [PortSwigger Academy: Lab: SQL injection UNION attack, finding a column containing text](https://portswigger.net/web-security/sql-injection/union-attacks/lab-find-column-containing-text)
