# Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression)

## Lab idea

Search input is processed as an AngularJS expression even though angle brackets and double quotes are HTML-encoded. It practices recognizing client-side template evaluation as an execution context separate from ordinary HTML parsing.
