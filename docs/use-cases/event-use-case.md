# Event Use Case

This document covers the typical use cases that would require a wallet when an individual wants to purchase ticket(s) and attend an event. In this scenario, we have a user Alice that will use a ticket seller's website to browse for ticket(s) to a specific event that they wish to attend. When Alice finds the specific seat(s) that they would like to purchase, they use their wallet to pay for the ticket(s). Upon successful payment, the ticket(s) are added to Alice's wallet. From here, there are two distinct steps that Alice can take:
1. Attend the event, which will require using the ticket to gain entry into the event venue
2. Sell the ticket to someone else, which will require transferring the ticket from Alice's wallet to the buyer's wallet

## Use Case Diagram
```mermaid
flowchart LR
  alice
  subgraph uc[Use Cases]
    uc1["Purchase Ticket(s)"]
    uc2[Use Ticket]
    uc3[Sell Ticket]
  end
  alice-->uc
```

### Purchase Ticket
|                     |                |
|---------------------|----------------|
| **Use Case ID**     | Purchase Ticket |
| **User Story**      | As an Attendee, I want to purchase a ticket via a Ticket Seller to an event so that I may gain entry to the event at the Event Venue. |
| **Goal**            | Puchase a ticket so that I can attend an event. |
| **Actors**          | **Primary:** Attendee  |
|                     | **Secondary:** Ticket Seller, Event Venue |
| **Pre-Conditions**  | 1. The Attendee has access to the Ticket Seller.<br/> 2. The Attendee has a wallet with a valid financial instrument. |
| **Post-Conditions** | 1. The Attendee's has successfully purchased the ticket.<br/> 2. The Attendee's wallet contains the ticket. |
| **Trigger**         | The Attendee launches the Ticket Seller's (TS) website via their internet browser. |
| **Main Flow**       | 1. The TS website lists the different events available and provides a search mechanism.<br/> 2. The Attendee searches for the event they wish to attend.<br/> 3. The TS website displays events matching search criteria.<br/> 4. The Attendee clicks on the event to list the available seats.<br/> 5. The TS website displays the available seats.<br/> 6. The Attendee selects the seats they wish to reserve and clicks the "Reserve Seats" button.<br/> 7. The TS website displays the "Pay" page for the selected seats and requests payment.<br/> 8. The Attendee chooses to "Pay with their OWF-powered wallet".<br/> 9. The TS website redirects the Attendee to the OWF powered wallet to complete payment.<br/> 10. The Attendee chooses the payment instrument and submits the payment.<br/> 11. The OWF-powered wallet transmits payment instructions to the TS website.<br/> 12. The TS website validates payment.<br/> 13. Upon successful payment, the TS website displays receipt page, which includes a "Save Ticket to OWF-powered Wallet" option.<br/> 14. User selects "Save Ticket to OWF-Powered Wallet" button.<br/> 15. The TS website sends the ticket to the Attendee's OWF-powered Wallet.<br/> 16. Use Case Ends |
| **Exceptions**      | 1. Step 1. The TS website is down.<br/>2. Step 2-10. The Attendee closes the browser window. The seats that have been reserved must be returned to available after a given amount of time.<br/>3. Step 11. The transmission from the OWF-powered wallet to the TS website fails. The payment should not occur and the seats that have been reserved must be returned to available after a given amount of time.<br/> 4. Step 12. The payment is not successful. The seats that have been reserved must be returned to available after a given amount of time.<br/> 5. Step 13-14. The Attendee closes the browser window. The seats have been reserved and the attendee must have an alternative option to obtain the ticket.<br/> 6. Step 15. The transmission of the ticket from the TS website to the OWF-powered wallet fails. The seats have been reserved and the attendee must have an alternative option to obtain the ticket. |

### Use Ticket
| **Use Case ID**     |                |
|---------------------|----------------|
| **User Story**      |                |
| **Goal**            |                |
| **Actors**          | **Primary:**   |
|                     | **Secondary:** |
| **Pre-Conditions**  |                |
| **Post-Conditions** |                |
| **Trigger**         |                |
| **Main Flow**       |                |
| **Exceptions**      |                |

### Sell Ticket
| **Use Case ID**     |                |
|---------------------|----------------|
| **User Story**      |                |
| **Goal**            |                |
| **Actors**          | **Primary:**   |
|                     | **Secondary:** |
| **Pre-Conditions**  |                |
| **Post-Conditions** |                |
| **Trigger**         |                |
| **Main Flow**       |                |
| **Exceptions**      |                |

## Overall Sequence Diagram
```mermaid
sequenceDiagram
  actor Alice
  participant aw as Alice's Wallet
  participant ts as Ticket Seller
  participant ev as Event Venue
  actor Bob
  participant bw as Bob's Wallet
  opt Add Financial Instrument
    Alice->>aw: addFI(fiDetails)
  end
  loop Select Tickets
    Alice->>ts: chooseTicket(ticketDetails)
    ts->>ts: addTicketToCart(ticketDetails)
  end
  opt Checkout
    Alice->>ts: checkout(walletEndpoint)
    aw->>ts: determineAcceptablePaymentOptions()
    ts-->>aw: availablePaymentOptions
    Alice->>aw: Select Financial Instrument
    aw->>ts: sendPaymentDetails(paymentDetails)
    alt Payment Accepted
      ts-->>aw: ticket
    else Payment Denied
      ts-->>aw: error
    end
  end
  opt Attend Event
    Alice->>aw: Choose Ticket
    aw->>aw: Display QR Code
    Alice->>ev: Present QR Code
    alt Ticket Not Used
      ev->>ev: Mark Ticket as Used
      ev->>Alice: Allow Entry
    else Ticket Already Used
      ev->>Alice: Do NOT Allow Entry
    end
  end
  opt Add Financial Instrument
    Bob->>bw: addFI(fiDetails)
  end
  opt Sell Ticket
    Alice->Bob: Agree to Transaction Details
    critical Atomic Swap
      bw->>aw: Pay
      aw->>bw: Ticket
    end
  end
```