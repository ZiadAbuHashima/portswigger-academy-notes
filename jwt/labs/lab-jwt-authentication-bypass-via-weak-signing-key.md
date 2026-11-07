# Lab: JWT authentication bypass via weak signing key

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-weak-signing-key

## Lab idea

This challenge uses a JWT signing secret that is weak enough to be guessed from common values. Its high-level objective is to understand that signature verification alone is insufficient when the signing key lacks strength. It practices recognizing weak-secret risk and its consequences for the integrity of token claims.
