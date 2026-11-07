# Lab: Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped)

## Lab idea

The reflected input is inserted into a JavaScript template literal, with several characters encoded or escaped. It practices identifying template-literal interpolation as a distinct JavaScript context and checking whether escaping matches that context.
