# Lab: Server-side template injection with information disclosure via user-supplied objects

**Official lab:** [Lab: Server-side template injection with information disclosure via user-supplied objects](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-with-information-disclosure-via-user-supplied-objects)

**Lab idea:** The challenge demonstrates how an object passed into a template can expose sensitive framework information. It practices assessing the data and capabilities available in a template context and recognizing how template injection can lead to information disclosure.

## Vulnerability in brief
Server-side template injection (SSTI) is a vulnerability in which untrusted input is interpreted as template-language syntax and evaluated by a server-side template engine. Template engines normally combine fixed templates with changing data to render pages. The vulnerability arises when applications construct template source by concatenating user input into it instead of supplying that input strictly as data. This may happen accidentally through unsafe template design or intentionally when an application permits users to submit or modify templates.

## Solution idea
1. Log in and edit one of the product description templates.
2. Change one of the template expressions to something invalid, such as a fuzz string ${{<%[%'"}}%\ , and save the template.
3. Study the Django documentation and notice that the built-in template tag debug can be called to display debugging information.
4. In the template, remove your invalid syntax and enter the following statement to invoke the debug built-in: {% debug %}
- …
6. In the template, remove the {% debug %} statement and enter the expression {{settings.SECRET_KEY}}
7. Save the template to output the framework's secret key.
8. Click the "Submit solution" button and submit the secret key to solve the lab.

## Payloads / key values
- `${{<%[%'"}}%\`
- `debug`
- `{% debug %}`
- `settings`
- `SECRET_KEY`
- `{{settings.SECRET_KEY}}`

## Official source
- [PortSwigger Academy: Lab: Server-side template injection with information disclosure via user-supplied objects](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-with-information-disclosure-via-user-supplied-objects)
