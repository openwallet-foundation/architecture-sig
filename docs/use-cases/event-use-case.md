# Event Use Case

This document covers the typical use cases that would require a wallet when an individual wants to purchase ticket(s) and attend an event. In this scenario, we have an Attendee that will use a Ticket Seller's website to browse for ticket(s) to a specific event that they wish to attend. When the Attendee finds the specific seat(s) that they would like to purchase, they use their wallet to pay for the ticket(s). Upon successful payment, the ticket(s) are added to the Attendee's wallet. From here, there are two distinct steps that the Attendee can take:
1. Attend the event, which will require redeeming the ticket to gain entry into the Event Venue
2. Sell the ticket to someone else, which will require transferring the ticket from the Attendee's wallet to the Buyer's wallet

Potential Complexities:
* Two people should not be able to utilize the same ticket to gain access to the event.
* What considerations exist to ensure that the purchaser of the ticket is the one redeeming the ticket? For example, for stolen wallets or high-value tickets.

## Use Case Diagram
```mermaid
flowchart LR
  Attendee
  subgraph uc[Use Cases]
    uc1(["Purchase Ticket"])
    uc2(["Save Ticket"])
    uc3([Redeem Ticket])
    uc4([Sell Ticket])
  end
  Attendee-->uc1 & uc2 & uc3 & uc4
```

### Purchase Ticket
| **Use Case ID**     | Purchase Ticket |
|---------------------|----------------|
| **User Story**      | As an Attendee, I want to purchase a ticket via a Ticket Seller to an event so that I may gain entry to the event at the Event Venue. |
| **Goal**            | Puchase a ticket so that I can attend an event. |
| **Actors**          | **Primary:** Attendee |
|                     | **Secondary:** Ticket Seller (TS), Event Venue (EV) |
| **Pre-Conditions**  | 1. The Attendee has access to the Ticket Seller.<br/> 2. The Attendee has a wallet with a valid financial instrument. |
| **Post-Conditions** | 1. The Attendee's has successfully purchased the ticket. |
| **Trigger**         | The Attendee launches the Ticket Seller's (TS) website via their internet browser. |
| **Main Flow**       | 1. The TS website lists the different events available and provides a search mechanism.<br/> 2. The Attendee searches for the event they wish to attend.<br/> 3. The TS website displays events matching search criteria.<br/> 4. The Attendee clicks on the event to list the available seats.<br/> 5. The TS website displays the available seats.<br/> 6. The Attendee selects the seats they wish to reserve and clicks the "Reserve Seats" button.<br/> 7. The TS website displays the "Pay" page for the selected seats and requests payment.<br/> 8. The Attendee chooses to "Pay with their OWF-powered wallet".<br/> 9. The TS website redirects the Attendee to the OWF powered wallet to complete payment.<br/> 10. The Attendee chooses the payment instrument and submits the payment.<br/> 11. The OWF-powered wallet transmits payment instructions to the TS website.<br/> 12. The TS website validates payment.<br/> 13. Upon successful payment, the TS website sends information to the EV regarding the purchased ticket and marks the ticket as sold in the TS database<br/> 14. Upon successful payment, the TS website displays receipt page, which includes a "Save Ticket to OWF-powered Wallet" option.<br/> 15. Use Case Ends |
| **Exceptions**      | 1. Step 1. The TS website is down.<br/>2. Step 2-10. The Attendee closes the browser window. The seats that have been reserved must be returned to available after a given amount of time.<br/>3. Step 11. The transmission from the OWF-powered wallet to the TS website fails. The payment should not occur and the seats that have been reserved must be returned to available after a given amount of time.<br/> 4. Step 12. The payment is not successful. The seats that have been reserved must be returned to available after a given amount of time.<br/> 5. Step 13. The transmission between TS and EV fails. Corrective action must be made to ensure EV knows of valid ticket sale.<br/> 6. Step 13. The database update fails. Corrective action must be made to ensure that the ticket cannot be sold a second time.<br/> 7. Step 13-14. The Attendee closes the browser window. The seats have been reserved and the attendee must have an alternative option to obtain the ticket. |
| **Wallet Functionality Needed** | 1. Ability for a website to use the wallet as a payment mechanism. |

### Save Ticket
| **Use Case ID**     | Save Ticket |
|---------------------|----------------|
| **User Story**      | As a ticket purchaser, I want to save the ticket to my wallet. |
| **Goal**            | Save a ticket to the wallet so that I can attend an event. |
| **Actors**          | **Primary:** Ticket Purchaser (TP) |
|                     | **Secondary:** Ticket Seller (TS) |
| **Pre-Conditions**  | 1. The ticket purchaser has a wallet.<br/> 2. The ticket purchaser has purchased a ticket (see _Purchase Ticket_ use case) |
| **Post-Conditions** | 1. The Attendee's wallet contains the ticket. |
| **Trigger**         | The Ticket Purchaser clicks the "Save Ticket to OWF-powered Wallet" option on the Ticket Seller's website or email. |
| **Main Flow**       | 1. The TS system sends the ticket to the Attendee's OWF-powered Wallet.<br/> 2. Use Case Ends. |
| **Exceptions**      | 1. Step 1. The transmission of the ticket from the TS system to the OWF-powered wallet fails. The ticket purchaser must be able to retry to save functionality again or have an alternative way to obtain the ticket. |
| **Wallet Functionality Needed** | 1. Ability to save a ticket to the wallet. |

### Redeem Ticket
| **Use Case ID**     | Redeem Ticket |
|---------------------|----------------|
| **User Story**      | As a Ticket Holder, I want to be able to gain entry to an event at the Event Venue by redeeming my ticket. |
| **Goal**            | Gain entry to an event by redeeming my ticket. |
| **Actors**          | **Primary:** Ticket Holder (TH) |
|                     | **Secondary:** Event Venue (EV)|
| **Pre-Conditions**  | 1. The Ticket Holder has a ticket within their wallet.<br/> 2. The Ticket Holder is at the Event Venue. |
| **Post-Conditions** | 1. The Ticket Holder has gained access to the event.<br/> 2. The Ticket has been marked as redeemed (i.e., the ticket not be used again to gain entry). |
| **Trigger**         | The Ticket Holder reaches the front of the queue at the Event Venue. |
| **Main Flow**       | 1. The Ticket Holder (TH) opens their wallet and searches their wallet for the specific event ticket.<br/> 2. The Wallet displays the event matching the search criteria.<br/> 3. The TH clicks the specific event.<br/> 4. The wallet determines the correct mechanism used to gain access to the Event Venue and displays the selected ticket using the appropriate mechanism.<br/> 5. The TH presents the ticket to the Event Venue's device reader. <br/> 6. The device reader queries the EV's system to ensure the ticket is valid and displays validity to the Event Venue attendant.<br/> 7. The Event Venue allows the TH access to the event.<br/>8. Use Case Ends |
| **Exceptions**      | 1. Step 1-5. The TH steps out of line. The TH is not allowed access to the event.<br/> 2. Step 1-5. The TH cannot locate the ticket to the event in their wallet. The TH is not allowed access to the event.<br/> 3. Step 6. The ticket is not valid. The Ticket Holder is not allowed access to the event. |
| **Wallet Functionality Needed** | 1. Ability to view all event tickets in the wallet.<br/> 2. Ability to use a specific ticket to gain entry to an event (mechanisms may include QR code, barcode, NFC tap).<br/> 3. Ability to view the tickets in the wallet without data access (device download). |

### Sell Ticket
| **Use Case ID**     | Sell Ticket |
|---------------------|----------------|
| **User Story**      | As a Ticket Holder, I want to be able to sell my ticket to another person. |
| **Goal**            | Sell a ticket to a secondary buyer so that they may gain access to the event. |
| **Actors**          | **Primary:** Ticket Holder (TH), Ticket Buyer (TB)   |
|                     | **Secondary:** Event Venue (EV) |
| **Pre-Conditions**  | 1. The TH has a ticket in their wallet. |
| **Post-Conditions** | 1. The TB has the ticket in their wallet.<br/> 2. The TH no longer has the ticket in their wallet. |
| **Trigger**         | The TH and TB agree to the terms of the sale. |
| **Main Flow**       | 1. The TB pays the TH for the ticket.<br/> 2. The TH transfers the ticket to the TB's wallet.<br/> 3. Use Case Ends. |
| **Exceptions**      | 1. Step 1-2. Both of these steps should be atomic in nature. If one fails, the other should also fail to complete. |
| **Wallet Functionality Needed** | 1. Ability to view all event tickets in the wallet.<br/> 2. Ability to transfer an event ticket to another wallet. |

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