---
title: How Exchange and Microsoft Teams interact
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: dstrome
description: Learn what functionality exists between Microsoft Teams and the various Exchange setups such as creating and joining teams, creating channels, and more.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# How Exchange and Microsoft Teams interact

> [!Tip]
> Watch the following session to learn how Teams interacts with Azure Active Directory (AAD), Office 365 Groups, Exchange, SharePoint and OneDrive for Business: [Foundations of Microsoft Teams](https://aka.ms/teams-foundations)

For the full Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Office 365 Group creation.

Users' Exchange mailboxes can be hosted online or on-premises. Users hosted on Exchange Online or Exchange Dedicated vNext can use all the features of Teams. They can create and join teams and channels, create and view meetings, call and chat, modify user profile pictures, add and configure connectors, tabs, and bots.

Users hosted on either Exchange Online Dedicated - Legacy, or Exchange on-premises, must be synchronized to Azure Active Directory for Office 365. They can create and join teams and channels, add and configure tabs and bots, and chat and call. However, they can’t modify user profile pictures, or add and configure connectors. They can receive messages from connectors configured by other users. For creating and viewing meetings, it's a mixed bag: Creating and viewing meetings is supported for Exchange 2016 cumulative update 3 (CU3) and above, but not for versions prior to Exchange 2016 CU3.

The following table provides information for users with Exchange Online hosted in various environments.

**Actions supported:**

| User's mailbox is hosted in: | eDiscovery| Legal&nbsp;Hold | Retention| Team and Channel mgmt |Create and view meetings| Modify user profile picture | Call History | Manage Contacts | Access Outlook contacts | Voicemail |Add and configure connectors|Add and configure tabs|Add and configure bots| 
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|**Exchange Online**|Yes <sup>2</sup>|Yes <sup>2</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|**Exchange Online Dedicated vNext**|Yes <sup>2</sup>|Yes <sup>2</sup>|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|**Exchange Online Dedicated – Legacy** (Sync to Azure AD required)|Yes <sup>2</sup>|Yes <sup>2,3</sup>|Yes <sup>4|Yes|No|No|Yes|Yes|No|Yes <sup>5|Yes|Yes|Yes|
|**Exchange on-premises** (Sync to Azure AD required)|Yes <sup>2</sup>| Yes <sup>2,3</sup> |Yes <sup>4|Yes|Yes (Exchange 2016 CU3+)|Yes (Exchange 2016 CU3+)|Yes|Yes|No|Yes <sup>5|Yes|Yes|Yes|

<sup>1</sup> Exchange 2016 CU3 and above supported  
<sup>2</sup> eDiscovery and Legal Hold for compliance on channel messages is supported for all hosting options.  
<sup>3</sup> Teams private chat messages are not yet supported for Legal Hold for this hosting option.

<sup>4</sup> Retention will use a shadow mailbox for the online user to store messages. [Microsoft Teams Supports eDiscovery for Teams user in an Exchange Hybrid environment](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-supports-eDiscovery-for-Teams-users-in-a/ba-p/200009).

<sup>5</sup> Teams users with on premise Exchange mailbox may use voicemail with Teams and receive voicemail messages in Outlook, but voicemail messages will not be available to view or play within the Teams client.

## Requirements to get the most out of Microsoft Teams

Microsoft Teams works with several Office 365 services to provide users with a rich experience. To support this experience, you need to enable certain features or services and assign licenses.

- SharePoint Online is required to share and store files in team conversations. Microsoft Teams doesn't support SharePoint on-premises.

- Users must be assigned a SharePoint Online license if they want to share files in Chats. If users aren't assigned and enabled with SharePoint Online licenses, they don't have OneDrive for Business storage in Office 365. File sharing will continue to work in Channels, but users are unable to share files in Chats without OneDrive for Business storage in Office 365.

- Users must be enabled for Office 365 group creation to create teams in Microsoft Teams.

- To let Microsoft Teams work with Exchange on-premises, you must configure the new Exchange OAuth authentication protocol as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](https://docs.microsoft.com/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help).

> [!NOTE]
>For Exchange On-Premises and Teams integration, the required license needs to be assigned for the AAD synced user.

## Additional considerations

Here are some extra things to think about as you implement Microsoft Teams in your organization.

- In Microsoft Teams, security and compliance features like eDiscovery, Content Search, archiving, and legal hold work best in Exchange Online and SharePoint Online environments. For channel conversations, messages are journaled to the group mailbox in Exchange Online, where they're available for eDiscovery. If SharePoint Online and OneDrive for Business (using work or school account) are enabled across the organization and for users, these compliance features are available for all files within Teams as well.

- Control and protect the configuration of compliance policies in Teams and Exchange using Conditional Access. For more information see [How do Conditional Access policies work for Teams?](security-compliance-overview.md#how-do-conditional-access-policies-work-for-teams) .

- If your organization has compliance requirements to ensure all meeting discussions are discoverable, you should disable private meetings if the organizer has an Exchange on-premises mailbox.

- In an Exchange hybrid deployment, content from chat messages is searchable regardless of whether chat participants have a cloud-based mailbox or an on-premises mailbox. To learn more, read [Searching cloud-based mailboxes for on-premises users in Office 365](https://docs.microsoft.com/office365/securitycompliance/search-cloud-based-mailboxes-for-on-premises-users). To learn about searching for content in Teams, read [Content Search in the Office 365 Security & Compliance Center](https://docs.microsoft.com/Office365/SecurityCompliance/content-search#searching-microsoft-teams-and-office-365-groups).

> [!TIP]
> For information about how to use Azure AD Connect to synchronize with Azure Active Directory, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=854600).
