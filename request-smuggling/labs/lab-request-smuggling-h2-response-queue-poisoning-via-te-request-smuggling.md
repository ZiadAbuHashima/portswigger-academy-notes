# Lab: Response queue poisoning via H2.TE request smuggling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling](https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling)

## Lab idea

The lab focuses on response-queue poisoning arising from an HTTP/2 downgrade and ambiguous transfer-encoding handling. It practices evaluating how mismatched request parsing can shift responses between requests and affect privileged endpoints.
