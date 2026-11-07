# Lab: JWT authentication bypass via jku header injection

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jku-header-injection

## Lab idea

This challenge concerns a verifier that follows a `jku` header URL without restricting it to a trusted domain. Its high-level objective is to understand how untrusted remote key selection can weaken JWT signature validation. It practices assessing trust boundaries around externally fetched JWK Sets.
