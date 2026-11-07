# Lab: Basic clickjacking with CSRF token protection

**Official PortSwigger URL:** https://portswigger.net/web-security/clickjacking/lab-basic-csrf-protected

## Lab idea

This challenge centers on an account-deletion control that uses a CSRF token. Its concept is to show that a valid token does not by itself prevent a user from being misled into activating an action on a framed page. It practices recognizing the difference between CSRF and clickjacking and assessing how interface layering can affect an authorized, signed-in user's actions.
