---
title: Communication compliance with Microsoft Teams
author: robmazz
ms.author: robmazz
manager: laurawi
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: anwara
description: Learning about communication compliance, part of the insider risk solution set, from the Microsoft Teams perspective (this is part of the M365 communication compliance functionality).
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Communication compliance with Microsoft Teams

Communication compliance is an insider risk solution in Microsoft 365 that helps minimize communication risks by helping you detect, capture, and act on inappropriate messages in your organization.

For Microsoft Teams, communication compliance helps identify the [following types](/microsoft-365/compliance/communication-compliance-feature-reference) of inappropriate content in Teams channels or in 1:1 and group chats:

- Offensive, profane, and harassing language
- Adult, racy, and gory images
- Sharing of sensitive information

For more information on communication compliance and how to configure policies for your organization, see [Communication compliance in Microsoft 365](/microsoft-365/compliance/communication-compliance).

## How to use communication compliance in Microsoft Teams

Communication compliance and Microsoft Teams are tightly integrated and can help minimize communication risks in your organization. After you've configured your first communication compliance policies, you can actively manage inappropriate Microsoft Teams messages and content that is automatically flagged in alerts.

### Getting started

Getting started with communication compliance in Microsoft Teams begins with [planning](/microsoft-365/compliance/communication-compliance-plan) and creating pre-defined or custom policies to identify inappropriate user activities in Teams channels or in 1:1 and groups. Keep in mind that you'll need to [configure](/microsoft-365/compliance/communication-compliance-configure) some permissions and basic prerequisites as part of the configuration process.

Teams administrators can configure communication compliance policies at the following levels:

- **User level**: Policies at this level apply to an individual Teams user or may be applied to all Teams users in your organization. These policies cover messages that these users may send in 1:1 or group chats. Chat communications for the users are automatically monitored across all Microsoft Teams where the users are a member.
- **Teams level**: Policies at this level apply to a Microsoft Team channel. These policies cover messages sent in the Teams channel only.

### Act on inappropriate messages in Microsoft Teams

After you have configured your policies and have received communication compliance alerts for Microsoft Teams messages, it's time for compliance reviewers in your organization to take action on these messages. Reviewers can help safeguard your organization by reviewing communication compliance alerts and removing flagged messages from view in Microsoft Teams.

![Remove a message in Teams](./media/communication-compliance-remove-teams-message.png)

Removed messages and content are replaced with notifications for viewers explaining that the message or content has been removed and what policy is applicable to the removal. The sender of the removed message or content is also notified of the removal status and provided with original message content for context relating to its removal. The sender can also view the specific policy condition that applies to the message removal.

Example of policy tip seen by sender:

![Policy tip for sender](./media/communication-compliance-warning-1.png)

Example of policy condition notification seen by the sender:

![Policy condition info for sender](./media/communication-compliance-warning-2.png)

Example of policy tip seen by recipient:

![Policy tip for recipient](./media/communication-compliance-warning-3.png)