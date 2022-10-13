![Status](https://img.shields.io/badge/status-draft-important) [![License](https://img.shields.io/badge/license-cc--by--4.0-informational)](http://creativecommons.org/licenses/by/4.0/)

# Use Cases
This page will document the different use cases where a wallet is expected to be used.

```mermaid
%%{ init: { 'flowchart': { 'curve': 'linear' } } }%%
flowchart LR
  wh[Wallet Holder]
  subgraph d[Driving]
    subgraph odl[Obtain Driver's License]
      odlUC1([Prove Identification])
      odlUC2([Store License])
    end
    subgraph dpl[Present License]
      dplUC1([To Police Officer])
      dplUC2([To Accident Participants])
      dplUC3([To Insurance Agent])
    end
    subgraph dpi[Present Proof of Insurance]
      dpiUC1([To Police Officer])
      dpiUC2([To Accident Participants])
    end
    subgraph dpe[Prove Vehicle Entry Requirements]
      dpeUC1([To Toll Booth])
      dpeUC2([To Parking Attendant])
    end
  end
  subgraph em[Employment]
   emUC1([Prove Education])
   emUC2([Prove Work Experience])
   emUC3([Prove Current Employment])
  end
  subgraph ev[Event]
    evUC1([Purchase Ticket])
    evUC2([Sell Ticket])
    evUC3([Redeem Ticket])
    evUC4([Purchase Merchandise])
  end
  subgraph h[Healthcare]
    hUC1[Prove Medical Insurance]
    hUC2[Obtain Prescription]
    hUC3[Prove Vaccination Status]
  end
  subgraph i[Identification]
    iUC1([Prove Citizenship])
    iUC2([Prove Age])
    iUC3([Prove Place of Birth])
    iUC4([Prove Residency])
    iUC5([Prove Legal Personage])
  end
  subgraph p[Purchase]
    pUC1([Determine Acceptable Instruments])
    pUC2([Present Instrument])
  end
  subgraph s[Shopping]
    sUC1([Purchase Merchandise])
    sUC2([Return Merchandise])
  end
  subgraph t[Travel]
    tUC1([Purchase Ticket])
    subgraph tpt[Present Ticket]
      tptUC1([To Bag Check])
      tptUC2([To Security])
      tptUC3([To Gate Agent])
    end
    tUC2([Reserve Lodging])
    tUC3([Present Reservation])
  end
  wh-->d & em & ev & h & i & s & t
  evUC1 & evUC4 & sUC1 & tUC1-->p
  click evUC1 "./docs/use-cases/event-use-case.md#purchase-ticket" "See details"
  click evUC2 "./docs/use-cases/event-use-case.md#sell-ticket" "See details"
  click evUC3 "./docs/use-cases/event-use-case.md#use-ticket" "See details"
```

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.