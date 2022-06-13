---
title: "Manage Q&A in Teams Meetings"
author: wlibebe
ms.author: wlibebe
ms.reviewer: justle
manager: serdars
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Microsoft Teams

description: Learn about how IT Admins can set up, use, and manage Q&A in Teams Q&A for a structured approach to gathering questions, organizing discussions, deleting individual messages, using available languages, and understanding the data lifecycle as well as data retention and deletion policies.
---
# Manage Q&A in Teams Meetings

Q&A is an integrated meeting experience that gives participants the ability to formally ask and receive answers questions, as well as engage in discussion posts. This experience is a best practice for meetings with more than 10 participants.

This article describes how to manage Q&A and user-level policies which dictate whether an organizer can enable Teams Q&A in their meetings.

> [!NOTE]
> This feature is currently in private preview and not publicly accessible. If you'd like to participate in the private preview program, sign up [here](https://m365crmedu.powerappsportals.com/LMSSignup/)


## Prerequisites

- Verify that you haven’t blocked access to [Yammer’s IPs and URLs.](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide)
- To allow users in your organization to add Q&A to Teams meetings, you need to confirm that sign-ins for the Office 365 Yammer service are enabled in Azure Active Directory
  - Go to the **Azure AD admin center** > **All services** > **Enterprise Applications** > **Office 365 Yammer** > **Properties**.
  - For the **Enabled for users to sign-in?** option, select **Yes** if required.

## Who can use Q&A

Q&A can be used by the following user types:

- Regular user —A user with Microsoft 365 credentials in your tenant.
- Federated user —A user with Microsoft 365 credentials to a different tenant.
- Guest user —Any guests you add to your Microsoft Teams, SharePoint, or Azure Active Directory.

> [!NOTE]
> Q&A does not support anonymous users at this time.

When admins enable Q&A, users with the organizer role can turn on Q&A when creating or updating meetings. Through Teams and Outlook meeting options, organizers can also remove Q&A from meetings where it was previously added to stop attendees from using the feature.

## Use the Teams admin center to manage Q&A

> [!NOTE]
> Managing Q&A in the admin center is not available in Public Preview. Use PowerShell to set up and manage Q&A for your users.

Your organization might have requirements to limit which organizers can turn on Q&A. You can use the Teams admin center to manage which organizers can turn on Q&A in large meetings. 
Follow these steps to control which organizers can use Q&A:

1. In the Teams admin center, go to **Meetings** > [**Meeting Policies**](/meeting-policies-participants-and-guests)
2. Select an existing policy or create a new one and give it a name such as “No Q&A for these organizers”
3. Scroll to the section called **“Participants & Guests”**, select disable for the **“Question & Answer experience”** setting, and save the policy
4. Assign the policy to specific M365 Groups, end-users, or subscriptions that you want to prevent from setting up Q&A

## Use PowerShell to manage Q&A

Your organization might have requirements to limit which organizers can turn on Q&A. You can use PowerShell to manage which organizers can turn on Q&A in large meetings.

Example PowerShell command to Enable Q&A:

```PowerShell
Set-CsTeamsMeetingPolicy  -Identity Global -QnAEngagementMode Enabled
```

## Delete an individual message from Q&A in Teams

To delete a question or answer posted in the Q&A application, follow these steps:

1. Log into the Exchange Admin Center as a Global Administrator.
2. Go to **Recipients** > **Mailboxes** and search by name for the user who organized the meeting.
3. Select the meeting organizer and click on **Manage mailbox delegation**. In the **Read and manage** section, select **Edit** > **Add permissions**.
4. Add yourself as a delegate of the meeting organizer and select Save.
5. Open Outlook Calendar in the Outlook Web App (not desktop) and select **Add calendar** and then **Add from directory**.
6. Search for the meeting organizer and add their calendar to **My calendars**. Meetings for the selected user will now be shown on your calendar.
7. In your calendar, find the meeting you want to delete content for, open the meeting record, and select **Chat with participants**. This will open the meeting chat in Teams.
8. Navigate to the Q&A application in the Teams app bar.
9. Find any questions or answers you want to delete and select Delete.
10. Once you’re finished deleting content, go back to the Exchange Admin Center and remove yourself as a delegate of the meeting organizer.

> [!NOTE]
> If you delete a question before removing the answers, the first answer to the question will become the question.
>
> To avoid this, follow these steps in order:
>
> 1. Identify the question you’d like to delete
> 2. Delete the answers to the question
> 3. Delete the question

## Available languages for Yammer versus Teams

The Q&A will default to the user’s language for Teams. When there’s a difference in the languages available for Teams versus Yammer, the following will occur for language:
- Nearest Primary Language—Yammer will default to the nearest primary language, if available. For example, Yammer doesn’t provide a French Canadian (fr-CA) version, so it will display content in French (fr-FR) instead.
- Unsupported Language—If the language is not provided by Yammer at all, Yammer will default to US English (en-US).

## eDiscovery

eDiscovery for Q&A in Teams, powered by Yammer, will work the same as eDiscovery for any other Yammer content.

- If you use  Teams Q&A in your tenant’s Teams application, this content will be available in eDiscovery regardless of the configuration or existence of your Yammer network. To use eDiscovery for standard Yammer content, your Yammer network needs to be in [Native Mode](/yammer/configure-your-yammer-network/overview-native-mode).
- When you perform eDiscovery, you can determine whether messages were generated in Yammer or through Q&A in Teams. In the File Metadata section, you can find that information in the Item Class field.
- If your organization uses the Teams Q&A, powered by Yammer, the content generated by Q&A is considered Yammer content and will be discoverable. For more information about eDiscovery in Microsoft 365 apps, see [eDiscovery solutions in Microsoft 365.](/microsoft-365/compliance/ediscovery?view=o365-worldwide)

## Data Storage

Q&A messages created as part of the meeting are stored as Yammer messages. These messages are stored in Yammer and ingested for eDiscovery.
Files are always stored in SharePoint, which handles all the data rest policies and locations.

The following explains how messaging data is stored:

- Q&A content is searchable via eDiscovery and Advanced eDiscovery at the user level.
- Message data (which includes message content) will be stored in North America or EU by default (depending on the customer’s Yammer network location).
- For tenants that don’t have an existing Yammer network, the Q&A Yammer network will be created in the United States Yammer region. Your organization's messages for Q&A will always be stored in the US.
- Like OneNote tabs, removing the Q&A from a meeting does not delete the meeting data. Removing Q&A from the meeting only removes access to the data from the meeting. If you add the Q&A tab back, you will see all the meeting conversations again.

## GDPR for Q&A in Teams

When you complete a Data Subject Request through the Microsoft 365 Admin Center, it automatically removes users’ contact information from all their content in the Q&A.

## Data lifecycle for Q&A in Teams

The lifecycle of data generated by Q&A in Teams is determined by your Yammer Data Retention settings in the Compliance Center. If all users in the meeting who received a copy of the Q&A messages in their substrate shard are hard deleted from Azure Active Directory, Yammer will delete its copy of the Q&A content for that meeting within 30 days of all users being deleted.

## Retention and deletion

Retention of content follows the retention policies set for Yammer – regardless of whether you have different policies set for Yammer and Teams.

> [!NOTE]
> If your Yammer Network is not in Native Mode, the policies created here will apply only to Teams Q&A data. In Native Mode, all Yammer users are in Azure Active Directory (Azure AD), all groups are Microsoft 365 groups, and all files are stored in SharePoint Online.

## FAQ

**Q: How do I export Q&A content?**

**A:** Q&A content is stored in the Microsoft 365 compliance center and accessed through eDiscovery. Future iterations will include a meeting highlights report and export functionality for meeting organizers.

**Q: Does Q&A support Microsoft 365 Multi-Geo capabilities?**

**A:** Q&A does not currently support Microsoft 365 Multi-Geo capabilities. Q&A data will be stored in North America or EU by default (depending on the customer’s Yammer network location).

**Q: Where can I learn more about structured meetings?**

**A:** Follow these best practices for hosting successful large meetings in Microsoft Teams.
