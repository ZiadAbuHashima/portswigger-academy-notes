# Lab: Basic password reset poisoning

**Official lab:** [Basic password reset poisoning](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-basic-password-reset-poisoning)

**Lab idea:** This challenge illustrates how password-reset emails can be affected when the application uses an untrusted Host header to form the reset link. It practices tracing how request-derived domain information flows into account-recovery messages and why those links need a trusted origin.
