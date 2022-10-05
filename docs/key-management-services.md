# Key Management Services

- [edit live](https://mermaid.live/edit#pako:eNrNU8FugzAM_ZUop6K1_QBUVdq021apGlekKg0us0qSyQloqOu_L2soUMIHjANynp8fz8a5cGkK4CmXlbD2FUVJQuWa-eeGsLddFo6bzfPROhLSbbcD6oOUPbHMEeqSWaAGJRywAO3whEAPrBI0kHDwBu1eIC2ShywqQ25P2ATGYgiTiYrb18cK5R_pjEUytvsByviaXXYJKBvMSaM1SIdGHyTBzaGoBpbFUi86qlddspfWgWXKlslAaoDw1M7T7qEX6iquY2fvRorqPxrrh8lia14oxlwbt0BNhImqjLDvCGmjHuZ861nj_YLMOC8mA5wOrVMaaWx-VqthGCEd3v1SsfV6XBKy9x8bJfutDdK9ygS_1_MlV0BKYOGv462hnLtPUJDz1IeFoHPOc331PFE7k7Va8tRRDUtefxX-o93t5elJVBauv4PCNIA)

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
      + String kid
      + String kty
      + String crv
      + String alg
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
