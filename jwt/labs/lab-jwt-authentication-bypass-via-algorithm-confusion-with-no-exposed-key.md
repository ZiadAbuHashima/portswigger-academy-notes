# Lab: JWT authentication bypass via algorithm confusion with no exposed key

**Official URL:** https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion-with-no-exposed-key

## Lab idea

This challenge adds a key-discovery dimension to algorithm confusion: the server's RSA public key is not directly exposed. The high-level objective is to reason about deriving or identifying the public verification key from server-issued tokens, then assess the risk of an unsafe algorithm switch. It practices JWT analysis when key material is not published through an obvious endpoint.
