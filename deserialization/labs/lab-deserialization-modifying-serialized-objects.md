# Lab: Modifying serialized objects

**Official lab:** [https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects)

## Lab idea

This challenge focuses on a serialized PHP session object whose fields influence administrative privileges. It practices assessing whether client-controlled object state is trusted for authorization.

## Vulnerability in brief
Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

## Solution idea
1. Log in using your own credentials.
2. Use Burp's Inspector panel to study the request in its decoded form.
3. In Burp Repeater, use the Inspector to examine the cookie again and change the value of the admin attribute to b:1 .
4. Send the request.
5. Change the path of your request to /admin and resend it.
6. Change the path of your request to /admin/delete?username=carlos and send the request to solve the lab.

## Payloads / key values
- `GET /my-account`
- `admin`
- `b:0`
- `false`
- `b:1`
- `/admin`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Modifying serialized objects](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects)
