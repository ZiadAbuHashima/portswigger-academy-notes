# Lab: Arbitrary object injection in PHP

**Official lab:** [https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-arbitrary-object-injection-in-php](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-arbitrary-object-injection-in-php)

## Lab idea

This challenge explores how a serialized PHP session can be altered to instantiate an unexpected object and invoke behavior associated with that object. It practices recognizing object injection and tracing how application code handles deserialized state.

## Vulnerability in brief
Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

## Solution idea
1. Log in to your own account and notice the session cookie contains a serialized PHP object.
2. From the site map, notice that the website references the file /libs/CustomTemplate.php .
3. In Burp Repeater, notice that you can read the source code by appending a tilde ( ~ ) to the filename in the request line.
4. In the source code, notice the CustomTemplate class contains the __destruct() magic method.
- …
6. Send a request containing the session cookie to Burp Repeater.
7. In Burp Repeater, replace the session cookie with the modified one in your clipboard.
8. Send the request.

## Payloads / key values
- `/libs/CustomTemplate.php`
- `~`
- `CustomTemplate`
- `__destruct()`
- `unlink()`
- `lock_file_path`
- `/home/carlos/morale.txt`
- `O:14:"CustomTemplate":1:{s:14:"lock_file_path";s:23:"/home/carlos/morale.txt";}`

## Official source
- [PortSwigger Academy: Lab: Arbitrary object injection in PHP](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-arbitrary-object-injection-in-php)
