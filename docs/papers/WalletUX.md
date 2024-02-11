# Wallet User Experience

## Full Title

The contents and availability of notifications to the user of a digital [Wallet](https://tcwiki.azurewebsites.net/index.php?title=Wallet) needs to satisfy both privacy concerns and user preferences.

## Summary Bullet Points for Architecture Documentation

- What type of user experience should we expect for obtaining credentials?
- What type of user experience should we expect before presenting protected data?
- How can the messages to the wallet enable it to create a good UX?

## Goals

The following are the required **success criteria** for both the user and the Verifier.

- Before the wallet can reach its full potential, it needs to acquire appropriate credentials.
- The user expects that the use of the wallet will not present any additional obstacles to stress-free verification. Typically, this means that the verification process will not degrade the user experience by creating excessively long wait times at the point of verification.
- The point of **Wallet Notices** is to supply the data needed for a stress-free [User Experience](https://tcwiki.azurewebsites.net/index.php?title=User_Experience) with credentials and other private data.
- Either the user has selected the wallet to contact the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier), or the initial request from the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) is used by the device to direct the request to the Wallet.
- Notices from the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) identify it and the verified data it needs for the purpose of providing access to some resource.
- The display of the Verifier notification will be created by the [Wallet](https://tcwiki.azurewebsites.net/index.php?title=Wallet) based on user settings.
- Some sort of user gesture is to be required by the Wallet before any data about the user or wallet is authorized to be sent to the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier).
- Once user data has been release to the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) it is responsible for notifications of any release of user data not approved by the user.
- When possible these breaches and any terms updates will be stored by the wallet along with [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) requests that the user has accepted.
- The user will be able to view these notifications for as long as the user has told the wallet to retain them.
- It is a requirement that all eligible users have access to any advantages that are digitally available and so those credentials where the subject is not competent to handle digital credentials still must have access to all benefits available to others. (perhaps this should be in inclusion section?)

## Context

- The user will have a device in their possession that contains, at a minimum, cryptographic keys and the ability to securely display information to the user.
- The location of the rest of the wallet functionality is not specified.
- The term "user" here applies to the wallet holders [Subjects](https://tcwiki.azurewebsites.net/index.php?title=Subject) of the presentation and delegates when they are different from the holder.
- Typically, only the holder (owner) of the wallet receives and stores notices.
- This section considers only the role of the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) as it is assumed that the issuer or any other party first needs to verify the wallet and holder of the wallet before exchanging any certificate data.
- Government legislation that mandates the release of information on different terms than these is not in the scope of this page.
- A Privacy Transparency Statement will be included in (or prior to) any request for [Subject](https://tcwiki.azurewebsites.net/index.php?title=Subject) information.
- Any communications partner of the holder can supply credentials in multiple formats. It is the holder's choice about storing those credentials in the wallet.

## Problems

- User fatigue sets in on excessive notice displays. This fatigue is different for different users and so display thresholds need to be under user control.
- [Smartphones](https://tcwiki.azurewebsites.net/index.php?title=Smartphone) typically have one overall notification setting per app. The wallet notification setting should be on, but many users may not choose to enable it.
  - The wallet may require notifications before they start operations, but product marketing staff are likely to object to that requirement.
  - Smartphones provide detailed settings under notifications (Banners, Sounds, Badges, etc.), but they are very seldom part of the user's attention.
- Some wallet devices can be tracked by the radio signals that are released as a part of establishing a connection to the wallet.
- At the time that the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) creates the request and provides their own [Identifier](https://tcwiki.azurewebsites.net/index.php?title=Identifier) and privacy transparency statement, the [Identifier](https://tcwiki.azurewebsites.net/index.php?title=Identifier) of the Holder is not known. The [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) probably records the endpoint network address of the [Entity](https://tcwiki.azurewebsites.net/index.php?title=Entity) that contacted them, but that could just be the address of a VPN endpoint.
- Most statements of terms and conditions are too long to display on a single wallet screen to the user, but still must be available in some form that persists in the wallet and can be examined by the user whenever they wish to view them.

## Solutions

- Holder of wallets must be able to be delegates of all eligible subjects that have access to the credentials offered to wallet holders. Eligibility is typically determined by local law.
- Where required during verification, the wallets may offer support of liveness detection as proof of presence. The user needs to understand the reason for access to biometric sensors where this is required. Typically, this requires that the camera or other sensor data is available to the wallet.
- Liveness detection may be offered by the Verifier with suitable notification and opt-out by the user.
- All secure digital identifiers must be sourced from a digital device in the subject's possession. The device must be able to understand something you have (a private key) is linked to something you are (a sensor on the device.)
- The initial message from the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) to the user must contain:

1. An identification of the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) that can be presented to the user in terms that they can understand.
2. A Privacy Transparency Statement that can be presented to the user as a part of a request to which the user must positively indicate acceptance.
  1. The purpose(s) for which the user credential and other data is required. This must be something the user sees and understands.
  2. If the purpose is not sufficient the wallet can present detailed data requests so long as they are covered by the purpose.
  3. Optionally the verifier can ask for other data, this is not required, but if present requires opt-in by the user.
  4. Some indication as to the retention period for data if it is stored by the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) beyond the verification process itself.
  5. Whenever data is stored, some contact information must be supplied for the user to determine what data is stored or request deletion of the data.
  6. The jurisdiction under which the data retention is controlled. (Whether this is part of trust registry is tbd.)

- On any extended relationship between the verifier and holder, changes to future transaction terms and conditions must create a new consent request.
- Breach notifications are likely to be covered by local government regulations. Where possible these should be as notifications to the wallet.
- The [User Experience](https://tcwiki.azurewebsites.net/index.php?title=User_Experience) must allow the holder to review past transactions with any site that asks for subject private information.

### Audit

- The only way to verify that privacy-preserving mandates are satisfied is for some level of auditing as to what a [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) actually does.
- Audits are likely to have some information that should not be released to the public.
- A list of notifications from [Verifiers](https://tcwiki.azurewebsites.net/index.php?title=Verifier) should be maintained by user wallets for the user's sole benefit. This can be considered to be an audit trail.
- Audit trails in the [Verifier](https://tcwiki.azurewebsites.net/index.php?title=Verifier) containing user private information must be protected by encryption or similar levels of disclosure protection.

## References

- ISO/IEC TS Privacy technologies 27560:2023 Consent record information structure [https://www.iso.org/standard/80392.html](https://www.iso.org/standard/80392.html)
- H. Rosnagel, et al. Research on User Experience for Digital Identity Wallets: State-of-the-Art and Recommendations (2023) https://publica-rest.fraunhofer.de/server/api/core/bitstreams/f14ff390-c8a1-42ee-8256-326e2ab41b47/content

