# Why trust any Request for Verification?

Authors: Tom Jones, …

Date: 2023-10-30 (OWF Arch meeting)

## Abstract

Innovators love to solve the easy cases for any new technology so that they can be first to market with a viable product. For those technologies that impact all users, such a strategy can result in highly negative responses from many users that would prevent their use in broad applications like the rights and privileges granted to residents by governments or other organization with an obligation to provide solutions for all who need them. This is a discussion of the hard problems in user consent to any request for verification of their identifiers, attributes or rights. As such, it focuses on the mobile device to mobile device use cases where the device holder has no location specific signals that might help them make an informed choice and so it totally reliant on signals from the verifier to make their trust decisions.

## Scenarios

These three scenarios are not exhaustive, but intended to span the wide range of cases where two people, unknown to each other, must exchange credentials in any random location where required.

### Emergency Medicine (Break the Glass)

Here the consent is provided by the medical establishment based on the condition of the patient. The device can be accessed to provide access to critical health information to aid the patient and prevent life-threating action by the emergency provider.

### Gig contractors Delivery of restricted goods

A Door-dash employee is given a package to deliver that is either valuable or includes restricted goods. If the holder has an mDL they can hold their device close to the device of the driver to provide proof of access to the goods in question. There is little in the physical world to distinguish between a legitimate delivery and a random attacker trying to get user information, especially if the delivery is an unexpected gift.

### Customs and Border Patrol Agent

A government employee on duty sees a person access an area that requires explicit permission. The holder and employee hold up their devices. The holder can see the authority for the request on their own device and decides to provide the data request. While it is illegal to present false government credentials, this sort of attack can be hard to track back to an individual presenting false credentials.

## Problems

The holder of the device must trust the packet of information that is sent to their device by the verifier with very little evidence from the real world to help inform their decision. This is new ground, and the user experience must be acceptable to the holder and the security must be accepted by both parties.

### Privacy

The big issues endlessly discussed are tracking, identification and user choice. None are clearly defined.

There has been a wide-spread reaction against tracking by large private enterprises and by public authorities. But people appreciate attention to their concerns which is facilitated by tracking \their current state as well as tracking bad actors to prevent them from breaking the laws against us as we use the public networks. The creation of a public consensus on exactly when tracking is beneficial will be a major challenge if new technologies are to be accepted by all the residents who require it for access.

Identification is required when accessing controlled resources. The state of Washington has nearly 200 different licenses that are used to allow access to locations, social services, and types of employment. But there are times when all of us want to go about our business and "be let alone", which is the original purpose of legal privacy as defined by Brandeis and Warren.

### User Experience

User choice is often touted as the solution to the problems above. But there appears to be little concern for user experience of constant questioning before they are allowed to proceed with their daily business. Many of the proposed identification solutions appear to be tolerable as a continues tax on people's attention as they are navigating the digital ecosystems of their smartphones and laptop computers.

No consistent user experience has been proposed for instantiating a connection from the wallet to the verifier or determine what information the user needs to see to make an informed decision without annoying the user with multiple screens or confusing statement of non-compliance between the wallet and verifier or requests for the user to instantiate a different wallet that the verifier will accept. While something like this confusion can exist when presenting user credentials to get access to health care or other sites, when there is a human asking for the appropriate credential, the user can see all their choices by looking into their wallet. Nothing similar is part of the planning for a digital credential. One possible data flow is outlined below.

The user trusts their phone & wallet. What does wallet present to the user. Some sort of trust mark applied by the wallet. Can this be in scope for OWF?

### Governance and Compliance

The issues here are what standards, exactly, should apply in any situation. It's not enough that we have North American and Europe on difference trajectories, but that multiple sources of standardizations exist, even within the W3C. Once the standards exist, some means of indication compliance within the messages transferred between entities needs to be written out. What applies when I take my Washington State DL to Hungary?[https://openidentityexchange.org/networks/87/item.html?id=708](https://openidentityexchange.org/networks/87/item.html?id=708)

The wallet needs to provide proof of conformance at an appropriate level of assurance. (Juliana)

The verifier needs to give the user confidence to proceed.

## Existing solutions

### LA Wallet

The state of Louisiana was an early mobile driver's license provider. They deployed a new design where the same wallet could be used by the holder of the wallet as well as by others that wanted to get some data from another holder of an LA Wallet. The balance of identification and privacy has not been addressed. Not ISO std.

### Government Employee on the job

The badge given by a sovereign entity to any employee carrying out the laws of the land is a badge of authority which must be respected by all who see it presented by an official. Impersonation of a badge holder is typically a serious offence. The way that this would be presented on a user device for an informed choice is not defined.

### First Responders on the job

In the case of King County in the State of Washington, an emergency physician is employed by the county that has the authority to issue access tokens to Emergency Medical Technicians (EMTs) to apply medical procedures to patients that are non-responsive. These permissions apply only to that individual during the time on duty.

### Bank Payment systems

Before a bank is willing to pay a demand, it must be convinced that the holder of the account has given approval. This process is well-tested over many years and is often used for access to other venues as well, especially in the Nordic countries of Europe. Its adoption in other countries has been slowed, in part because the banks do not want to accept the liabilities involved in cross-purpose identification (aka single sign on).

### Federated systems (Unions, Schools, Workplaces)

One of the most common places for identifier credentials is access to a common space by a closed set of people. Up till now this solution was handled well by smart cards that could respond to nearby signals that also serve to power the card for the time it took to get a positive identification. If the need arises for use of the identifier in other scenarios, the smart card solution might need to be migrated to a smartphone wallet. It would be fairly easy for an attacker to steal an existing mobile device and reverse engineer it for malevolent purposes in locations where online validation was not practical. Extending the use of the single purpose identification to other organizations is a reality, but not well understood.

### US DHS TSA specifications for travel from US airports

Proposals for regulations have been posted and responses made from, among others, the ACLU and friends. Clearly government regulations will need to be met and we have in front of us several proposals that could be reconciled and commented upon.

## Data Flows

1. The holder of a mobile device comes to a place where access to some asset requires that the holder, or the subject of a credential, must justify their right to access the resource.
2. Each one, the holder, and the verifier, must recognize the type of credential required and have the appropriate wallet and verification app running. For the holder of the wallet this might be a challenge unless the verifier provides some sort of indication to help the user. – It could be the active wallet on that channel can determine if it can cope with the verifier or help the user select
3. The verifier and the holder hold their devices in close proximity and some communication protocol carries the request of the verifier with sufficient information to convince the holder to release their own data to the verifier.
4. It is here assumed that the verifier agent holding the device needs to provide the holder of the need for the information and of their authority to require the information. The purpose of the request is made clear in the data flow along with a signed request that the holder can use to determine the how, what, where and why of the request made (called the receipt).
5. The holder's device has been provisioned with an application (called a wallet) installed on their device which has the information to prove their access to the resource.
6. The Wallet creates a User Experience (described below) with a choice button, and possibly some options for optional data.
7. The holder gestures their acceptance of the terms.
8. The Wallet now stores the receipt from the verifier with their response for future reference.

Assumptions: communications are secure. The above assumes the holder is the subject. There is no phone-home. The wallet contains some sort of core list of trusted entities to make a consent decision.

The wallet needs the capability to express all that it can to the user to make an informed decision.

Device capability needs to be expressed. Different users have different phones.

## User Experiences

The receipt of the request provided by the verifier to the user must be sufficient to give the holder of the device the confidence to make an informed choice. The default screen will include the information that most holders will need to see prior to making an informed choice.

1. The verifier's authority and identifier to request data.
2. The verifier's purpose in requesting the data.
3. The data retained by the verifier if not clear from the purpose.
4. The security of the device transmitting the request.
5. The authority of the agent of the verifier holding the device.
6. The recourse to the verifier for validation of information collected.
7. A set of opt-in data elements that are above and beyond the purpose of the request.
8. The gesture required to indicate consent to release data to allow access to the resource
9. Access to full details of the terms and conditions for the people who really need to know.

## Notes and Conclusions

ISO 18013-5 required the issuer to verify the governance of the wallet and of the verifiers. Not sure that works for all cases. Someone else's problem field here.

The assumption for these use cases is that all transactions happen with one request and one response. That means that no consideration was given to the creation of a session between the devices. In more complex cases such a session creation might produce a better user experience, or it might prolong the decision-making process to the point where the user gets really annoyed or just gives up the whole concept of digital identifiers and goes back to paper credentials.

Since these use cases focus on just the wallet and the verifier, more complex cases like those found in browser interactions with websites using single-sign-on (SSO) protocols are not discussed. It would still be possible to continue a protocol interaction with just the wallet and verifier, but any authentication process would remain local to those two entities. In other words, these interactions mimic those found in real world wallets, not those in complex website navigations.

Given the above limitations, these example use cases do show the way to provide sufficient information to the wallet holder to make informed trust decisions about the verifier that can carry forward to more complex transactions.
