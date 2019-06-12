---
title: "Get started with Secure Messaging for Healthcare organizations"
author: jambirk
ms.author: jambirk 
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: 
description: Get started with Secure Messaging for Healthcare organizations
---

# Get started with Secure Messaging for Healthcare organizations

Messaging policies are used to control which chat and channel messaging features are available to users in Microsoft Teams, and are part of the overall deployment of Secure Messaging for Healthcare organizations like Hospitals, clinics, or doctor's offices, where having a message picked up and acted upon in a timely manner is crucial, as is knowing when crucial messages are read.

You can use the default policy or create one or more custom messaging policies for people in your organization. After you create a policy, you will assign it a user or groups of users in your organization. For example, you may choose to only allow certain job roles to use these features (perhaps doctors and nurses only) and other workers (like the janitorial or kitchen staff) to get a more limited set of features. Decide for yourself what needs your organization has, the guidance here is at most a suggestion.

Policies can be easily managed in the [Microsoft Teams admin center](http://admin.teams.microsoft.com) by logging in with administrator credentials and choosing **Messaging Policies** in the left navigation pane.

 ![Screen shot of the Messaging policies page](../../media/messaging-policies-image1.png)

To edit the existing default Messaging policy for your organization, click the **Global (Org-wide default)** row, and then make your changes. To create a new custom messaging policy, click **New policy** and select your settings. Choose **Save** when you are done.

![Screen shot of  messaging policy settings](../../media/hc-message-policy.png)

The following settings are of special interest for Healthcare applications, and should be considered when designing a custom policy used in the Healthcare field:

## Read receipts

- ![Icon of the number 1, referencing a callout in the previous screenshot](../../media/sfbcallout1.png) **Read receipts** Read receipts allows the sender of a chat message to know when their message was read by the recipient. Use this setting to specify whether read receipts are user controlled, enabled for everyone, or disabled for everyone. Message read receipts are important in Healthcare organizations because they remove uncertainly about whether a message was read.

  For Healthcare applications, choose either **User controlled** or **Enabled for everyone**. Be aware that when using the **Enabled for everyone** setting, the only way to set receipts for the whole  tenant is either to have only one messaging policy for the whole tenant (the default policy named "Global (Org-wide Default)") or to have all messaging policies in the tenant use the same settings for receipts.

  > [!NOTE]
  > When read receipts are used in a large group chat (with over 100 users, for example), the receipt messages can overwhelm the actual messages, and lead to chat user frustration. This is something you will need to make users aware of. A smaller group chat (perhaps 20 users or less) makes better use of this feature.

    *Usage example without read receipts:* Jakob Roth, a high risk patient, is admitted to the hospital.  Sofia Krause is a nurse working as part of the inter-disciplinary team (IDT) of medical workers, including different specialists, is assigned as the primary care coordinator in charge of this patient.  Sofia sends emails and other instant messages to a groups of nurses and doctors who use a variety of messaging clients and apps, and often gets no response or indication whether a message was read by team members. Due to tangled communication processes, Jakob's medication is misapplied and his hospital stay is extended.

    *Usage example with read receipts:* Jakob Roth, a high risk patient, is admitted to the hospital.  Sofia Krause is a nurse working as part of the inter-disciplinary team (IDT) of medical workers, including different specialists, is assigned as the primary care coordinator in charge of this patient.  Sofia starts a group chat with a set of doctors and other nurses who will be working with the patient to coordinate care and starts an emergency triage.  The nurses and doctors communicate and collaborate over the patient's care plan throughout the care coordination process.  Important and urgent messages are sent through 1:1 and group chat conversations. Sofia uses the read receipts functionality to determine if messages sent requesting support are delivered and read by the targeted physicians or nurses. Jakob's patient outcomes are near-optimal and he goes home sooner because his care team communicates smoothly.

## Priority notifications

[!INCLUDE [preview-feature](../../includes/preview-feature.md)]

[!INCLUDE [pri-message-offer](../../includes/pri-message-offer.md)]

- ![Icon of the number 2, referencing a callout in the previous screenshot](../../media/sfbcallout2.png) **Users can send priority notifications** Use this setting to allow users to send priority chat messages to other users. This feature helps hospital staff alert one another when a critical incident requires their attention. Unlike regular “important” messages, priority notifications notify users repeatedly for a period of 20 minutes or until messages are picked up and read by the recipient, maximizing the likelihood that the message is picked up and acted upon in a timely manner.

  An admin can enable or disable the ability for users assigned this policy to send priority notifications. This feature is on by default. The recipient of the priority message might not have the same messaging policy, and will not have an option to disable receiving priority messages. For Healthcare applications, we recommend enabling the feature for at least some users, but you'll need to determine which ones.

  *Usage Example:* Sofia Krause is readmitting a high-risk patient, Jakob Roth. Manuela Carstens, a physician, is the primary care doctor for this patient.  Sofia sends a message to Manuela using a priority notification asking for immediate help with triage of Jakob.  Manuela's phone receives the message but Manuela didn't feel the phone vibration and does not reply. Teams re-notifies Manuela and will continue to persistently re-notify until she reads the message. If read receipts are also enabled, Sofia can be aware that the message was read by Manuela, even before Manuela decides how to respond.

## Related topics

- [Manage messaging policies in Teams](../../messaging-policies-in-teams.md)
- [Get started with Teams for Healthcare organizations](teams-in-hc.md)
