![Status](https://img.shields.io/badge/status-draft-important) [![License](https://img.shields.io/badge/license-cc--by--4.0-informational)](http://creativecommons.org/licenses/by/4.0/)

# Decentralized Identifiers

```mermaid
classDiagram


class DID {
    <<Abstract>>
    + DID id
    resolve()
}

class DIDUrl {
    <<Abstract>>
    + DIDUrl id
    dereference()
}

class ResolutionOptions {
    <<Abstract>>
    + String Accept
}

class DIDDocument {
    <<Abstract>>
    + DID id
    + List~VerificationMethod~ authentication
    + List~VerificationMethod~ assertionMethod
    + List~VerificationMethod~ capabilityInvocation
    + List~VerificationMethod~ capabilityDelegation
    + List~VerificationMethod~ keyAgreement
    + List~Service~ service
    + create()
    + resolve(ResolutionOptions options) : DIDResolutionResult
    + update()
    + deactivate()
}

class DIDResolutionResult {
    <<Abstract>>
    + DIDResolutionMetadata ResolutionMetadata
    + DIDDocument DIDDocument
    + DIDDocumentMetadata DIDDocumentMetadata
}

class DIDDocumentMetadata {
   <<Abstract>>
   + String Created
   + String Updated
   + bool Deactivated
   + String NextUpdate
   + String VersionID
   + String NextVersionID
   + String EquivalentID _
   + String CanonicalID
}

class ResolutionError {
    <<Abstract>>
    + String Code
    + bool InvalidDID
    + bool NotFound
    + bool RepresentationNotSupported
}

class DIDResolutionMetadata {
    <<Abstract>>
    + String ContentType
    + ResolutionError Error
}

class VerificationMethod {
    <<Abstract>>
    + DIDUrl id
    + String type
    + DID controller
    + PublicKey publicKeyJwk
    + verify()
    + encrypt()
}

class Service {
    <<Abstract>>
    + DIDUrl id
    + String type
    + String serviceEndpoint
}

class IIdentifier {
    <<interface>>
    String did
    DIDDocument doc
}

class IdentifierProvider {
    <<abstract>>
    +create(KeyManagementService kms) IIdentifier
    +update(KeyManagementService kms) IIdentifier
    +resolve(KeyManagementService kms) bool
    +deactivate(KeyManagementService kms) bool
    +register(IIdentifier identity, String registry?) bool
}

class IdentifierStore {
    <<abstract>>
    +import(IIdentifier args) bool
    +get(String did) IIdentifier
    +delete(String did) bool
    +list(String provider?) List~IIdentifier~
}

class IdentifierManagementService {
    -List~IdentifierProvider~ providers
    -IdentifierStore store
    -KeyManagementService kms
    +createIdentifier(String alias?, String tag?, String provider?) IIdentifier
    +importIdentifier(IIdentifier identity, String alias?, String tag?) IIdentifier
    +updateIdentifier(String did, DIDDocument doc,String alias?, String tag?, String provider?) IIdentifier
    +getIdentifier(String did, String alias?, String tag?, String provider?) IIdentifier
    +getIdentities(String alias?, String tag?, String provider?) List~IIdentifier~
    +deleteIdentifier(String did, String provider?) bool
    +getIdentifierProviders(String provider?) List~IdentifierProvider~
}

IdentifierManagementService "1" .. "1" IdentifierStore
IdentifierManagementService "1" .. "1" KeyManagementService
IdentifierManagementService "1" *.. "many" IdentifierProvider

IdentifierStore "1" .. "many"  IIdentifier
IIdentifier "1" .. "1"  DIDDocument

DIDDocument "1" .. "1" DID
DIDDocument "1" *.. "many" VerificationMethod
VerificationMethod "1" .. "1" DIDUrl
VerificationMethod "1" .. "1" DID
DIDDocument "1" *.. "many" Service
Service "1" .. "1" DIDUrl


DIDResolutionResult "1" .. "many" DIDDocument
DIDDocumentMetadata "1" .. "1" DIDResolutionResult
DIDResolutionMetadata "1" .. "1" DIDResolutionResult
ResolutionError "1" .. "1" DIDResolutionResult
ResolutionOptions "many" .. "1" DIDDocument
```

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
