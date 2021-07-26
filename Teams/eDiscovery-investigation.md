---
title: Conduct an eDiscovery investigation of content
author: markjjo
ms.author: markjjo
manager: laurawi
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - SPO_Content
ms.reviewer: anwara
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn what to do when you need to perform eDiscovery such as when you need to submit all Electronically Stored Information for legal proceedings.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Conduct an eDiscovery investigation of content in Microsoft Teams

Large Enterprises are often exposed to high penalty legal proceedings that demand submission of all Electronically Stored Information (ESI). Microsoft Teams content can be searched and used during eDiscovery investigations.

## Overview

All Microsoft Teams 1:1 or group chats are journaled through to the respective users' mailboxes. All standard channel messages are journaled through to the group mailbox representing the team. Files uploaded in standard channels are covered under the eDiscovery functionality for SharePoint Online and OneDrive for Business.

eDiscovery of messages and files in [private channels](private-channels.md) works differently than in standard channels. To learn more, see [eDiscovery of private channels](#ediscovery-of-private-channels).

Not all Teams content is eDiscoverable. The following table shows the content types that you can search for using Microsoft eDiscovery tools:

| Content type | eDiscoverable | Notes |
|:--- | :--- |:--- |
|Audio recordings | No | |
|Card content|Yes|See [Search for card content](#search-for-card-content) for more information.|
|Chat links | Yes | |
|Chat messages | Yes |This includes content in Teams channels, 1:1 chats, 1:N group chats, and chats with guest user participants.  |
|Code snippets | No | |
|Edited messages | Yes | If the user is on hold, previous versions of edited messages are also preserved. |
|Emojis, GIFs, and stickers | Yes | |
|Inline images | Yes | |
|Meeting IM conversations | Yes | |
|Meeting metadata<sup>1</sup> | Yes |  |
|Name of channel | No | |
|Private channel messages | Yes | |
|Quotes | Yes | Quoted content is searchable. However, search results don't indicate that the content was quoted. |
|Reactions (such as likes, hearts, and other reactions) | No | |
|Subject | Yes | |
|Tables | Yes | |
|Feed notifications | No | |
|||

<sup>1</sup> Meeting (and call) metadata includes the following:

- Meeting start and end time, and duration
- Meeting join and leave events for each participant
- VOIP join/calls
- Anonymous join
- Federated user join
- Guest user join

  The image shows an example of meeting metadata.

  > [!div class="mx-imgBorder"]
  > ![Image is of the CVR records meeting metadata.](media/conversationOption3.png)

Here's an example of an IM conversation between participants during the meeting.

![Conversation between participants in Teams.](media/MeetingIMConversations.png)

> [!div class="mx-imgBorder"]
> ![Conversation between participants in eDiscovery search results.](media/MeetingImConversation2.png)

For more information about conducting an eDiscovery investigation, see [Get started with Core eDiscovery](/microsoft-365/compliance/get-started-core-ediscovery).

Microsoft Teams data will appear as IM or Conversations in the Excel eDiscovery export output. You can open the `.pst` file in Outlook to view those messages after you export them.

When viewing the .pst file for the team, all conversations are located in the Team Chat folder under Conversation History. The title of the message contains the team name and channel name. For example, the image below shows a message from Bob who messaged the Project 7 standard channel of the Manufacturing Specs team.

![Screenshot of a Team Chat folder in a user's mailbox in Outlook](media/Conduct_an_eDiscovery_investigation_of_content_in_Microsoft_Teams_image1.png)

Private chats in a user's mailbox are stored in the Team Chat folder under Conversation History.

## eDiscovery of private channels

Records for messages sent in a private channel are delivered to the mailbox of all private channel members, rather than to a group mailbox. The titles of the records are formatted to indicate which private channel they were sent from.

Because each private channel has its own SharePoint site that's separate from the parent team site, files in a private channel are managed independently of the parent team.

Teams doesn't support eDiscovery search of a single channel within a team, so the whole team must be searched. To perform an eDiscovery search of content in a private channel, search across the team, the site collection associated with the private channel (to include files), and mailboxes of private channel members (to include messages).

Use the following steps to identify files and messages in a private channel to include in your eDiscovery search.

### Include private channel files in an eDiscovery search

Before you perform these steps, install the [SharePoint Online Management Shell and connect to  SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

1. Run the following to get a list of all SharePoint site collections associated with private channels in the team.

    ```PowerShell
    Get-SPOSite
    ```

2. Run the following PowerShell script to get a list of all SharePoint site collection URLs associated with private channels in the team and the parent team group ID.

    ```PowerShell
    $sites = get-sposite -template "teamchannel#0"
    foreach ($site in $sites) {$x= get-sposite -identity $site.url -detail; $x.relatedgroupID; $x.url}
    ```

3. For each team or group ID, run the following PowerShell script to identify all relevant private channel sites, where $groupID is the group ID of the team.

    ```PowerShell
    $sites = get-sposite -template "teamchannel#0"
    $groupID = "e8195240-4a70-4830-9106-80193cf717cb"
    foreach ($site in $sites) {$x= Get-SpoSite -Identity $site.url -Detail; if ($x.RelatedGroupId -eq $groupID) {$x.RelatedGroupId;$x.url}}
    ```

### Include private channel messages in an eDiscovery search

Before you perform these steps, make sure you have the [latest version of the Teams PowerShell module](teams-powershell-overview.md) installed.

1. Run the following command to get a list of private channels in the team.

    ```PowerShell
    Get-TeamChannel -GroupId <GroupID> -MembershipType Private
    ```

2. Run the following command to get a list of private channel members.

    ```PowerShell
    Get-TeamChannelUser -GroupId <GroupID> -DisplayName "Engineering" -Role Member
    ```

3. Include the mailboxes of all members from each private channel in the team as part of your [eDiscovery search query](/microsoft-365/compliance/search-for-content-in-core-ediscovery).

## Search for content for guest users

You can use eDiscovery tools to search for Teams content related to guest users in your organization. Teams chat content that's associated with a guest user is preserved in a cloud-based storage location and can be searched for using eDiscovery. This includes searching for content in 1:1 and 1:N chat conversations in which a guest user is a participant with other users in your organization. You can also search for private channel messages in which a guest user is a participant and search for content in *guest:guest* chat conversations where the only participants are guest users.

To search for content for guest users:

1. Connect to Azure AD PowerShell. For instructions, see the "Connect with the Azure Active Directory PowerShell" section in [Connect to Microsoft 365 with PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module). Be sure to complete Step 1 and Step 2 in the previous topic.

2. After you successfully connect to Azure AD PowerShell, run the following command to display the user principal name (UPN) for all guest users in your organization. You have to use the UPN of the guest user when you create the search in step 4.

   ```powershell
   Get-AzureADUser -Filter "userType eq 'Guest'" -All $true | FL UserPrincipalName
   ```

   > [!TIP]
   > Instead of displaying a list of user principal names on the computer screen, you can redirect the output of the command to a text file. You can do this by appending `> filename.txt` to the previous command. The text file with the user principal names will be saved to the current folder.

3. In a different Windows PowerShell window, connect to Security & Compliance Center PowerShell. For instructions, see [Connect to Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell). You can connect with or without using multi-factor authentication.

4. Create a content search that searches for all content (such as chat messages and email messages) in which the specified guest user was a participant by running the following command.

   ```powershell
   New-ComplianceSearch <search name> -ExchangeLocation <guest user UPN>  -AllowNotFoundExchangeLocationsEnabled $true -IncludeUserAppContent $true
   ```

   For example, to search for content associated with the guest user Sara Davis, you would run the following command.

   ```powershell
   New-ComplianceSearch "Sara Davis Guest User" -ExchangeLocation "sara.davis_hotmail.com#EXT#@contoso.onmicrosoft.com" -AllowNotFoundExchangeLocationsEnabled $true -IncludeUserAppContent $true
   ```

    For more information about using PowerShell to create content searches, see [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch).

5. Run the following command to start the content search that you created in step 4:

   ```powershell
   Start-ComplianceSearch <search name>
   ```

6. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and then click **Show all** > **Content search**.

7. In the list of searches, select the search that you created in step 4 to display the flyout page.

8. On the flyout page, you can do the following things:

   - Click **View results** to view the search results and preview the content.

   - Next to the **Query** field, click **Edit** to edit and then rerun the search. For example, you can add a search query to narrow the results.

   - Click **Export results** to export and download the search results.

## Search for card content

Card content generated by apps in Teams channels, 1:1 chats, and 1xN chats is stored in mailboxes and can be searched. A *card* is a UI container for short pieces of content. Cards can have multiple properties and attachments, and can include buttons that can trigger card actions. For more information, see [Cards](/microsoftteams/platform/task-modules-and-cards/what-are-cards)

Like other Teams content, where card content is stored is based on where the card was used. Content for cards used in a Teams channel is stored in the Teams group mailbox. Card content for 1:1 and 1xN chats are stored in the mailboxes of the chat participants.

To search for card content, you can use the `kind:microsoftteams` or `itemclass:IPM.SkypeTeams.Message` search conditions. When reviewing search results, card content generated by bots in a Teams channel has the **Sender/Author** email property as `<appname>@teams.microsoft.com`, where `appname` is the name of the app that generated the card content. If card content was generated by a user, the value of **Sender/Author** identifies the user.

When viewing card content in Content search results, the content appears as an attachment to the message. The attachment is named `appname.html`, where `appname` is the name of the app that generated the card content. The following screenshots show how card content (for an app named Asana) appears in Teams and in the results of a search.

**Card content in Teams**

![Card content in Teams channel message](media/CardContentTeams.png)

**Card content in search results**
  
![Same card content in the results of a Content search](media/CardContentEdiscoverySearchResults.png)

> [!NOTE]
> To display images from card content in search results at this time (such as the checkmarks in the previous screenshot), you have to be signed into Teams (at https://teams.microsoft.com) in a different tab in the same browser session that you use to view the search results. Otherwise, image placeholders are displayed.

## Related topics

- [Microsoft 365 eDiscovery solutions](/microsoft-365/compliance/ediscovery)
- [Get started with Core eDiscovery](/microsoft-365/compliance/get-started-core-ediscovery)
- [Teams workflow in Advanced eDiscovery](/microsoft-365/compliance/teams-workflow-in-advanced-ediscovery)
- [Teams PowerShell Overview](teams-powershell-overview.md)
