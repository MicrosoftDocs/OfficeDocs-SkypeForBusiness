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

Retention policies and retention labels from Microsoft 365 helps you to more effectively manage the information in your organization. You configure retention settings to keep data that's needed to comply with your organization's internal policies, industry regulations, or legal needs, and to delete data that's considered a liability, that you're no longer required to keep, or has no legal or business value.

Teams supports retention policies for chat and channel messages so that as an admin, you can decide proactively whether to retain this data, delete it, or retain it for a specific period of time and then delete it. You can apply a Teams retention policy to your entire organization or to specific users and teams. 

To learn more about retention and how you can apply retention settings to other workloads in Microsoft 365, see [Learn about retention policies and retention labels](https://docs.microsoft.com/microsoft-365/compliance/retention).

The minimum licensing requirement for retention policies for Teams is Microsoft 365 E3. To learn more about licensing, see [Microsoft Teams service description](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description).

## How Teams retention policies work

For detailed information what's included and excluded for Teams retention policies, and how these policies work depending on your policy configuration, see [Learn about retention for Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/retention-policies-teams).

> [!NOTE]
> That page explains why you might sometimes see delays when retention policies delete messages. For example, messages can be visible up to 7 days after the expiration period you've configured in the retention policy.

If you set up multiple Teams retention policies with different retention settings, the [principles of retention](https://docs.microsoft.com/microsoft-365/compliance/retention#the-principles-of-retention-or-what-takes-precedence) apply. Here's an overview of what takes precedence:

- Retention always wins over deletion
- Longest retention period always wins
- Explicit inclusion wins over implicit inclusion for specified locations
- Shortest deletion period wins

## When to use retention policies for Teams

In many cases, organizations consider private chat data as more of a liability than channel messages, which are typically more project-related conversations.

You can set up separate retention policies for private chats (1:1 or 1:many chats) and channel messages. You can also configure unique policies that apply to specific users or teams in your organization. For Teams chats, you can select which users the policy applies to. For Teams channel messages, you can select which teams the policy applies to.

For example, for channel messages, you can apply a one-year deletion policy to specific teams in your organization and apply a three-year deletion policy to all other teams.

## Create and manage retention policies for Teams

To create a retention policy for Teams chats and channel messages, use the instructions from [Retention policy for Teams locations] (https://docs.microsoft.com/microsoft-365/compliance/create-retention-policies#retention-policy-for-teams-locations). That page has additional information about creating and managing retention policies for other workloads in Microsoft 365. For example, you might want to also create a retention policy for Microsoft 365 Groups to retain and delete files that accessed in Teams and stored in OneDrive and SharePoint.  

## End user experience

For private chats (1:1 chats) or group chats, the end users will see that chats older than the retention policy configuration are deleted and a control message stating "We've deleted older messages due to your org's retention policy" is shown on top of yet undeleted messages.
:::image type="content" source="media/retention-policies-image1.png" alt-text="Screenshot of chat retention":::


:::image type="content" source="media/retention-policies-image2.png" alt-text="Screenshot of group chat retention":::

For Channel messages, the end users (channel members) will see the deleted messages disappear from view after messages expire. If the deleted message was a parent message of a threaded conversation, then, in place of parent message, a message stating "This message has been deleted because of a Retention Policy" will be displayed.

:::image type="content" source="media/retention-policies-image3.png" alt-text="Screenshot of channel before retention":::

:::image type="content" source="media/retention-policies-image4.png" alt-text="Screenshot of channel after retention":::

> [!NOTE]
> End user messaging is not user or admin modifiable at this time.


## Related topics

- [Get started with retention policies and retention labels](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-retention)
