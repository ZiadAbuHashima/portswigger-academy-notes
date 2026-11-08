# Lab: SQL injection vulnerability allowing login bypass

**Official lab:** [Lab: SQL injection vulnerability allowing login bypass](https://portswigger.net/web-security/sql-injection/lab-login-bypass)

## Lab idea

Practices understanding how SQL injection in authentication logic can alter a credential check and undermine the intended login control.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Use Burp Suite to intercept and modify the login request.
2. Modify the username parameter, giving it the value: administrator'--

## Payloads / key values
- `username`
- `administrator'--`

## Official source
- [PortSwigger Academy: Lab: SQL injection vulnerability allowing login bypass](https://portswigger.net/web-security/sql-injection/lab-login-bypass)
