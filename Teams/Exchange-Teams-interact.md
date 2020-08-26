---
title: How Exchange and Microsoft Teams interact
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.reviewer: dstrome
description: Learn what functionality exists between Microsoft Teams and the various Exchange setups such as creating and joining teams, creating channels, and more.
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# How Exchange and Microsoft Teams interact

> [!Tip]
> Watch the following session to learn how Teams interacts with Azure Active Directory (AAD), Microsoft 365 Groups, Exchange, SharePoint and OneDrive for Business: [Foundations of Microsoft Teams](https://aka.ms/teams-foundations)

For the full Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Microsoft 365 Group creation.

Users' Exchange mailboxes can be hosted online or on-premises.

Users hosted on Exchange Online or Exchange Dedicated vNext can use all the features of Teams. They can create and join teams and channels, create and view meetings, call and chat, modify user profile pictures (if the Outlook on the web mailbox policy allows them to do so), and add and configure connectors, tabs, and bots. For a more comprehensive list of available features, see the table below.

Users hosted on Exchange Online Dedicated (Legacy) must be synchronized to Azure Active Directory on Microsoft 365 or Office 365. They can create and join teams and channels, add and configure tabs and bots, and make use of the chat and calling features. However, they cannot modify profile pictures, manage meetings, access outlook contacts, or manage connectors.

> [!IMPORTANT]
> For integration with on-premises, it's highly recommended that you have an Exchange full Classic Hybrid deployment with Exchange Server 2016 or later to meet the requirements below. For more information about setting up a hybrid deployment, see [Exchange Server hybrid deployments](https://docs.microsoft.com/exchange/exchange-hybrid).

Users with mailboxes hosted on-premises must be synchronized to Azure Active Directory. They can make use of all the features in the above scenario, but additionally, they can manage meetings if the requirements listed on [Requirements for mailboxes hosted on-premises](#requirements-for-mailboxes-hosted-on-premises) section are met.

The following table provides a helpful quick reference to feature availability based on the Exchange environment.

**Actions supported:**

| User's mailbox is hosted in:                                        | eDiscovery       | Legal&nbsp;Hold    | Retention  | Team and Channel mgmt | Create and view meetings in Teams | Modify user profile picture | Call History | Manage Contacts | Access Outlook contacts | Voicemail  | Add and configure connectors | Add and configure tabs | Add and configure bots |
|---------------------------------------------------------------------|------------------|--------------------|------------|-----------------------|-----------------------------------|-----------------------------|--------------|-----------------|-------------------------|------------|------------------------------|------------------------|------------------------|
| **Exchange Online**                                                 | Yes <sup>1</sup> | Yes <sup>1</sup>   | Yes        | Yes                   | Yes                               | Yes<sup>7</sup>             | Yes          | Yes             | Yes <sup>6</sup>        | Yes        | Yes                          | Yes                    | Yes                    |
| **Exchange Online Dedicated vNext**                                 | Yes <sup>1</sup> | Yes <sup>1</sup>   | Yes        | Yes                   | Yes                               | Yes<sup>7</sup>             | Yes          | Yes             | Yes <sup>6</sup>        | Yes        | Yes                          | Yes                    | Yes                    |
| **Exchange Online Dedicated – Legacy** (Sync to Azure AD required)  | Yes <sup>1</sup> | Yes <sup>1,2</sup> | Yes <sup>3 | Yes                   | No                                | No                          | Yes          | Yes             | No                      | Yes <sup>4 | Yes <sup>5                   | Yes                    | Yes                    |
| **Exchange On-premises** (Sync to Azure AD) | Yes <sup>1</sup> | Yes <sup>1</sup>   | Yes <sup>3</sup> | Yes                   | Yes <sup>8</sup>         | No                          | Yes          | Yes             | No                      | Yes <sup>4 | Yes <sup>5                   | Yes                    | Yes                    |

<sup>1</sup> eDiscovery and Legal Hold for compliance on channel messages is supported for all hosting options.

<sup>2</sup> Teams private chat messages are not yet supported for Legal Hold for this hosting option.

<sup>3</sup> Retention will use a shadow mailbox for the online user to store messages.

<sup>4</sup> Teams users with on-premises Exchange mailbox may use voicemail with Teams and receive voicemail messages in Outlook, but voicemail messages will not be available to view or play within the Teams client.

<sup>5</sup> If one of the owners of a team can add connectors, everyone else in that team will be able to do so, even if their mailboxes are homed on-premises.

<sup>6</sup> Only contacts in default contacts folder. Access to other contacts folders or sub-folders is not supported.

<sup>7</sup> Teams honors the [Outlook on the web mailbox policy](https://docs.microsoft.com/powershell/module/exchange/client-access/set-owamailboxpolicy) setting that's configured by tenant admins to control whether users can change their profile picture. If the **-SetPhotoEnabled** setting is turned off in the policy, users cannot add, change, or remove their profile picture. For example, if a user uploads a profile picture that's approved by your organization's IT or HR department, no action is needed. However, if a user uploads an inappropriate picture, change it according to your organization's internal policies.

<sup>8</sup> You need to meet the requirements listed on [Requirements to create and view meetings for mailboxes hosted on-premises](#Requirements-to-create-and-view-meetings-for-mailboxes-hosted-on-premises) section.

## Requirements to get the most out of Microsoft Teams

Microsoft Teams works with several Microsoft 365 and Office 365 services to provide users with rich experience. To support this experience, you need to enable certain features or services and assign licenses.

- Users must be assigned an Exchange Online license.

- SharePoint Online is required to share and store files in team conversations. Microsoft Teams doesn't support SharePoint on-premises.

- Users must be assigned a SharePoint Online license if they want to share files in Chats. If users aren't assigned and enabled with SharePoint Online licenses, they don't have OneDrive for Business storage in Microsoft 365 or Office 365. File sharing will continue to work in Channels, but users are unable to share files in Chats without OneDrive for Business storage in Microsoft 365 or Office 365.

- Users must be enabled for Microsoft 365 group creation to create teams in Microsoft Teams.

> [!IMPORTANT]
> If you uninstall the Skype for Business client after you move a user to **Teams Only** mode, presence may stop working in Outlook and other Office apps. Presence works fine in Teams. To resolve this issue, select your profile picture in the top right-hand corner of Microsoft Teams and then select **Settings**. On the **General** tab under **Application**, select **Register Teams as the chat app for Office (requires restarting Office applications)**. After you select this option, close and re-open all Office apps, including Outlook. After you open Outlook, presence information will be available.

## Requirements to create and view meetings for mailboxes hosted on-premises

If mailboxes are hosted on-premises, to create and view meetings, the following requirements must be meet:

- The required Teams license needs to be assigned for the Azure Active Directory synced user.

- Users must be synchronized to Azure Active Directory. For information about how to use Azure AD Connect to synchronize with Azure Active Directory, see [Hybrid identity documentation](https://docs.microsoft.com/azure/active-directory/hybrid/).

- Mailboxes are hosted in Exchange Server 2016 Cumulative Update 3 or later.

> [!NOTE]
> Exchange 2016 CU3 adds support for REST API integration with Microsoft 365 and Autodiscover (AutoD) V2. REST is required to support Calendar application in Teams, for more information, see [Use REST APIs to access mailboxes in Exchange hybrid deployments](https://docs.microsoft.com/graph/hybrid-rest-support). Autodiscover (AutoD) V2 is required to allow the Teams service to perform an unauthenticated discovery of the user's mailbox, and also to support scheduling in Outlook for Teams. 

- Autodiscover and Exchange Web Services is published externally.

- OAuth authentication is configured preferably via the Exchange Hybrid Configuration Wizard running a full hybrid configuration (Classic or Modern). If you are not able to use the Hybrid Configuration Wizard, configure OAuth as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](https://docs.microsoft.com/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help).

> [!NOTE]
> Exchange trusts OAuth Token from Teams service which is known as EvoSTS. Step 1 should be enough, but just the EvoSTS; ACS is used for Free/Busy lookup in the calendar.

- The checkbox for the Exchange Hybrid Deployment feature in Azure AD Connect is set.

- For calendar app support and Teams Outlook Add-In for Mac, Exchange Web Service URLs must be configured as SPNs in Tenant Azure AD for the Exchange Service Principal. This step is done with Hybrid Configuration Wizard or following [manual steps for Hybrid Modern Authentication](https://docs.microsoft.com/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication#add-on-premises-web-service-urls-as-spns-in-azure-ad).

To enable calendar delegation for these users:

- Both delegate and delegator must have a mailbox on the Exchange Server.

- You must also complete steps 2-3 as described in [Configure Integration and OAuth between Skype for Business Online and Exchange Server](https://docs.microsoft.com/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises); these steps will provide the Teams scheduling application the required permissions to confirm delegate permissions.
 
> [!NOTE]
> Step 2 includes role assignment for ArchiveApplication, which is not required for delegation.

## Additional considerations

Here are some extra things to think about as you implement Microsoft Teams in your organization.

- In Microsoft Teams, security and compliance features like eDiscovery, Content Search, archiving, and legal hold work best in Exchange Online and SharePoint Online environments. For channel conversations, messages are journaled to the group mailbox in Exchange Online, where they're available for eDiscovery. If SharePoint Online and OneDrive for Business (using work or school account) are enabled across the organization and for users, these compliance features are available for all files within Teams as well.

- Control and protect the configuration of compliance policies in Teams and Exchange using Conditional Access. For more information see [How do Conditional Access policies work for Teams?](security-compliance-overview.md#how-conditional-access-policies-work-for-teams) .

- If your organization has compliance requirements to ensure all meeting discussions are discoverable, you should disable private meetings if the organizer has an Exchange on-premises mailbox. For more information, see [Allow scheduling private meetings](https://docs.microsoft.com/microsoftteams/meeting-policies-in-teams#allow-scheduling-private-meetings).

- In an Exchange hybrid deployment, content from chat messages is searchable regardless of whether chat participants have a cloud-based mailbox or an on-premises mailbox. To learn more, read [Searching cloud-based mailboxes for on-premises users](https://docs.microsoft.com/office365/securitycompliance/search-cloud-based-mailboxes-for-on-premises-users). To learn about searching for content in Teams, read [Content Search in the Microsoft 365 Compliance Center](https://docs.microsoft.com/Office365/SecurityCompliance/content-search#searching-microsoft-teams-and-office-365-groups).

## Troubleshooting

For a full troubleshooting guide on the topic, make sure to check out [Troubleshoot Microsoft Teams and Exchange Server interaction issues](https://docs.microsoft.com/microsoftteams/troubleshoot/known-issues/teams-exchange-interaction-issue).
