# Lab: JWT authentication bypass via algorithm confusion

**Official URL:** https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion

## Lab idea

The challenge explores algorithm confusion in a JWT verifier that uses an RSA key pair. Its high-level objective is to understand how inconsistent algorithm handling can undermine trust in token signatures and enable an authorization bypass. It practices recognizing the boundary between asymmetric and symmetric key use in JWT verification.
