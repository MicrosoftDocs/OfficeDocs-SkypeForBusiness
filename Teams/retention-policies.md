---
title: Retention policies in Microsoft Teams 
author: cabailey
ms.author: cabailey
ms.reviewer: 
  - anwara 
  - prvijay
manager: laurawi
ms.topic: conceptual
ms.service: msteams
audience: admin
description: Use retention policies for Microsoft Teams to keep messages that are needed to comply with  internal policies, industry regulations, or legal needs, and to delete messages that are considered a liability or has no legal business value.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Retention policies in Microsoft Teams

Retention policies and retention labels from Microsoft 365 help you to more effectively manage the information in your organization. You can configure retention settings to keep data that's needed to comply with your organization's internal policies, industry regulations, or legal needs. You can also configure retention settings to delete data that's considered a liability, that you're no longer required to keep, or that has no legal or business value.

Teams supports retention policies for chat and channel messages so that as an admin, you can decide proactively whether to retain this data, delete it, or retain it for a specific period of time and then delete it. You can apply a Teams retention policy to your entire organization or to specific users and teams. Retention labels aren't supported for Teams.

To learn more about retention, and how you can apply retention settings by using retention policies or retention labels for other workloads in Microsoft 365, see [Learn about retention policies and retention labels](https://docs.microsoft.com/microsoft-365/compliance/retention).

The minimum licensing requirement for retention policies for Teams is Microsoft 365 E3. To learn more about licensing, see [Microsoft Teams service description](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description).

## How Teams retention policies work

Teams chat messages are stored in a hidden folder in the mailbox of each user included in the chat, and Teams channel messages are stored in a similar hidden folder in the group mailbox for the team. To retain messages that are subject to a retention policy, a copy of the content is automatically kept in a hidden folder named **SubstrateHolds** as a subfolder in the Exchange **Recoverable Items** folder. Until these messages are permanently deleted from the SubstrateHolds folder, they remain searchable by eDiscovery tools.

For detailed information about what's included and excluded for Teams retention policies, and how these policies work depending on your policy configuration, see [Learn about retention for Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams).

> [!NOTE]
> That page explains why you might sometimes see delays when retention policies delete messages. For example, messages can be visible up to 7 days after the expiration period you've configured in the retention policy.

If you set up multiple Teams retention policies with different retention settings, the principles of retention resolve any conflicts. For example:
- If there is a conflict between retaining or deleting the same content, the content is always retained.
- If there is a conflict in how long to retain the same content, it is retained for the longest retention period.

These two principles of retention address most conflicts that might arise when you have multiple retention policies for Teams, but for more information, see [The principles of retention, or what takes precedence?](https://docs.microsoft.com/microsoft-365/compliance/retention#the-principles-of-retention-or-what-takes-precedence)

## When to use retention policies for Teams

In many cases, organizations consider private chat data as more of a liability than channel messages, which are typically more project-related conversations.

You can set up separate retention policies for private chats (1:1 or 1:many chats) and channel messages. You can also configure unique policies that apply to specific users or teams in your organization. For Teams chats, you can select which users the policy applies to. For Teams channel messages, you can select which teams the policy applies to.

For example, for channel messages, you can apply a one-year deletion policy to specific teams in your organization and apply a three-year deletion policy to all other teams.

## Create and manage retention policies for Teams

To create a retention policy for Teams chats and channel messages, use the instructions from [Retention policy for Teams locations](https://docs.microsoft.com/microsoft-365/compliance/create-retention-policies#retention-policy-for-teams-locations).

That page has additional information about creating and managing retention policies for other workloads in Microsoft 365. For example, you might want to also create a retention policy for Microsoft 365 Groups to retain and delete files that are accessed in Teams and stored in OneDrive or SharePoint.  

## Retention of edited messages

Retention on Teams messages works on the timestamp of the creation of the original message. As an example, let's look at a scenario where there is a 30-day deletion policy on Teams chat or channel messages and a user sends a message (“original message”) on day 1, then later modifies it to an “edited message” on day 15.

Here, the original message will be copied to a temporary location in the backend storage and deleted within 21 days. If there is Legal hold (via eDiscovery portal) or Retention hold in place on the user, then all versions of original, deleted and edited messages are stored as long as the hold policy is active.

The “edited message” would be deleted by the retention policy on Day-30 i.e. based on the timestamp on the original message.

## End user experience

For private chats (1:1 chats) or group chats, the end users will see that chats older than the retention policy configuration are deleted and a control message stating "We've deleted older messages due to your org's retention policy" is shown on top of yet undeleted messages.

:::image type="content" source="media/retention-policies-image1.png" alt-text="User informed in Teams that chat message are deleted because of a Teams retention policy":::


:::image type="content" source="media/retention-policies-image2.png" alt-text="User in Teams explaining messages are deleted as a result of a Teams retention policy":::

For Channel messages, the end users (channel members) will see the deleted messages disappear from view after messages expire. If the deleted message was a parent message of a threaded conversation, then, in place of parent message, a message stating "This message has been deleted because of a Retention Policy" will be displayed.

:::image type="content" source="media/retention-policies-image3.png" alt-text="Screenshot of channel before retention":::

:::image type="content" source="media/retention-policies-image4.png" alt-text="Screenshot of channel after retention":::

> [!NOTE]
> The displayed messages that end users see as a result of deleted messaging are not configurable at this time.


## Related topics

- [Get started with retention policies and retention labels](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-retention)
- [Learn about retention for Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams)
- [Create and configure retention policies](https://docs.microsoft.com/microsoft-365/compliance/create-retention-policies)
