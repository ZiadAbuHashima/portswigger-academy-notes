# Lab: SameSite Strict bypass via sibling domain

**Official lab:** [Lab: SameSite Strict bypass via sibling domain](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-sibling-domain)

## Lab idea

This related browser-trust challenge centers on cross-site WebSocket hijacking (CSWSH), a live-chat feature, and a vulnerable sibling domain under SameSite=Strict cookies. It practices considering the wider same-site attack surface rather than treating the primary host in isolation.
