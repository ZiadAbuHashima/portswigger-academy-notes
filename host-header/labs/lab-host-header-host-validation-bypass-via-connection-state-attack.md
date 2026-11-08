# Lab: Host validation bypass via connection state attack

**Official lab:** [Host validation bypass via connection state attack](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-host-validation-bypass-via-connection-state-attack)

**Lab idea:** The challenge explores routing-based SSRF where a front-end appears to validate hosts but makes assumptions about requests on a connection based on the first request. It practices assessing connection-level behavior and how inconsistent assumptions across requests can affect access to internal administrative functionality.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. Send the GET / request to Burp Repeater.
2. Make the following adjustments:
3. Send the request.
4. Duplicate the tab, then add both tabs to a new group.
- …
6. Study the response and observe that the admin panel contains an HTML form for deleting a given user.
7. On the second tab in your group, use these details to replicate the request that would be issued when submitting the form.
8. Send the requests in sequence down a single connection to solve the lab.

## Payloads / key values
- `GET /`
- `/admin`
- `Host`
- `192.168.0.1`
- `/`
- `YOUR-LAB-ID.h1-web-security-academy.net`
- `Connection`
- `keep-alive`
- `/admin/delete`
- `username`
- `csrf`
- `POST /admin/delete HTTP/1.1 Host: 192.168.0.1 Cookie: _lab=YOUR-LAB-COOKIE; session=YOUR-SESSION-COOKIE Content-Type: x-www-form-urlencoded Content-Length: CORRECT csrf=YOUR-CSRF-TOKEN&username=carlos`

## Official source
- [PortSwigger Academy: Lab: Host validation bypass via connection state attack](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-host-validation-bypass-via-connection-state-attack)
