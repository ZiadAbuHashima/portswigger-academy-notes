# Lab: User ID controlled by request parameter, with unpredictable user IDs

**Official lab:** [https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids)

## Lab idea

The account page uses GUIDs rather than readily predictable user identifiers, but the underlying issue is still horizontal access control. The challenge practices distinguishing identifier unpredictability from authorization.
