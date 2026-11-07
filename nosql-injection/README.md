# NoSQL injection (NoSQLi)

NoSQL injection is a vulnerability in which untrusted input interferes with the queries an application sends to a NoSQL database. Unlike SQL databases, NoSQL systems do not share one query language or data model, so the exact syntax and behavior vary by database. PortSwigger's topic focuses on general testing concepts and MongoDB examples. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Main concepts and causes

The topic distinguishes **syntax injection**, where input alters or breaks a database query's syntax, from **operator injection**, where an attacker-controlled query operator changes how records are selected. Some database features can also evaluate JavaScript expressions as part of a query. A common underlying cause is building queries by concatenating user input or accepting structured input without sufficiently controlling its interpretation. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Impact

Depending on the affected query and application functionality, NoSQL injection can bypass authentication or other protections, expose or modify data, cause denial of service, or enable server-side code execution. A change to a query used for updates or deletion can also have destructive consequences. [Official topic](https://portswigger.net/web-security/nosql-injection)

## High-level detection and assessment

In an authorized assessment, identify inputs that reach database-backed features, such as search, filtering, lookups, and login flows. Observe whether carefully controlled, non-destructive changes produce database-related errors or consistent differences in application responses. Comparing the behavior of harmless true and false conditions, and checking whether unexpected structured values are interpreted as query operators, can help determine whether input affects query logic. Testing should be scoped and avoid operations that could alter or delete data. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Prevention

Use parameterized query mechanisms provided by the specific database and avoid constructing query syntax by concatenating untrusted input. Validate and sanitize inputs against an allowlist appropriate to the expected data. For operator injection, allowlist accepted keys and reject unexpected query operators or object structures. Consult the security guidance for the database technology in use. [Official topic](https://portswigger.net/web-security/nosql-injection)

## Lab notes

- [Detecting NoSQL injection](labs/lab-nosql-injection-detection.md)
- [Exploiting NoSQL operator injection to bypass authentication](labs/lab-nosql-injection-bypass-authentication.md)
- [Exploiting NoSQL injection to extract data](labs/lab-nosql-injection-extract-data.md)
- [Exploiting NoSQL operator injection to extract unknown fields](labs/lab-nosql-injection-extract-unknown-fields.md)

## References

- [NoSQL injection](https://portswigger.net/web-security/nosql-injection)
- [Lab: Detecting NoSQL injection](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-detection)
- [Lab: Exploiting NoSQL operator injection to bypass authentication](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-bypass-authentication)
- [Lab: Exploiting NoSQL injection to extract data](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-data)
- [Lab: Exploiting NoSQL operator injection to extract unknown fields](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-extract-unknown-fields)
