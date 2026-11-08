# Lab: Single-endpoint race conditions

**Official lab:** [Lab: Single-endpoint race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-single-endpoint)

**Lab idea:** The account email-change feature has a race condition that can associate an arbitrary email address with an account. This challenge practices recognizing concurrency risks when simultaneous requests update one pending account-change record. [1]

[1]: https://portswigger.net/web-security/race-conditions/lab-race-conditions-single-endpoint "Lab: Single-endpoint race conditions"

## Vulnerability in brief
Race conditions are a web vulnerability class closely related to business-logic flaws. They occur when concurrent requests interact with shared application data without adequate safeguards. If operations overlap while the data is in a temporary, incomplete state, they can collide and cause behavior that would not occur when requests run one at a time. The brief period in which this collision is possible is the **race window**. Limit-overrun cases are a form of time-of-check to time-of-use (TOCTOU) flaw: a check and the later state change are not protected as one operation.

## Solution idea
1. Log in and attempt to change your email to anything@exploit-<YOUR-EXPLOIT-SERVER-ID>.exploit-server.net .
2. Complete the process and confirm that your email address has been updated on your account page.
3. Try submitting two different @exploit-<YOUR-EXPLOIT-SERVER-ID>.exploit-server.net email addresses in succession, then go to the email client.
4. Notice that if you try to use the first confirmation link you received, this is no longer valid.
- …
6. Check your inbox:
7. Go to your account page and notice that you now see a link for accessing the admin panel.
8. Visit the admin panel and delete the user carlos to solve the lab.

## Payloads / key values
- `anything@exploit-<YOUR-EXPLOIT-SERVER-ID>.exploit-server.net`
- `@exploit-<YOUR-EXPLOIT-SERVER-ID>.exploit-server.net`
- `POST /my-account/change-email`
- `test1@exploit-<YOUR-EXPLOIT-SERVER-ID>.exploit-server.net, test2@..., test3@...`
- `email`
- `carlos@ginandjuice.shop`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Single-endpoint race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-single-endpoint)
