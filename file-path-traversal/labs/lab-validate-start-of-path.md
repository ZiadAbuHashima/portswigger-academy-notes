# Lab: File path traversal, validation of start of path

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-validate-start-of-path

**Lab idea:** The application accepts a full path in a request parameter and checks that it starts with an expected folder. The challenge practices distinguishing a textual prefix check from verifying that the final resolved file remains inside the permitted directory.
