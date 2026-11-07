# Lab: JWT authentication bypass via flawed signature verification

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-flawed-signature-verification

## Lab idea

The lab focuses on a JWT-based session mechanism that accepts unsigned tokens because of flawed signature handling. Its objective is to recognize how that verification failure can let token claims influence access control. It practices examining JWT headers, claims, and the integrity assumptions made by an application.
