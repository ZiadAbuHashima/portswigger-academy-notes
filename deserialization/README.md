# Insecure deserialization (ID)

## Overview

Serialization converts an object and its state into a format that can be stored or transmitted; deserialization rebuilds that data as a usable object. Insecure deserialization occurs when an application deserializes data that an attacker can control. Because object fields and, in some implementations, object types are restored, crafted data may influence application logic before or during normal use of the object. This is a vulnerability class, not a general learning or testing category.

The risk is not limited to readable text formats. Binary serialized data can also be manipulated, and related features may be described as marshalling or pickling in some languages. An unexpected object can trigger behavior through language-specific lifecycle methods or through chains of methods and classes already present in application dependencies.

## Main concepts

- **Object state and type:** Serialized representations may preserve fields, values, and type information. Trusting those values as authentic can undermine application assumptions.
- **Object injection:** Some deserializers can instantiate an unexpected class available to the application, rather than only restoring the intended type.
- **Gadget chains:** Existing methods in application code or dependencies can interact in unexpected ways when given attacker-controlled objects. Chaining these behaviors may route data to sensitive operations.
- **Indirect entry points:** The risky deserialization may occur in session handling or another feature that processes serialized content, including file-related flows; it need not appear as an obvious direct user-facing operation.

## Potential impact

Depending on the runtime, reachable classes, and application behavior, exploitation may enable remote code execution. Other potential outcomes include privilege escalation, arbitrary file access, and denial of service. The security impact can therefore exceed the apparent purpose of the input field or cookie involved.

## High-level detection and assessment

During authorized testing, look for client-controlled or otherwise untrusted serialized data in cookies, session tokens, request parameters, uploaded files, and data passed between application components. Encodings such as Base64 or signatures do not by themselves make content trustworthy. Review code and dependencies for deserialization functions, object lifecycle hooks, and flows from restored fields into sensitive operations. In a controlled assessment, compare behavior when serialized state is changed and check whether the application accepts unexpected object state or types. Avoid intrusive testing outside explicit authorization.

## Prevention

Avoid deserializing untrusted input wherever possible. Prefer narrow, class-specific data formats and explicit schemas that expose only the required fields; avoid generic object deserialization. If untrusted serialized data must be accepted, verify its integrity and authenticity before deserialization, for example with a correctly managed digital signature. Validation performed only after object construction may be too late. Keep dependencies maintained, but do not treat removal of known gadget chains as a sufficient defense: the underlying problem is deserializing attacker-controlled data.

## Lab notes

- [Lab: Arbitrary object injection in PHP](labs/lab-deserialization-arbitrary-object-injection-in-php.md)
- [Lab: Developing a custom gadget chain for Java deserialization](labs/lab-deserialization-developing-a-custom-gadget-chain-for-java-deserialization.md)
- [Lab: Developing a custom gadget chain for PHP deserialization](labs/lab-deserialization-developing-a-custom-gadget-chain-for-php-deserialization.md)
- [Lab: Exploiting Java deserialization with Apache Commons](labs/lab-deserialization-exploiting-java-deserialization-with-apache-commons.md)
- [Lab: Exploiting PHP deserialization with a pre-built gadget chain](labs/lab-deserialization-exploiting-php-deserialization-with-a-pre-built-gadget-chain.md)
- [Lab: Exploiting Ruby deserialization using a documented gadget chain](labs/lab-deserialization-exploiting-ruby-deserialization-using-a-documented-gadget-chain.md)
- [Lab: Modifying serialized data types](labs/lab-deserialization-modifying-serialized-data-types.md)
- [Lab: Modifying serialized objects](labs/lab-deserialization-modifying-serialized-objects.md)
- [Lab: Using application functionality to exploit insecure deserialization](labs/lab-deserialization-using-application-functionality-to-exploit-insecure-deserialization.md)
- [Lab: Using PHAR deserialization to deploy a custom gadget chain](labs/lab-deserialization-using-phar-deserialization-to-deploy-a-custom-gadget-chain.md)

## References

- [Official topic: Insecure deserialization](https://portswigger.net/web-security/deserialization)
- [Official source: Lab: Arbitrary object injection in PHP](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-arbitrary-object-injection-in-php)
- [Official source: Lab: Developing a custom gadget chain for Java deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-java-deserialization)
- [Official source: Lab: Developing a custom gadget chain for PHP deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-developing-a-custom-gadget-chain-for-php-deserialization)
- [Official source: Lab: Exploiting Java deserialization with Apache Commons](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-exploiting-java-deserialization-with-apache-commons)
- [Official source: Lab: Exploiting PHP deserialization with a pre-built gadget chain](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-exploiting-php-deserialization-with-a-pre-built-gadget-chain)
- [Official source: Lab: Exploiting Ruby deserialization using a documented gadget chain](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-exploiting-ruby-deserialization-using-a-documented-gadget-chain)
- [Official source: Lab: Modifying serialized data types](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-data-types)
- [Official source: Lab: Modifying serialized objects](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects)
- [Official source: Lab: Using application functionality to exploit insecure deserialization](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-using-application-functionality-to-exploit-insecure-deserialization)
- [Official source: Lab: Using PHAR deserialization to deploy a custom gadget chain](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-using-phar-deserialization-to-deploy-a-custom-gadget-chain)
