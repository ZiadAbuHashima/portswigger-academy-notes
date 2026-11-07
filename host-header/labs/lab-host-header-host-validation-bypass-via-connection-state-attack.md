# Lab: Host validation bypass via connection state attack

**Official lab:** [Host validation bypass via connection state attack](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-host-validation-bypass-via-connection-state-attack)

**Lab idea:** The challenge explores routing-based SSRF where a front-end appears to validate hosts but makes assumptions about requests on a connection based on the first request. It practices assessing connection-level behavior and how inconsistent assumptions across requests can affect access to internal administrative functionality.
