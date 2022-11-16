![Status](https://img.shields.io/badge/status-draft-important) [![License](https://img.shields.io/badge/license-cc--by--4.0-informational)](http://creativecommons.org/licenses/by/4.0/)

# Key Management Services

- [edit live](https://mermaid.live/edit)

This document describes generic key management services.

Note that this module is not related to "storing digital objects" that are cryptographic keys.

It is referring to the internal interfaces needed to securely manage "digital object".


```mermaid
classDiagram
    class KMS{
        <<Abstract>>
        + String service_identifier
        + generateKeyPair(String alg)
        + importPrivateKey(PrivateKey k)
        + exportPrivateKey(String kid)
        + getPublicKey(String kid)
        + getPublicKeys()
        + sign(String kid, Bytes msg)
        + verify(String kid, Bytes msg, Bytes sig)
        + encrypt(String kid, Bytes msg)
        + decrypt(String kid, Bytes msg)
    }
    class RemoteKMS {
        <<Service>>
        + String type
        + String connection_credential
        + destroy()
    }
    class LocalKMS {
        <<Service>>
        + String type
        + destroy()
    }
    class PublicKey {
        <<Interface>>
        + List~String~ tags
        + String description
        + String kid
        + String kty
        + String crv
        + String x5c
        + String alg
        + List~String~ key_ops
        + String x
        + String y
        + verify(Bytes msg, Bytes sig)
        + encrypt(Bytes msg)
    }
    class PrivateKey {
        <<Interface>>
        + String d
        + sign(Bytes msg)
        + decrypt(Bytes msg)
    }
    class SecretKey {
        <<Interface>>
        + List~String~ tags
        + String description
        + String kid
        + String kty
        + String crv
        + String alg
        + List~String~ key_ops
        + String d
        + encrypt(Bytes msg)
        + decrypt(Bytes msg)
    }
    PrivateKey o.. PublicKey
    KMS  ..> "many" SecretKey : contains
    KMS  ..> "many" PrivateKey : contains
    KMS  ..> "many" PublicKey : contains
    KMS <|.. RemoteKMS : implements
    KMS <|.. LocalKMS : implements
```

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.