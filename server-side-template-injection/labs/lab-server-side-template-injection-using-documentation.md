# Lab: Server-side template injection using documentation

**Official lab:** [Lab: Server-side template injection using documentation](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-using-documentation)

**Lab idea:** This challenge asks learners to identify a template engine and use its documentation to understand how unsafe template evaluation can reach server-side capabilities. It practices methodical engine identification and security-focused documentation research.

## Vulnerability in brief
Server-side template injection (SSTI) is a vulnerability in which untrusted input is interpreted as template-language syntax and evaluated by a server-side template engine. Template engines normally combine fixed templates with changing data to render pages. The vulnerability arises when applications construct template source by concatenating user input into it instead of supplying that input strictly as data. This may happen accidentally through unsafe template design or intentionally when an application permits users to submit or modify templates.

## Solution idea
1. Log in and edit one of the product description templates.
2. Study the Freemarker documentation and find that appendix contains an FAQs section with the question "Can I allow users to upload templates and what are the security implications?".
3. Go to the "Built-in reference" section of the documentation and find the entry for new() .
4. Load the JavaDoc for the TemplateModel class, and review the list of "All Known Implementing Classes".
5. Observe that there is a class called Execute , which can be used to execute arbitrary shell commands
6. Either attempt to construct your own exploit, or find @albinowax's exploit on our research page and adapt it as follows: <#assign ex="freemarker.template.utility.Execute"?new()> ${ ex("rm…
7. Remove the invalid syntax that you entered earlier, and insert your new payload into the template.
8. Save the template and view the product page to solve the lab.

## Payloads / key values
- `${someExpression}`
- `${foobar}`
- `new()`
- `TemplateModel`
- `Execute`
- `<#assign ex="freemarker.template.utility.Execute"?new()> ${ ex("rm /home/carlos/morale.txt") }`

## Official source
- [PortSwigger Academy: Lab: Server-side template injection using documentation](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-using-documentation)
