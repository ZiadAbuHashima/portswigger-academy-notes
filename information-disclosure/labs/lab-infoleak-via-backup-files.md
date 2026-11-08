# Lab: Source code disclosure via backup files

**Official URL:** https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files

**Lab idea:** A backup artifact in a hidden directory exposes application source code that contains a database credential. The challenge practices recognizing accidental backup-file exposure and assessing the sensitivity of information in leaked source.

## Vulnerability in brief
Information disclosure is a vulnerability class in which a website unintentionally exposes sensitive information. The leaked content can include personal or business data, or technical details about the application and its infrastructure. Unlike a general learning category, this topic covers a distinct security weakness: unintended disclosure through application responses or exposed resources.

## Solution idea
1. Browse to /robots.txt and notice that it reveals the existence of a /backup directory.
2. Browse to /backup/ProductTemplate.java.bak to access the source code.
3. In the source code, notice that the connection builder contains the hard-coded password for a Postgres database.
4. Go back to the lab, click "Submit solution", and enter the database password to solve the lab.

## Payloads / key values
- `/robots.txt`
- `/backup`
- `ProductTemplate.java.bak`
- `/backup/ProductTemplate.java.bak`

## Official source
- [PortSwigger Academy: Lab: Source code disclosure via backup files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)
