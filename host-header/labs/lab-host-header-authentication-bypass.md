# Lab: Host header authentication bypass

**Official lab:** [Host header authentication bypass](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-authentication-bypass)

**Lab idea:** This challenge demonstrates a privilege-checking flaw in which the application makes assumptions about a user's authorization based on the HTTP Host header. It practices recognizing that host routing information must not be treated as proof of a user's identity or privilege.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. Send the GET / request that received a 200 response to Burp Repeater.
2. Browse to /robots.txt and observe that there is an admin panel at /admin .
3. Try and browse to /admin .
4. Send the GET /admin request to Burp Repeater.
5. In Burp Repeater, change the Host header to localhost and send the request.
6. Change the request line to GET /admin/delete?username=carlos and send the request to delete carlos to solve the lab.

## Payloads / key values
- `GET /`
- `/robots.txt`
- `/admin`
- `GET /admin`
- `localhost`
- `GET /admin/delete?username=carlos`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Host header authentication bypass](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-authentication-bypass)
