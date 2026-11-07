# Lab: SSRF via OpenID dynamic client registration

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/openid/lab-oauth-ssrf-via-openid-dynamic-client-registration

**Lab idea:** The OAuth service supports dynamic client registration and uses client-specific metadata in an unsafe way, potentially causing server-side requests to unintended destinations. The challenge practices identifying SSRF risk in OpenID Connect registration features and their handling of supplied metadata.
