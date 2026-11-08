# Lab: Information disclosure in version control history

**Official URL:** https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history

**Lab idea:** The site exposes version-control history that contains sensitive information no longer present in the current application files. The challenge practices recognizing that repository history and change records can preserve secrets even after an apparent cleanup.

## Vulnerability in brief
Information disclosure is a vulnerability class in which a website unintentionally exposes sensitive information. The leaked content can include personal or business data, or technical details about the application and its infrastructure. Unlike a general learning category, this topic covers a distinct security weakness: unintended disclosure through application responses or exposed resources.

## Solution idea
1. Open the lab and browse to /.git to reveal the lab's Git version control data.
2. Download a copy of this entire directory.
3. Explore the downloaded directory using your local Git installation.
4. Look closer at the diff for the changed admin.conf file.
5. Go back to the lab and log in to the administrator account using the leaked password.
6. To solve the lab, open the admin interface and delete carlos .

## Payloads / key values
- `/.git`
- `wget -r https://YOUR-LAB-ID.web-security-academy.net/.git/`
- `"Remove admin password from config"`
- `admin.conf`
- `ADMIN_PASSWORD`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Information disclosure in version control history](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history)
