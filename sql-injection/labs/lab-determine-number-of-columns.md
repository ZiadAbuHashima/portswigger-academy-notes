# Lab: SQL injection UNION attack, determining the number of columns returned by the query

**Official lab:** [Lab: SQL injection UNION attack, determining the number of columns returned by the query](https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)

## Lab idea

Practices the initial compatibility assessment for a UNION-style SQLi issue by determining the number of columns in the original query result.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Modify the category parameter, giving it the value '+UNION+SELECT+NULL-- .
3. Modify the category parameter to add an additional column containing a null value: '+UNION+SELECT+NULL,NULL--
4. Continue adding null values until the error disappears and the response includes additional content containing the null values.

## Payloads / key values
- `category`
- `'+UNION+SELECT+NULL--`
- `'+UNION+SELECT+NULL,NULL--`

## Official source
- [PortSwigger Academy: Lab: SQL injection UNION attack, determining the number of columns returned by the query](https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)
