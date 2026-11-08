# Lab: Information disclosure on debug page

**Official URL:** https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page

**Lab idea:** An accessible debug page reveals sensitive application information, including an environment variable. The challenge practices noticing references to diagnostic functionality and understanding why debug output should not be exposed in production.

## Vulnerability in brief
Information disclosure is a vulnerability class in which a website unintentionally exposes sensitive information. The leaked content can include personal or business data, or technical details about the application and its infrastructure. Unlike a general learning category, this topic covers a distinct security weakness: unintended disclosure through application responses or exposed resources.

## Solution idea
1. With Burp running, browse to the home page.
2. Go to the "Target" > "Site Map" tab.
3. In the site map, right-click on the entry for /cgi-bin/phpinfo.php and select "Send to Repeater".
4. In Burp Repeater, send the request to retrieve the file.
5. Go back to the lab, click "Submit solution", and enter the SECRET_KEY to solve the lab.

## Payloads / key values
- `/cgi-bin/phpinfo.php`
- `SECRET_KEY`

## Official source
- [PortSwigger Academy: Lab: Information disclosure on debug page](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page)
