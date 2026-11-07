# Lab: Basic server-side template injection (code context)

**Official lab:** [Lab: Basic server-side template injection (code context)](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic-code-context)

**Lab idea:** This challenge uses an unsafe Tornado template in a preferred-name feature, where a value is incorporated into template code context. It practices recognizing the difference between data and template syntax in a user-controlled field and using the engine's documentation to assess the risk.