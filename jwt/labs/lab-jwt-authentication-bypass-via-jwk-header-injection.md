# Lab: JWT authentication bypass via jwk header injection

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jwk-header-injection

## Lab idea

The lab examines a verifier that accepts a public key embedded in the JWT's `jwk` header without establishing that the key is trusted. Its objective is to recognize how token-controlled verification keys can enable authentication bypass. It practices reviewing key provenance and signature-validation policy.
