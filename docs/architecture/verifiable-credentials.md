![Status](https://img.shields.io/badge/status-draft-important) [![License](https://img.shields.io/badge/license-cc--by--4.0-informational)](http://creativecommons.org/licenses/by/4.0/)

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

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.