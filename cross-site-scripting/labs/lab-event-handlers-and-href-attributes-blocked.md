# Lab: Reflected XSS with event handlers and href attributes blocked

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked)

## Lab idea

The application allows some markup but blocks event handlers and anchor href attributes. It practices evaluating the limits of tag and attribute allowlists and recognizing that partial filtering can leave alternate unsafe contexts.
