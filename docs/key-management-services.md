# Key Management Services

- [edit live](https://mermaid.live/edit)

This document describes generic key management services.

Note that this module is not related to "storing digital objects" that are cryptographic keys.

It is referring to the internal interfaces needed to securely manage "digital object".


```mermaid
classDiagram
    class KMS
    <<Abstract>> KMS
    KMS: + String service_identifier
    KMS: + generateKeyPair()
    KMS: + imortPrivateKey(PrivateKey)
    KMS: + getPublicKey(kid)
    class RemoteKMS{
      + String connection_credential
      + sign(String kid, Bytes msg)
      + verify(String kid, Bytes msg, Bytes sig)
    }
    class LocalKMS{
      + String connection_credential
      + sign(String kid, Bytes msg)
      + verify(String kid, Bytes msg, Bytes sig)
    }
    class PublicKey {
      + List~String~ tags
      + String description
      + String kid
      + String kty
      + String crv
      + String alg
      + List~String~ key_ops
      + String x
      + String y
      + verify(Bytes msg, Bytes sign)
    }
    class PrivateKey {
      + String d
      + sign(Bytes msg)
    }
    PrivateKey <|-- PublicKey
    
    RemoteKMS ..  PrivateKey
    LocalKMS ..  PrivateKey
    KMS <|-- RemoteKMS
    KMS <|-- LocalKMS
```
