---
title: Retention policies in Microsoft Teams 
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: prvijay
description: Learn about retention policies and how to create and manage them in Teams.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Retention policies in Microsoft Teams

By default, Teams chat, channel, and files data are retained forever. Teams conversations are persistent and retained forever by default. As an admin, you can set up retention policies for Teams chat and channel messages and decide proactively whether to retain the data, delete it, or retain and then delete it. You can apply a Teams retention policy to your entire organization or to specific users and teams.

Use retention policies to retain data for compliance for a specific period of time or delete data if it's considered a liability after a specific period of time. Teams retention policies ensure that when you delete data, it's permanently removed from all storage locations on the Teams service.

You create and manage retention policies in the [Office 365 Security & Compliance Center](https://protection.office.com/) or by using the Security & Compliance Center PowerShell cmdlets.

The minimum licensing requirement for retention policies is Office 365 E3. To learn more about licensing, see [Office 365 licensing for Teams](Office-365-licensing.md).

> [!NOTE]
> We don’t yet support configuration for retention of private channel messages. Retention of files shared in private channels is supported.

## What are retention policies for Teams?

Managing content commonly requires two actions, retaining data so that it can't be permanently deleted before the end of the retention period and deleting data permanently at the end of the retention period.

- **Retain data**: Use a retention policy to ensure that your data is retained for the specified duration, regardless of what happens in the user app. Data is retained for compliance reasons and available for eDiscovery until the retention period expires, after which you can choose to do nothing or permanently delete the data. For example, in Teams, if you create a policy to retain Teams channel messages for 7 years, the messages are retained for eDiscovery for 7 years, even if users delete their Teams messages.
- **Delete data**: Use a retention policy to delete data to ensure that it's not a liability for your organization. After the retention period expires, data is permanently deleted from all storage locations in Teams.

With retention policies for Teams, you can choose to:

- Retain Teams chats and/or channel messages for a specified duration and then do nothing. 
- Retain Teams chats and/or channel messages for a specified duration and then delete the data.
- Delete Teams chats and/or channel messages after a specified duration.

When data is subject to a retention policy, users can continue to work with it as if nothing's changed because the data is retained in place, in its original location. If a user edits or deletes data that's subject to the policy, a copy is saved to a secure location where it's retained while the policy is in effect.

### How Teams retention policies work

Teams chats are stored in a hidden SubstrateHolds folder in the mailbox of each user in the chat, and Teams channel messages are stored in a similar SubstratesHolds hidden folder in the group mailbox for a team. Teams uses an Azure-powered chat service that also stores this data, and by default this service stores the data forever. Teams retention policies permanently delete data from the Exchange mailboxes and the underlying chat service.

When you apply a retention policy to Teams chats and channel messages, here's what happens:

- If a chat or channel message is edited or deleted by a user during the retention period, the message is copied (if it was edited) or moved (if it was deleted) to the SubstrateHolds folder and stored there until the retention period expires. If the retention policy is configured to delete data when the retention period expires, messages are permanently deleted on the day the retention period expires.
- If a chat or channel message isn't deleted by a user during the retention period, the message is moved to the SubstrateHolds folder within one day (between zero and 24 hours) after the retention expires. If the retention policy is configured to delete data when the retention period expires, the message is permanently deleted one day after it's moved to the folder.

Retention policies are retroactive. In other words, if you create a retention policy to delete data older than 90 days, Teams data created more than 90 days ago is deleted.

### Limitations

We're continuously working on optimizing retention functionality in Teams and plan to release new capabilities in the coming months. In the meantime, here's some limitations to be aware of:

- Teams requires a retention policy that's separate from other workloads. In other words, you have to create specific retention policies for Teams chats and/or channel messages. For this reason, you can't include Teams in org-wide retention policies.

- Private channel messages aren't supported. At this time, retention policies for Teams only apply to standard channel messages.

- Teams doesn't support advanced retention settings, such as the ability to apply a policy to only content that contains keywords or sensitive information. Currently, retention policies in Teams apply to all chat and/or channel message content.

## Why and when to use retention policies for Teams

In many cases, organizations consider private chat data as more of a liability than channel messages, which are typically more project-related conversations.

You can set up a separate retention policies for private chats (1:1 or 1:many chats) and channel messages. You can also configure unique policies that apply to specific users or teams in your organization. For Teams chats, you can select which users the policy applies to. For Teams channel messages, you can select which teams the policy applies to.

For example, for channel messages, you can apply a one-year deletion policy to specific teams in your organization and apply a three-year deletion policy to all other teams.

### Retention policies for Teams files

Teams files are stored in OneDrive for Business and SharePoint Online. Therefore, to retain or delete files in Teams, you create retention policies for OneDrive for Business and SharePoint Online. If you want to apply a policy to the files of a specific team, choose the SharePoint site for the team and the OneDrive for Business accounts of team members.

It's possible that a retention policy could delete a file that's referenced in a Teams chat or channel message before those messages get deleted. In this scenario, the file will still show up in the Teams message, but when users click the file, they'll get a "File not found" error. This can also happen in the absence of a policy, if someone manually deletes a file from SharePoint Online or OneDrive for Business.

### Skype for Business Online and Teams interop chats

When the Skype for Business Online chat comes into Teams, it becomes a message in a Teams chat thread and gets ingested into the appropriate mailbox. The same flow works – Teams deletion policies will delete these messages from the Teams thread. However, if conversation history is turned on for Skype for Business Online and from the Skype for Business Online client side those are being saved into a mailbox, that chat data isn't handled by a Teams retention policy.

### Multiple retention policies with different retention periods

If you set up multiple Teams retention policies with varying durations, the [principles of retention policies](https://docs.microsoft.com/en-us/microsoft-365/compliance/retention-policies#the-principles-of-retention-or-what-takes-precedence) apply. Here's an overview of what takes precedence:

- Preservation always wins over deletion
- Longest preservation period always wins
- Explicit inclusion wins over implicit inclusion in terms of locations
- Shortest deletion period wins

## Manage retention policies for Teams

### Using the Security & Compliance Center

#### Create a retention policy

To create a retention policy for Teams chats and channel messages, do the following:

1. In the left navigation of the Security & Compliance Center, go to **Information governance** > **Retention**.
2. Select **Create**.
3. On the **Name your policy** page, enter a name and description for your policy, and then click **Next**.
4. On the **Settings** page, specify whether you want to retain data, delete it, or both, the retention period, and then click **Next**.
5. On the **Choose locations** page, do the following, and then click **Next**:

    - To apply the policy to channel messages, turn on **Teams channel messages**.  If you want to apply the policy to specific teams in your organization, select **Choose teams**, and then select the teams that you want.
    - To apply the policy to chats, turn on **Teams chats**. If you want to apply the policy to specific users in your organization, select **Choose users**, and then select the users that you want.
      > [!NOTE]
      > When you turn on **Teams channel messages** and/or **Teams chats**, all other locations are  automatically turned off. A Teams retention policy can only include Teams locations.

        ![Screenshot of the Teams channel messages and Teams chats options on the Choose locations page](media/retention-policies-create.png)

      > [!IMPORTANT]
      > Teams chats and channel messages aren't affected by retention policies applied to user or group mailboxes in the **Exchange email** or **Office 365 groups** locations. Even though Teams chats and channel messages are stored in Exchange, they're only affected by retention policies applied to the Teams locations. A Teams retention policy permanently deletes Teams data from all storage locations on the Teams service.

6. Review your settings, and then when you're ready, select **Create this policy**.

#### Edit a retention policy

To edit a Teams retention policy, do the following:

1. In the left navigation of the Security & Compliance Center, go to **Information governance** > **Retention**.
2. In the list of retention policies, select the check box next to the retention policy you want to edit.
3. Select **Edit** next to what you want to edit, make your changes, click **Save**, and then click **Close**.

    ![Screenshot of the Teams channel messages and Teams chats options on the Choose locations page](media/retention-policies-edit.png)

#### Delete a retention policy

To delete a Teams retention policy, do the following:

1. In the left navigation of the Security & Compliance Center, go to **Information governance** > **Retention**.
2. In the list of retention policies, select the check box next to the retention policy you want to delete.
3. Select **Delete policy**.

### Using PowerShell

To create and manage Teams retention policies by using PowerShell, use the following cmdlets.

|Policy|Rule|
|---|---|
|[New-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancepolicy?view=exchange-ps)| [New-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancerule?view=exchange-ps)|
|[Get-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-teamsretentioncompliancepolicy?view=exchange-ps)| [Get-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-teamsretentioncompliancerule?view=exchange-ps)|
|[Set-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-teamsretentioncompliancepolicy?view=exchange-ps)| [Set-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-teamsretentioncompliancerule?view=exchange-ps)|
|[Remove-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-teamsretentioncompliancepolicy?view=exchange-ps)| [Remove-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-teamsretentioncompliancerule?view=exchange-ps)|

## Related topics

- [Overview of retention policies](https://support.office.com/article/overview-of-retention-policies-5e377752-700d-4870-9b6d-12bfc12d2423)
