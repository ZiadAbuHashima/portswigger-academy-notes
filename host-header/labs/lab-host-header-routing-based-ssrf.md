# Lab: Routing-based SSRF

**Official lab:** [Routing-based SSRF](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-routing-based-ssrf)

**Lab idea:** This challenge focuses on an application whose Host-header handling can cause server-side requests to reach an internal administrative interface. It practices identifying risky request routing and understanding the boundary between public-facing services and internal infrastructure.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. Send the GET / request that received a 200 response to Burp Repeater.
2. In Burp Repeater, select the Host header value, right-click and select Insert Collaborator payload to replace it with a Collaborator domain name.
3. Go to the Collaborator tab and click Poll now .
4. Send the GET / request to Burp Intruder.
- …
6. Copy the session cookie from the Set-Cookie header in the displayed response and add it to your request.
7. Right-click on your request and select Change request method .
8. Send the request to delete carlos and solve the lab.

## Payloads / key values
- `GET /`
- `200`
- `Host: 192.168.0.§0§`
- `From: 0 To: 255 Step: 1`
- `302`
- `/admin`
- `GET /admin`
- `POST`
- `/admin/delete`
- `username`
- `carlos`
- `GET /admin/delete?csrf=QCT5OmPeAAPnyTKyETt29LszLL7CbPop&username=carlos`
- `Set-Cookie`

## Official source
- [PortSwigger Academy: Lab: Routing-based SSRF](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-routing-based-ssrf)
