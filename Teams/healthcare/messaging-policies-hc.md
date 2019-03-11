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

Messaging policies are used to control which chat and channel messaging features are available to users in Microsoft Teams, and are part of the overall deployment of Secure Messaging for Healthcare organizations like Hospitals, clinics, or doctor's offices. 

You can use the default policy or create one or more custom messaging policies for people in your organization. After you create a policy, you will assign it a user or groups of users in your organization. For example, you may choose to only allow certain job roles to use these features (perhaps doctors and nurses only) and other workers (like the janitorial or kitchen staff) to get a more limited set of features. Decide for yourself what needs your organization has, the guidance here is at most a suggestion.

Policies can be easily managed in the [Microsoft Teams admin center](http://admin.teams.microsoft.com) by logging in with administrator credentials and choosing **Messaging Policies** in the left navigation pane.

![Messaging policies in Teams](../media/messaging-policies-image1.png)

To edit the existing default Messaging policy for your organization, click the **Global (Org-wide default)** row, and then make your changes. To create a new custom messaging policy, click **New policy** and select your settings. Choose **Save** when you are done.

![Healthcare messaging policy settings](../media/hc-message-policy.png)

The following settings are of special value to Healthcare applications, and should be considered when designing a custom policy used in the Healthcare field:

- ![number one](../media/sfbcallout1.png) **Read receipts** Read receipts allows the sender of a chat message to know when their message was read by the recipient. Use this setting to specify whether read receipts are user controlled, enabled for everyone, or disabled for everyone. Message read receipts are important in Healthcare organizations because they remove uncertainly about whether a message was read.

  For Healthcare applications, choose either **User controlled** or **Enabled for everyone**.

  > [!NOTE]
  > If read receipts are used in a large group chat (with over 100 users, for example), the receipt messages can overwhelm the actual messages, and lead to chat user frustration. This is something you will need to make users aware of.

- ![number two](../media/sfbcallout2.png) **Users can send priority notifications** Use this setting to allow users to send priority chat messages to other users. This feature helps hospital staff alert one another when a critical incident requires their attention. Unlike regular “important” messages, priority notifications repeatedly notify users for a period of 20 minutes or until messages are picked up and read by the recipient, maximizing the likelihood that the message is picked up and acted upon in a timely manner.

  An admin can enable or disable the ability for users assigned this policy to send priority notifications. The default setting is disabled. The recipient of the priority message might not have the same messaging policy, and will not have an option to disable receiving priority messages. For Healthcare applications, we recommend enabling the feature for at least some groups, but you'll need to determine which ones.

## Related topics

[Full Messaging Policies article](../messaging-policies-in-teams.md)

[Get started with Teams for Healthcare organizations](teams-in-hc.md)
