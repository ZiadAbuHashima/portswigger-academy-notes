# Clickjacking (UI redressing)

Clickjacking, also called **UI redressing** (user-interface redressing), is an interface-based attack in which a person is tricked into activating a control on a hidden website while believing they are clicking something else on a decoy page. A common mechanism is to place a target page inside an iframe and layer the decoy content over it. Layout, stacking order, and transparency can make an actionable target control line up with the apparent decoy control. The click is still a real user action within the target site's authenticated session. [1]

## Main concepts

Clickjacking is distinct from cross-site request forgery (CSRF): clickjacking relies on misleading the user into clicking, whereas CSRF attempts to cause a request without that user action. A CSRF token alone does not prevent clickjacking when the legitimate site loads in a frame and the browser submits its normal authenticated request. Attacks may also prefill form fields through URL parameters, combine the click with another issue such as DOM-based cross-site scripting (XSS), or require a sequence of clicks. Client-side frame-busting scripts can be unreliable and may be bypassed, so they should not be the primary defense. [1]

## Impact

If an attacker can frame a sensitive page and induce a click, the victim may unintentionally change account details, delete an account, submit a transaction, or perform another action available to their signed-in session. Clickjacking can also serve as a delivery mechanism for a separate flaw, such as click-triggered DOM XSS. [1]

## Authorized testing context

For authorized assessments, identify sensitive pages and actions that could be abused if framed. Review the site's framing policy, including `Content-Security-Policy` `frame-ancestors` and `X-Frame-Options`, and check in a controlled browser whether the relevant page can be embedded and its actions remain available. Evaluate the user's visible expectation against the underlying action, including any form prepopulation, confirmation steps, or browser-specific behavior. Keep testing non-destructive unless the engagement explicitly authorizes state-changing tests. [1]

## Prevention

Set a restrictive server-delivered framing policy. Content Security Policy's `frame-ancestors 'none'` disallows framing; `frame-ancestors 'self'` limits it to the same origin, while an explicit trusted-site allowlist can be used where framing is required. `X-Frame-Options: DENY` or `SAMEORIGIN` can provide an additional compatibility layer, though support for some directives varies by browser. Define and test policies carefully. Do not rely on CSRF tokens or JavaScript frame-busting alone as clickjacking defenses. [1]

## Lab notes

- [Basic clickjacking with CSRF token protection](labs/lab-basic-csrf-protected.md)
- [Exploiting clickjacking vulnerability to trigger DOM-based XSS](labs/lab-exploiting-to-trigger-dom-based-xss.md)
- [Clickjacking with a frame buster script](labs/lab-frame-buster-script.md)
- [Multistep clickjacking](labs/lab-multistep.md)
- [Clickjacking with form input data prefilled from a URL parameter](labs/lab-prefilled-form-input.md)

## References

[1]: https://portswigger.net/web-security/clickjacking "PortSwigger Web Security Academy: Clickjacking"
[2]: https://portswigger.net/web-security/clickjacking/lab-basic-csrf-protected "PortSwigger Web Security Academy lab: Basic clickjacking with CSRF token protection"
[3]: https://portswigger.net/web-security/clickjacking/lab-exploiting-to-trigger-dom-based-xss "PortSwigger Web Security Academy lab: Exploiting clickjacking vulnerability to trigger DOM-based XSS"
[4]: https://portswigger.net/web-security/clickjacking/lab-frame-buster-script "PortSwigger Web Security Academy lab: Clickjacking with a frame buster script"
[5]: https://portswigger.net/web-security/clickjacking/lab-multistep "PortSwigger Web Security Academy lab: Multistep clickjacking"
[6]: https://portswigger.net/web-security/clickjacking/lab-prefilled-form-input "PortSwigger Web Security Academy lab: Clickjacking with form input data prefilled from a URL parameter"
