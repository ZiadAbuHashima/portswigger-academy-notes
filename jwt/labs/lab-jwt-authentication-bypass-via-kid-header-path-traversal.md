# Lab: JWT authentication bypass via kid header path traversal

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-kid-header-path-traversal

## Lab idea

This challenge uses a `kid` header value to select a verification key from the server's filesystem. The high-level objective is to identify the security risk when a key identifier is treated as an unconstrained path. It practices examining how JWT metadata reaches server-side key lookup logic.
