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
