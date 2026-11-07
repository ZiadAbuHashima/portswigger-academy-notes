# Lab: Web cache poisoning via an unkeyed query string

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-query

**Lab idea:** This lab explores a cache that does not include the query string in its cache key, even though the application reflects query data in the response. It practices assessing cache-key composition and the consequences of request components that affect output but not cache identity.
