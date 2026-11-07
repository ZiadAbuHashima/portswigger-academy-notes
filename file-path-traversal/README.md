# Path traversal (directory traversal)

Path traversal is a vulnerability class that lets an attacker manipulate a file path used by an application to access files outside the intended directory. It is also known as directory traversal. It commonly occurs when an application incorporates user-controlled values, such as a filename in an image or download request, into a filesystem path without safely constraining the resolved destination. Relative path components can move up the directory hierarchy; path handling and validation can also be undermined when checks are incomplete or performed before later decoding or path interpretation. [1]

## Main concepts

An application may take a supplied filename, append it to a storage directory, then read the resulting path. If the resolved path is not confined to that directory, the application may access a different file elsewhere on the server. Operating systems use different path conventions, and applications may have checks for traversal sequences, required path prefixes, or file extensions. Such checks are not reliable substitutes for validating the final resolved path. [1]

## Impact

Unauthorized file reads may expose application code and data, back-end credentials, or sensitive operating-system files. In some cases, arbitrary file writes can let an attacker change application data or behavior and may ultimately enable server takeover. The actual impact depends on which paths and filesystem operations the application can reach. [1]

## High-level detection and assessment

During authorized testing, review features that accept file or path-like input, such as image display, downloads, or other file-handling functions. Assess whether that input influences a filesystem operation and whether the resulting path remains within the intended directory after the application’s validation, decoding, and path resolution. Treat unexpected file content, access beyond the intended storage area, or inconsistent results across path normalization as signals for careful investigation. Use only approved test targets and non-sensitive test data where possible. [1]

## Prevention

Prefer designs that do not pass user-supplied paths to filesystem APIs. Where file selection is needed, accept a constrained identifier mapped server-side to an allowed file, or validate against a strict allowlist. If user input must be used in a path, validate it before processing, append it to the intended base directory, canonicalize the result with the platform’s filesystem API, and verify that the canonical path is still inside the permitted base directory. [1]

## Lab notes

- [File path traversal, traversal sequences blocked with absolute path bypass](labs/lab-absolute-path-bypass.md)
- [File path traversal, traversal sequences stripped non-recursively](labs/lab-sequences-stripped-non-recursively.md)
- [File path traversal, simple case](labs/lab-simple.md)
- [File path traversal, traversal sequences stripped with superfluous URL-decode](labs/lab-superfluous-url-decode.md)
- [File path traversal, validation of file extension with null byte bypass](labs/lab-validate-file-extension-null-byte-bypass.md)
- [File path traversal, validation of start of path](labs/lab-validate-start-of-path.md)

## References

[1]: https://portswigger.net/web-security/file-path-traversal "PortSwigger Web Security Academy: Path traversal"
[2]: https://portswigger.net/web-security/file-path-traversal/lab-absolute-path-bypass "Lab: File path traversal, traversal sequences blocked with absolute path bypass"
[3]: https://portswigger.net/web-security/file-path-traversal/lab-sequences-stripped-non-recursively "Lab: File path traversal, traversal sequences stripped non-recursively"
[4]: https://portswigger.net/web-security/file-path-traversal/lab-simple "Lab: File path traversal, simple case"
[5]: https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode "Lab: File path traversal, traversal sequences stripped with superfluous URL-decode"
[6]: https://portswigger.net/web-security/file-path-traversal/lab-validate-file-extension-null-byte-bypass "Lab: File path traversal, validation of file extension with null byte bypass"
[7]: https://portswigger.net/web-security/file-path-traversal/lab-validate-start-of-path "Lab: File path traversal, validation of start of path"
