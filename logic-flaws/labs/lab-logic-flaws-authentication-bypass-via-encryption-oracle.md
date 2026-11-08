# Lab: Authentication bypass via encryption oracle

**Official URL:** https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-encryption-oracle

**Lab idea:** This challenge centers on an encryption oracle exposed through application behavior. It practices recognizing how related encryption and decryption features can undermine authentication when their outputs are trusted as identity data.

## Vulnerability in brief
Business logic vulnerabilities—also called application logic vulnerabilities or logic flaws—are design or implementation defects that make an application behave in ways its rules did not intend. They arise when a system's assumptions about user behavior, application state, or the behavior of another component are wrong, and the server does not safely handle an unusual but valid interaction. Unlike a single technical bug pattern, logic flaws are often specific to an application's workflows and require understanding what those workflows are supposed to do.

## Solution idea
1. Log in with the "Stay logged in" option enabled and post a comment.
2. Notice that when you try and submit a comment using an invalid email address, the response sets an encrypted notification cookie before redirecting you to the blog post.
3. Notice that the error message reflects your input from the email parameter in cleartext: Invalid email address: your-invalid-email Deduce that this must be decrypted from the notification…
4. In Repeater, observe that you can use the email parameter of the POST request to encrypt arbitrary data and reflect the corresponding ciphertext in the Set-Cookie header.
- …
6. Send the new ciphertext to Decoder, then URL and Base64-decode it.
7. From the proxy history, send the GET / request to Burp Repeater.
8. Using Burp Repeater, browse to /admin and notice the option for deleting users.

## Payloads / key values
- `stay-logged-in`
- `notification`
- `email`
- `Invalid email address: your-invalid-email`
- `POST /post/comment`
- `GET /post?postId=x`
- `POST`
- `Set-Cookie`
- `GET`
- `encrypt`
- `decrypt`
- `wiener:1598530205184`
- `username:timestamp`
- `administrator:your-timestamp`
- `Invalid email address:`
- `xxxxxxxxxadministrator:your-timestamp`
- `GET /`
- `session`
- `/admin`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Authentication bypass via encryption oracle](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-encryption-oracle)
