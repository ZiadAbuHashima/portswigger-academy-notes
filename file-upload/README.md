# File upload vulnerabilities

There is no widely used acronym for this topic.

## Overview

A file upload vulnerability occurs when an application does not sufficiently validate or safely handle a file submitted by a user. Weaknesses may involve its name, extension, declared or actual type, contents, or size. The risk also depends on what happens after upload: where the file is stored, whether it can be requested, and whether the server treats it as static data or executable code. [1]

Common causes include trusting user-controlled metadata such as a filename or multipart `Content-Type`; relying on incomplete extension blacklists; inconsistent parsing or validation across components; and storing files in locations or configurations where they can overwrite other files, be reached unexpectedly, or be executed. Upload processing that makes a file accessible before validation finishes can also create a timing weakness. [1]

## Main concepts

- **Validation is multi-dimensional:** extension, name, contents, type, and size need appropriate checks; a single client-supplied label is not proof of a file’s true type. [1]
- **Storage and serving matter:** the destination path, filename handling, and web-server configuration determine whether a stored file is exposed, interpreted, or executed. Static-file handling may also reveal content if executable files are served as plain text. [1]
- **Controls must be consistent:** differing parsing rules between the application, storage layer, and web server can undermine checks. Validation should complete before a file is placed where it is permanently accessible. [1]

## Potential impact

At the severe end, an uploaded server-side script may execute and enable remote code execution, with possible access to sensitive data, file modification, or further attacks from the server. Other consequences include overwriting important files, placing files in unintended locations, disclosure of uploaded source or content, and denial of service if uploads consume excessive storage. The specific impact depends on the failed validation and the server’s handling of the file. [1]

## High-level assessment context

For authorized testing, review upload features and their expected file types, then assess whether server-side controls validate the submitted file rather than relying on editable request metadata. Consider how names and extensions are parsed, whether the stored file’s location and retrieval behavior are safe, and whether server configuration could interpret or expose uploaded content. Also assess size limits and whether validation finishes before a file becomes accessible. Keep testing within the approved scope and avoid accessing or changing other users’ data. [1]

## Prevention

Use a whitelist of permitted extensions instead of a blacklist, and validate files with trusted server-side checks appropriate to the expected formats. Reject unsafe path or traversal content in filenames and assign server-generated names to prevent collisions. Do not place files in permanent storage until validation is complete; ensure uploaded content cannot be executed unintentionally and is served with safe handling. Prefer established upload-processing frameworks over ad hoc validation. [1]

## Lab notes

- [Lab: Remote code execution via polyglot web shell upload](labs/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload.md)
- [Lab: Remote code execution via web shell upload](labs/lab-file-upload-remote-code-execution-via-web-shell-upload.md)
- [Lab: Web shell upload via Content-Type restriction bypass](labs/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass.md)
- [Lab: Web shell upload via extension blacklist bypass](labs/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass.md)
- [Lab: Web shell upload via obfuscated file extension](labs/lab-file-upload-web-shell-upload-via-obfuscated-file-extension.md)
- [Lab: Web shell upload via path traversal](labs/lab-file-upload-web-shell-upload-via-path-traversal.md)
- [Lab: Web shell upload via race condition](labs/lab-file-upload-web-shell-upload-via-race-condition.md)

## References

[1]: https://portswigger.net/web-security/file-upload "PortSwigger Web Security Academy: File upload vulnerabilities"
[2]: https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload "PortSwigger Web Security Academy: Lab: Remote code execution via polyglot web shell upload"
[3]: https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload "PortSwigger Web Security Academy: Lab: Remote code execution via web shell upload"
[4]: https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass "PortSwigger Web Security Academy: Lab: Web shell upload via Content-Type restriction bypass"
[5]: https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass "PortSwigger Web Security Academy: Lab: Web shell upload via extension blacklist bypass"
[6]: https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension "PortSwigger Web Security Academy: Lab: Web shell upload via obfuscated file extension"
[7]: https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal "PortSwigger Web Security Academy: Lab: Web shell upload via path traversal"
[8]: https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition "PortSwigger Web Security Academy: Lab: Web shell upload via race condition"
