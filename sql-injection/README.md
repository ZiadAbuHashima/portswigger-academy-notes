# SQL injection (SQLi)

SQL injection (SQLi) is a web vulnerability in which untrusted input changes the meaning of a SQL query made by an application. It commonly occurs when an application builds a query by concatenating user-controlled values into SQL instead of keeping query structure separate from data. Inputs may arrive through form fields, URL parameters, cookies, headers, or other request data. Injection can occur in different query types and positions, not only in a `SELECT` statement's `WHERE` clause.

## Main concepts

SQLi can expose hidden records or alter application logic, such as database-backed access checks. When query results are reflected in the response, an attacker may be able to combine queries to retrieve data from other tables (a UNION-style attack). In blind SQLi, query results are not directly displayed; information may instead be inferred from response differences, database errors, response timing, or out-of-band interactions. The observable channel depends on the application's behavior and database configuration.

## Impact

Successful SQLi can expose sensitive information, including credentials, payment details, and personal data, or permit unauthorized changes or deletion of records. Depending on database privileges and environment, further consequences can include compromise of back-end infrastructure, persistent access, or denial of service.

## High-level detection and assessment

For authorized testing, review every input that may reach database operations, including less obvious state such as cookies. Use controlled, non-destructive tests and compare normal responses with carefully chosen SQL-relevant variations. Look for consistent changes in returned content or application logic, database-related errors, repeatable timing differences, or authorized out-of-band callbacks. Absence of visible errors does not rule out blind SQLi. Keep tests scoped to approved targets and avoid operations that could modify or delete data.

## Prevention

Use parameterized queries or prepared statements so input is handled as data rather than executable SQL. Do not construct query fragments through unsafe concatenation. Where dynamic identifiers or sort directions cannot be bound as values, select them from strict server-side allowlists. Apply least privilege to database accounts, avoid exposing detailed database errors to users, and use input validation and monitoring as supplementary safeguards rather than substitutes for parameterization.

## Lab notes

- [Blind SQL injection with conditional errors](labs/lab-conditional-errors.md)
- [Blind SQL injection with conditional responses](labs/lab-conditional-responses.md)
- [Blind SQL injection with out-of-band interaction](labs/lab-out-of-band.md)
- [Blind SQL injection with out-of-band data exfiltration](labs/lab-out-of-band-data-exfiltration.md)
- [Visible error-based SQL injection](labs/lab-sql-injection-visible-error-based.md)
- [Blind SQL injection with time delays](labs/lab-time-delays.md)
- [Blind SQL injection with time delays and information retrieval](labs/lab-time-delays-info-retrieval.md)
- [SQL injection attack, listing the database contents on non-Oracle databases](labs/lab-listing-database-contents-non-oracle.md)
- [SQL injection attack, listing the database contents on Oracle](labs/lab-listing-database-contents-oracle.md)
- [SQL injection attack, querying the database type and version on MySQL and Microsoft](labs/lab-querying-database-version-mysql-microsoft.md)
- [SQL injection attack, querying the database type and version on Oracle](labs/lab-querying-database-version-oracle.md)
- [SQL injection vulnerability allowing login bypass](labs/lab-login-bypass.md)
- [SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](labs/lab-retrieve-hidden-data.md)
- [SQL injection with filter bypass via XML encoding](labs/lab-sql-injection-with-filter-bypass-via-xml-encoding.md)
- [SQL injection UNION attack, determining the number of columns returned by the query](labs/lab-determine-number-of-columns.md)
- [SQL injection UNION attack, finding a column containing text](labs/lab-find-column-containing-text.md)
- [SQL injection UNION attack, retrieving data from other tables](labs/lab-retrieve-data-from-other-tables.md)
- [SQL injection UNION attack, retrieving multiple values in a single column](labs/lab-retrieve-multiple-values-in-single-column.md)

## References

Official topic material and the source for each lab note:

- [SQL injection topic](https://portswigger.net/web-security/sql-injection)
- [Lab: Blind SQL injection with conditional errors](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-errors)
- [Lab: Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses)
- [Lab: Blind SQL injection with out-of-band interaction](https://portswigger.net/web-security/sql-injection/blind/lab-out-of-band)
- [Lab: Blind SQL injection with out-of-band data exfiltration](https://portswigger.net/web-security/sql-injection/blind/lab-out-of-band-data-exfiltration)
- [Lab: Visible error-based SQL injection](https://portswigger.net/web-security/sql-injection/blind/lab-sql-injection-visible-error-based)
- [Lab: Blind SQL injection with time delays](https://portswigger.net/web-security/sql-injection/blind/lab-time-delays)
- [Lab: Blind SQL injection with time delays and information retrieval](https://portswigger.net/web-security/sql-injection/blind/lab-time-delays-info-retrieval)
- [Lab: SQL injection attack, listing the database contents on non-Oracle databases](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-non-oracle)
- [Lab: SQL injection attack, listing the database contents on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-oracle)
- [Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-mysql-microsoft)
- [Lab: SQL injection attack, querying the database type and version on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle)
- [Lab: SQL injection vulnerability allowing login bypass](https://portswigger.net/web-security/sql-injection/lab-login-bypass)
- [Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)
- [Lab: SQL injection with filter bypass via XML encoding](https://portswigger.net/web-security/sql-injection/lab-sql-injection-with-filter-bypass-via-xml-encoding)
- [Lab: SQL injection UNION attack, determining the number of columns returned by the query](https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)
- [Lab: SQL injection UNION attack, finding a column containing text](https://portswigger.net/web-security/sql-injection/union-attacks/lab-find-column-containing-text)
- [Lab: SQL injection UNION attack, retrieving data from other tables](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables)
- [Lab: SQL injection UNION attack, retrieving multiple values in a single column](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-multiple-values-in-single-column)
