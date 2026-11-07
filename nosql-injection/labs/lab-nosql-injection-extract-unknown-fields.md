# Lab: Exploiting NoSQL operator injection to extract unknown fields

**Official PortSwigger URL:** https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-unknown-fields

**Lab idea:** The MongoDB-backed user lookup is vulnerable to NoSQL injection. The challenge involves discovering previously unknown user-data fields and recovering a password-reset token needed to access Carlos's account. It practices reasoning about semi-structured records and query behavior when field names are not known in advance.
