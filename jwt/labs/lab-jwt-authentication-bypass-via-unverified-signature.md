# Lab: JWT authentication bypass via unverified signature

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-unverified-signature

## Lab idea

The lab's session mechanism does not verify signatures on received JWTs. Its high-level objective is to see how changing untrusted identity claims can bypass authentication or authorization when integrity checks are absent. It practices identifying the distinction between merely decoding a token and securely verifying it.
