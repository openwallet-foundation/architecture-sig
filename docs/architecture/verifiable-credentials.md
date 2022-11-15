# Verifiable Credentials

```mermaid
classDiagram

class Controller {
    <<Abstract>>
    + IRI id
    + List~IRI~ alsoKnownAs
    + List~VerificationMethod~ authentication
    + List~VerificationMethod~ assertionMethod
}


class Issuer~Controller~ {
    <<Service>>
    issue(Credential credential, PrivateKey privateKey) * VerifiableCredential
}


class Holder~Controller~ {
    <<Service>>
    present(Presentation presentation, PrivateKey privateKey) * VerifiablePresentation
}

class Verifier~Controller~ {
    <<Service>>
    verify(VerifiableCredential verifiableCredential, PublicKey publicKey) * Boolean
    verify(VerifiablePresentation verifiablePresentation, PublicKey publicKey) * Boolean
}



class Credential {
    <<Abstract>>
    + Context @context
    + IRI id
    + List~String~ type
    + Controller issuer
    + String issuanceDate
    + Object credentialSubject
    sign(PrivateKey privateKey)
}


class VerifiableCredential {
    <<Interface>>
    verify()
}

class Presentation {
    <<Abstract>>
    + Context @context
    + IRI id
    + List~String~ type
    + Controller holder
    + List~VerifiableCredential~ verifiableCredential
    sign(PrivateKey privateKey)
}

class VerifiablePresentation {
    <<Interface>>
    verify()
}



Controller .. Verifier
Controller .. Holder
Controller .. Issuer

Issuer "1" ..> "many" Credential : issues
Holder "1" ..> "many" Presentation : presents
Verifier "1" ..> "many" VerifiablePresentation : verifies

Holder "1" ..> "many" VerifiableCredential     : holds

VerifiablePresentation "1" ..o  "many" VerifiableCredential : contains

Credential ..|> VerifiableCredential : 
Presentation ..|> VerifiablePresentation : 
```
