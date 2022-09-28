# Architecture Task Force
This task force is intended to deliver a reference architecture for what the OpenWallet Foundation is looking to build. We are using [issues tagged with `module`](https://github.com/openwallet-foundation/architecture-task-force/issues?q=is%3Aissue+label%3Amodule) to define the different modules that we expect to find in the reference architecture.

## Conceptual Architecture (DRAFT)
```mermaid
%%{ init: { 'flowchart': { 'curve': 'linear' } } }%%
flowchart TD
  subgraph P[Protocols]
  end
  subgraph D[Digital Objects]
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
  end
  subgraph S[Storage]
    ES[Encrypted Storage]
    subgraph KS[Key Storage]
      TEE[Trusted Execution Environment]
      KV[Software Key Vault]
    end
  end
  subgraph C[Communication Manager]
  end
  S -.- D -.- P --> C
```

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.