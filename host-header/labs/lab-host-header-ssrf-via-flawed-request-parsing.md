# Lab: SSRF via flawed request parsing

**Official lab:** [SSRF via flawed request parsing](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-ssrf-via-flawed-request-parsing)

**Lab idea:** The challenge demonstrates routing-based SSRF caused by flawed parsing of the request's intended host, despite apparent validation of the Host header. It practices examining how request targets and host information are interpreted across components, with the high-level objective of reaching an internal admin interface.
