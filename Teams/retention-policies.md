---
title: Manage retention policies for Microsoft Teams 
author: cabailey
ms.author: cabailey
ms.reviewer: 
  - anwara 
  - prvijay
manager: laurawi
ms.topic: conceptual
ms.service: msteams
audience: admin
description: Use retention policies for Microsoft Teams to keep messages that your organization needs to comply with internal policies, industry regulations, or legal requirements, and to delete messages that are considered a liability or has no legal business value.
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Manage retention policies for Microsoft Teams

> [!NOTE]
> If you are seeing a message in Teams that your chats or messages have been deleted by a retention policy, see [Teams messages about retention policies](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> The information on this page is for IT administrators who manage these retention policies.

Retention policies and retention labels from Microsoft 365 help you to more effectively manage the information in your organization. You can configure retention settings to keep data that's needed to comply with your organization's internal policies, industry regulations, or legal requirements. You can also configure retention settings to delete data that's considered a liability, that you're no longer required to keep, or that has no legal or business value.

Teams supports retention policies for chat and channel messages so that as an admin, you can decide proactively whether to retain this data, delete it, or retain it for a specific period of time and then delete it. The start of the retention period for these actions is always based on when a message is created. You can apply a Teams retention policy to your entire organization or to specific users and teams. Retention labels aren't supported for Teams.

> [!NOTE]
> [Shared channels](shared-channels.md) are supported by retention policies.

To learn more about retention solutions in Microsoft 365, see [Learn about retention policies and retention labels](/microsoft-365/compliance/retention).

Users who are subject to a retention policy for Teams must have an appropriate license, such as Office 365 E3 or Office 365 A3. For other licensing options for these retention policies, see the [Information Governance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) section from [Microsoft 365 licensing guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance). To learn more about licensing for Teams, see [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description).

## How Teams retention policies support retain and delete actions

If you configure a Teams retention policy to retain chats or channel messages, users can still edit and delete their messages in their Teams app. Although users no longer see their pre-edited or deleted messages in Teams, data from these messages is stored in a secured location that's designed for eDiscovery searches by compliance administrators. Permanent deletion of this data doesn't happen before the end of the configured retention period, or if another retention policy is configured to retain this data, or it is subject to an [eDiscovery hold](/microsoft-365/compliance/retention#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds).

When a retention policy is configured to delete chats and channel messages, these messages become eligible for automatic deletion. If the messages are still displayed in the Teams app, they will disappear from there and [users are informed that a retention policy has deleted these messages](#end-user-experience). If the messages were previously subject to a retain action and have been edited or deleted by users, these messages will now be deleted from the secured location and no longer returned in eDiscovery searches.

For detailed information about how these policies work depending on your policy configuration and user actions, and what message data is included and excluded for Teams retention policies, see [Learn about retention for Microsoft Teams](/microsoft-365/compliance/retention-policies-teams). That page also explains why you might sometimes experience delays when retention policies delete messages. For example, messages can be visible to users in the Teams app up to 7 days after the expiration period you've configured in the retention policy.

If you set up multiple Teams retention policies with different retention settings, the principles of retention resolve any conflicts. For example:

- If there is a conflict between retaining or deleting the same content, the content is always retained in the secured location so that it remains searchable with eDiscovery for compliance administrators.
    
    This principle also applies to messages that are under eDiscovery holds for legal or investigative reasons.

- If there is a conflict in how long to retain the same content, it is retained in the secured location for the longest retention period.

These two principles of retention address most conflicts that might arise when you have multiple retention policies for Teams, but for more information, see [The principles of retention, or what takes precedence?](/microsoft-365/compliance/retention#the-principles-of-retention-or-what-takes-precedence)

## When to use retention policies for Teams

In many cases, organizations consider private chat data as more of a liability than channel messages, which are typically more project-related conversations.

You can very efficiently configure a single retention policy for all Teams messages. Or, for more fine-grained control, you can:

- Have separate retention policies for private chats (1:1 or 1:many chats), messages from standard channels, or messages from private channels.

- Apply the policies only to specific users or teams in your organization. For Teams chats and private channels, you can select which users the policy applies to. For Teams channel messages, you can select which teams the policy applies to.

For example, for standard channel messages: Create a retention policy for specific teams in your organization and configure that policy with a delete action after 1 year. Then create another retention policy for standard channel messages for all other teams and configure that policy with a delete action after 3 years.

## Create and manage retention policies for Teams

To create or edit a retention policy for Teams messages, use the instructions from [Retention policy for Teams locations](/microsoft-365/compliance/create-retention-policies#retention-policy-for-teams-locations).

That page has additional information about creating and managing retention policies for other workloads in Microsoft 365. For example, you might want to also create a retention policy for Microsoft 365 Groups to retain and delete files that are accessed in Teams and stored in OneDrive or SharePoint.  

## End-user experience

For private chats (1:1 chats) or group chats, users will see that chats older than the retention policy configuration are deleted and an automatically generated message stating "We've deleted older messages due to your org's retention policy" is shown on top of yet undeleted messages. For example:

:::image type="content" source="media/retention-policies-image1.png" alt-text="User informed in Teams that chat message are deleted because of a Teams retention policy.":::


:::image type="content" source="media/retention-policies-image2.png" alt-text="User in Teams explaining messages are deleted as a result of a Teams retention policy.":::

For Channel messages, users (channel members) will see the deleted messages disappear from view after messages expire. If the deleted message was a parent message of a threaded conversation, then, in place of parent message, a message stating "This message has been deleted because of a Retention Policy" will be displayed. For example:

:::image type="content" source="media/retention-policies-image3.png" alt-text="Screenshot of channel before retention.":::

:::image type="content" source="media/retention-policies-image4.png" alt-text="Screenshot of channel after retention.":::

> [!NOTE]
> The displayed messages that users see as a result of deleted messages are not configurable at this time.

The links in these displayed messages go to [Teams messages about retention policies](https://support.microsoft.com/en-us/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b). This documentation for end users helps to answer basic questions about why their messages have been deleted. However, as part of your retention policy deployment, make sure that you communicate to users and your help desk the impact of your configured settings.

## Related topics

- [Get started with retention policies and retention labels](/microsoft-365/compliance/get-started-with-retention)
- [Learn about retention for Microsoft Teams](/microsoft-365/compliance/retention-policies-teams)
- [Create and configure retention policies](/microsoft-365/compliance/create-retention-policies)
- Troubleshooting: [Messages in the Teams and Yammer apps are unexpectedly deleted by retention policies](/microsoftteams/troubleshoot/teams-im-presence/messages-unexpectedly-deleted-retention-policy)
