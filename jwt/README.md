# JWT attacks (JSON Web Token, JWT)

JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Main concepts

A JWT attack occurs when a recipient mishandles a token and accepts untrusted claims or an invalid signature. Common failures include not verifying a signature, accepting unsigned tokens, or allowing the token's `alg` header to steer verification in an unsafe way. Algorithm confusion can arise when an implementation mistakenly treats a public verification key as a symmetric signing secret. Weak or default shared secrets can also let an attacker produce signatures that the server accepts.

Other JWT header fields can affect key selection. `jwk` can embed a key, `jku` can reference a remote JWK Set, and `kid` can identify a key, sometimes by referencing a database entry or file. Trusting a key supplied by the token, fetching keys from an untrusted location, or using `kid` unsafely can undermine otherwise sound signature checks. The official topic also notes that unsafe `kid` handling can expose path traversal or SQL injection risks.

## Impact

A forged or improperly accepted token may let an attacker alter identity or authorization claims, impersonate another user, or gain elevated privileges. Because JWTs often underpin authentication and access control, successful attacks can compromise accounts and potentially much of an affected application.

## High-level detection and assessment

During authorized testing, identify whether JWTs are used in cookies or authorization headers. Decode tokens to understand their header and claims, then assess whether security-relevant values are trusted only after robust verification. Review the accepted algorithm and key-selection behavior, including whether embedded or remotely referenced keys are constrained and whether `kid` is handled safely. Carefully compare application behavior for controlled changes to a token and its signature, without affecting users or data outside the authorized scope. An acceptance difference can indicate a verification or key-trust weakness; confirm findings with the application's intended authorization behavior.

## Prevention

Use an up-to-date JWT library and ensure its verification API and security implications are understood. Explicitly allow only intended algorithms, robustly verify every received token's signature, and reject unsigned or otherwise unexpected tokens. Use strong, protected signing secrets or private keys. Do not accept arbitrary verification keys from token-controlled `jwk` values; restrict `jku` lookups to a strict trusted-host allowlist. Treat `kid` as untrusted input and resolve it through safe, constrained key lookup rather than unsafe file paths or SQL construction.

## Lab notes

- [JWT authentication bypass via algorithm confusion](labs/lab-jwt-authentication-bypass-via-algorithm-confusion.md)
- [JWT authentication bypass via algorithm confusion with no exposed key](labs/lab-jwt-authentication-bypass-via-algorithm-confusion-with-no-exposed-key.md)
- [JWT authentication bypass via flawed signature verification](labs/lab-jwt-authentication-bypass-via-flawed-signature-verification.md)
- [JWT authentication bypass via jku header injection](labs/lab-jwt-authentication-bypass-via-jku-header-injection.md)
- [JWT authentication bypass via jwk header injection](labs/lab-jwt-authentication-bypass-via-jwk-header-injection.md)
- [JWT authentication bypass via kid header path traversal](labs/lab-jwt-authentication-bypass-via-kid-header-path-traversal.md)
- [JWT authentication bypass via unverified signature](labs/lab-jwt-authentication-bypass-via-unverified-signature.md)
- [JWT authentication bypass via weak signing key](labs/lab-jwt-authentication-bypass-via-weak-signing-key.md)

## References

- [Official topic: JWT attacks](https://portswigger.net/web-security/jwt)
- [Lab: JWT authentication bypass via algorithm confusion](https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion)
- [Lab: JWT authentication bypass via algorithm confusion with no exposed key](https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion-with-no-exposed-key)
- [Lab: JWT authentication bypass via flawed signature verification](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-flawed-signature-verification)
- [Lab: JWT authentication bypass via jku header injection](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jku-header-injection)
- [Lab: JWT authentication bypass via jwk header injection](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jwk-header-injection)
- [Lab: JWT authentication bypass via kid header path traversal](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-kid-header-path-traversal)
- [Lab: JWT authentication bypass via unverified signature](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-unverified-signature)
- [Lab: JWT authentication bypass via weak signing key](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-weak-signing-key)
