---
title: How Exchange and Microsoft Teams interact
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
ms.reviewer: crowe
description: Learn what functionality exists between Microsoft Teams and the various Exchange setups such as creating and joining teams, creating channels, and more.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

How Exchange and Microsoft Teams interact 
=========================================

> [!Tip]
> Watch the following session to learn how Teams interacts with Azure Active Directory (AAD), Office 365 Groups, Exchange, SharePoint and OneDrive for Business: [Foundations of Microsoft Teams](https://aka.ms/teams-foundations)

For the full Microsoft Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Office 365 Group creation.

Users' Exchange mailboxes can be hosted online or on-premises. Users hosted on Exchange Online or Exchange Dedicated vNext can use all the features of Teams. They can create and join teams and channels, create and view meetings, call and chat, modify user profile pictures, add and configure connectors, tabs, and bots.

Users hosted on either Exchange Online Dedicated - Legacy, or Exchange on-premises, must be synchronized to Azure Active Directory for Office 365. They can create and join teams and channels, add and configure tabs and bots, and chat and call. However, they can’t modify user profile pictures, or add and configure connectors. They can receive messages from connectors configured by other users. For creating and viewing meetings, it's a mixed bag: Creating and viewing meetings is supported for Exchange 2016 cumulative update 3 (CU3) and above, but not for versions prior to Exchange 2016 CU3.

The following table provides information for users with Exchange Online hosted in various environments.

**Actions supported:** 

| User's mailbox is hosted in: | eDiscovery| Legal Hold | Retention| Team and Channel mgmt |Create and view meetings| Modify user profile picture | Call History | Manage Contacts | Access Outlook contacts | Voicemail |Add and configure connectors|Add and configure tabs|Add and configure bots| 
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|**Exchange Online**|Yes<sup>2</sup>|Yes<sup>2</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|**Exchange Online Dedicated vNext**|Yes<sup>2</sup>|Yes<sup>2</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|**Exchange Online Dedicated – Legacy** (Sync to Azure AD required)|Yes ([allowed list](https://support.office.com/en-us/article/searching-cloud-based-mailboxes-for-on-premises-users-in-office-365-3f7dde1a-a8ea-4366-86da-8ee6777f357c?ui=en-US&rs=en-US&ad=US))<sup>2</sup>|Yes<sup>2, 3</sup>|No|Yes|No|No|Yes|Yes|No|No|No|Yes|Yes|
|**Exchange on-premises** (Sync to Azure AD required)|Yes ([allowed list](https://support.office.com/en-us/article/searching-cloud-based-mailboxes-for-on-premises-users-in-office-365-3f7dde1a-a8ea-4366-86da-8ee6777f357c?ui=en-US&rs=en-US&ad=US))<sup>2</sup>|Yes<sup>2, 3</sup>|No|Yes|Yes(Exchange 2016 CU3+)|No|Yes|Yes|No|No|No|No|Yes|
                                                            
<sup>1</sup> Exchange 2016 CU3 and above supported  
<sup>2</sup> eDiscovery and Legal Hold for compliance on channel messages is supported for all hosting options.  
<sup>3</sup> Teams private chat messages are not yet supported for Legal Hold for this hosting option.

Additional information:

-   Microsoft Teams doesn't support SharePoint on-premises.

-   SharePoint Online is required to share and store files in team conversations.

-   OneDrive for Business is required to share and store files in private chats.

-   If users aren't assigned and enabled with SharePoint Online licenses, they don't have OneDrive for Business storage in Office 365. File sharing will continue to work in Channels, but users are unable to share files in Chats without OneDrive for Business storage in Office 365.

-   Users must be enabled for Office 365 group creation to create teams in Microsoft Teams.

-   In Microsoft Teams, security and compliance features like eDiscovery, Content Search, archiving, and legal hold work best in Exchange Online and SharePoint Online environments. For channel conversations, messages are journaled to the group mailbox in Exchange Online, where they're available for eDiscovery. If SharePoint Online and OneDrive for Business (using work or school account) are enabled across the organization and for users, these compliance features are available for all files within Teams as well.

-   For Exchange on-premises (hybrid deployment), you need to configure OAuth as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](https://technet.microsoft.com/en-us/library/dn594521(v=exchg.150).aspx). 

> [!NOTE]
> Currently, if your organization has compliance requirements to ensure all meeting discussions are discoverable, you should disable private meetings if the organizer has an Exchange on-premises mailbox.
> 
> [!IMPORTANT]
>   Users who participate in conversations that are part of the Chat list in Microsoft Teams must have an Exchange Online (cloud-based) mailbox for an admin to search chat conversations. That's because conversations that are part of the Chat list are stored in the cloud-based mailboxes of the chat participants. If a chat participant doesn't have an Exchange Online mailbox, the admin won't be able to search or place a hold on chat conversations. For example, in an Exchange hybrid deployment, users with on-premises mailboxes might be able to participate in conversations that are part of the Chat list in Microsoft Teams. However, in this case, content from these conversations isn't searchable and can't be placed on hold because the users don't have cloud-based mailboxes. For more details about Content Searches and Microsoft Teams, see [Run a Content Search in the Office 365 Security & Compliance Center](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a).
> 
> [!TIP]
>   For information about how to use Azure AD Connect to synchronize with Azure Active Directory, see [*Integrating your on-premises identities with Azure Active Directory*](https://go.microsoft.com/fwlink/?linkid=854600).
