---
title: Manage Q&A in Teams meetings and events
author: wlibebe
ms.author: wlibebe
ms.reviewer: sameer.sitaram
ms.date: 1/17/2024
manager: pamgreen
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.localizationpriority: medium
ms.collection: 
  - Tier2
  - m365initiative-meetings
audience: Admin
appliesto: 
  - Microsoft Teams
description: Learn about how IT Admins can set up, use, and manage Q&A in Q&A for Teams meetings, webinars, and town halls. Learn about Q&A, a structured approach to gathering questions snd organizing discussions. Learn how to delete individual Q&A   messages. Learn about using available languages for Q&A. Understand the data lifecycle and data retention and deletion policies for Q&A.
---
# Manage Q&A in Teams meetings and events

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

Q&A allows presenters, organizers, and co-organizers to take questions from attendees and answer them in real time. This feature is best suited for large, structured meetings and events– like town halls, webinars, all Hands, and trainings. Q&A is a per-organizer setting.

Your organization might have requirements to limit which organizers can use Q&A. As an admin, you can control whether an organizer can enable Q&A in their meetings and events.

To learn more about Q&A for your users, see [Q&A in Microsoft Teams meetings](https://support.microsoft.com/office/q-a-in-microsoft-teams-meetings-f3c84c72-57c3-4b6d-aea5-67b11face787).

## Prerequisites

- Verify that you haven’t blocked access to [Viva Engage’s IPs and URLs.](/microsoft-365/enterprise/urls-and-ip-address-ranges)
- To allow users in your organization to add Q&A to Teams meetings and events, you must confirm that sign-ins for the Office 365 Viva Engage service are enabled in Microsoft Entra ID.
Follow these steps to confirm that sign-ins are enabled:
  - Go to the **Microsoft Entra admin center** > **All services** > **Enterprise Applications** > **Office 365 Viva Engage** > **Properties**.
  - For the **Enabled for users to sign-in?** option, select **Yes** if necessary.

When you enable Q&A, organizers can turn on Q&A in their Meeting options when creating or updating meetings and events. Through Teams and Outlook meeting options, organizers can also remove Q&A from meetings where it was previously added to prevent attendees from using the feature.

## Manage Q&A

### Teams admin center

Follow these steps to control which organizers can use Q&A in their meetings and events:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Meeting Engagement** section and toggle **Q&A** **On** or **Off**.
6. Select **Save**.
7. Assign the policy to specific Microsoft 365 groups, users, or subscriptions that you want to allow or prevent from setting up Q&A.

### PowerShell

To manage whether organizers can use Q&A in their meetings and events, use the **`-QnAEngagementMode`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet.

To allow organizers with this policy to use Q&A in meetings and events they create, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -QnAEngagementMode Enabled
```

To prevent organizers with this policy from using Q&A in meetings and events they create, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -QnAEngagementMode Disabled
```

## Delete an individual message from Q&A in Teams

To delete a question or answer posted in the Q&A application, follow these steps:

1. Sign in to the Exchange Admin Center as a Global Administrator.
2. Go to **Recipients** > **Mailboxes** and search by name for the user who organized the meeting or event.
3. Select the organizer and select **Manage mailbox delegation**. In the **Read and manage** section, select **Edit** > **Add permissions**.
4. Add yourself as a delegate of the meeting organizer and select **Save**.
5. Open Outlook Calendar in the Outlook Web App (not desktop) and select **Add calendar** and then **Add from directory**.
6. Search for the meeting organizer and add their calendar to **My calendars**. Meetings for the selected user are now shown on your calendar.
7. In your calendar, find the meeting you want to delete content for, open the meeting record, and select **Chat with participants**. Selecting chat with participants opens the meeting chat in Teams.
8. Navigate to the **Q&A** application in the Teams app bar.
9. Find any questions or answers you want to delete and select **Delete**.
10. Once you’re finished deleting content, go back to the Exchange Admin Center and remove yourself as a delegate of the meeting organizer.

If you delete a question before removing the answers, the first answer to the question becomes the question. To avoid this scenario, follow these steps in order:

1. Identify the question you’d like to delete
2. Delete the answers to the question
3. Delete the question

## Available languages for Viva Engage vs Teams

Q&A defaults to the user’s language for Teams. When there’s a difference in the languages available for Teams versus Viva Engage, the following language defaults occur:

- **Nearest Primary Language**—Viva Engage defaults to the nearest primary language, if available. For example, Viva Engage doesn’t have a French Canadian (fr-CA) version, so it displays content in French (fr-FR) instead.
- **Unsupported Language**—If Viva engage doesn't support the language at all, Viva Engage defaults to US English (en-US).

## eDiscovery

eDiscovery for Q&A works the same as eDiscovery for any other Viva Engage content.

- If you use Q&A in your tenant’s Teams application, this content is available in eDiscovery regardless of the configuration or existence of your Viva Engage network. To use eDiscovery for standard Viva Engage content, your Viva Engage network needs to be in [Native Mode](/viva/engage/overview-native-mode).
- When you perform eDiscovery, you can determine whether messages were generated in Viva Engage or through Q&A in Teams. In the File Metadata section, you can find that information in the Item Class field.
- If your organization uses the Q&A, powered by Viva Engage, the content Q&A generates is considered Viva Engage content and is discoverable. For more information about eDiscovery in Microsoft 365 apps, see [eDiscovery solutions in Microsoft 365.](/microsoft-365/compliance/ediscovery)
- If the meeting organizer enables anonymous posting, the questions attendees post are ingested into the organizer’s mailbox for eDiscovery.

## Data Storage

Q&A messages created as part of the meeting are stored as Viva Engage messages. These messages are stored in Viva Engage and ingested for eDiscovery.
Files are always stored in SharePoint, which handles all the data rest policies and locations.

The following guidance explains how messaging data is stored:

- Q&A content is searchable via eDiscovery at the user level.
- Message data (which includes message content) is stored in North America or EU by default (depending on your Viva Engage network location).
- For orgs that don’t have an existing Viva Engage network, the Q&A Viva Engage network is created in the United States Viva Engage region. Your organization's messages for Q&A are always stored in the US.
- Similar to OneNote tabs, removing the Q&A from a meeting doesn't delete the meeting data. Removing Q&A from the meeting only removes access to the data from the meeting. If you add the Q&A tab back, you can see the meeting conversations again.

## GDPR for Q&A in Teams

When you complete a Data Subject Request through the Microsoft 365 Admin Center, it automatically removes users’ contact information from all their content in the Q&A.

## Data lifecycle for Q&A in Teams

The lifecycle of data generated by Q&A in Teams depends on your Viva Engage Data Retention settings in the Microsoft Purview compliance portal. If you hard delete all users in the meeting who received a copy of the Q&A messages in their substrate shard via Microsoft Entra ID, Viva Engage deletes its copy of the Q&A content for that meeting within 30 days of user deletion.

## Retention and deletion

Retention of content follows the retention policies set for Viva Engage – regardless of whether you have different policies set for Viva Engage and Teams.

> [!NOTE]
> If your Viva Engage Network isn't in Native Mode, the policies created here apply only to Q&A data. In Native Mode, all Viva Engage users are in Microsoft Entra ID, all groups are Microsoft 365 groups, and all files are stored in SharePoint Online.

## Related topics

- [Plan for meetings](plan-meetings.md)
- [Plan for webinars](plan-webinars.md)
- [Plan for town halls](plan-town-halls.md)
