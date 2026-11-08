# Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression)

## Lab idea

Search input is processed as an AngularJS expression even though angle brackets and double quotes are HTML-encoded. It practices recognizing client-side template evaluation as an execution context separate from ordinary HTML parsing.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Enter a random alphanumeric string into the search box.
2. View the page source and observe that your random string is enclosed in an ng-app directive.
3. Enter the following AngularJS expression in the search box: {{$on.constructor('alert(1)')()}}
4. Click search .

## Payloads / key values
- `ng-app`
- `{{$on.constructor('alert(1)')()}}`

## Official source
- [PortSwigger Academy: Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression)
