![Status](https://img.shields.io/badge/status-draft-important) [![License](https://img.shields.io/badge/license-cc--by--4.0-informational)](http://creativecommons.org/licenses/by/4.0/)

# Conceptual Architecture
```mermaid
%%{ init: { 'flowchart': { 'curve': 'linear' } } }%%
flowchart BT
  subgraph A[ ]
    direction TB
    subgraph S[Storage]
      direction TB
      subgraph ES[Encrypted Storage]
        esLS[Encrypted Local Storage]
        esCS[Encrypted Cloud Storage]
      end
      subgraph KS[Key Storage]
        TEE[Trusted Execution Environment]
        KV[Software Key Vault]
      end
    end
    subgraph D[Digital Objects]
      direction TB
      subgraph I[Identity]
        VC[Verifiable Credentials]
        mID[Mobile ID]
      end
      subgraph F[Financial Instruments]
        CC[Credit Card]
        DC[Debit Card]
        LP[Loyalty Points]
      end
      subgraph DA[Digital Assets]
        FT[Fungible Tokens]
        NFT[Non-Fungible Tokens]
      end
      subgraph DK[Digital Keys]
        HK[Hotel Keys]
        AK[Automobile Keys]
      end
      subgraph CK[Cryptographic Keys]
        ckKS[Key Share]
        ckTBD["..."]
      end
      subgraph T[Tickets]
        ET[Event Ticket]
        TT[Transit Ticket]
        PT[Plane Ticket]
      end
    end
    subgraph PE[Policy Engine]
      peTBD["..."]
    end
    subgraph P[Protocols]
      direction TB
      pD[Deposit]
      pW[Withdrawal]
      pP[Purchase]
      pR[Refund]
      pPP[Present Proof]
      pT[Transfer]
      pS[Send]
      pR1[Receive]
      pB[Burn]
      pTBD["..."]
    end
    subgraph C[Communication Manager]
      direction TB
      QR[QR Code]
      NFC["Near Field Communication (NFC)"]
      MST["Magnetic Secure Transmission (MST)"]
      cmTBD["..."]
    end
    C ~~~ P ~~~ PE ~~~ D ~~~ S

    style A fill:#fff,stroke:#333,stroke-width:4px
  end
```

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.