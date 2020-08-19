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

Users' Exchange mailboxes can be hosted online or on-premises. For integration with on-premises, it's recommended that you have an Exchange full Classic Hybrid deployment. For more information about setting up a hybrid deployment, see [Exchange Server hybrid deployments](https://docs.microsoft.com/exchange/exchange-hybrid).

Users hosted on Exchange Online or Exchange Dedicated vNext can use all the features of Teams. They can create and join teams and channels, create and view meetings, call and chat, modify user profile pictures (if the Outlook on the web mailbox policy allows them to do so), and add and configure connectors, tabs, and bots. For a more comprehensive list of available features, see the table below.

Users hosted on Exchange Online Dedicated (Legacy) must be synchronized to Azure Active Directory on Microsoft 365 or Office 365. They can create and join teams and channels, add and configure tabs and bots, and make use of the chat and calling features. However, they can't modify profile pictures, manage meetings, access outlook contacts, or manage connectors.

Users with mailboxes hosted on-premises must be synchronized to Azure Active Directory. They can make use of all the features in the above scenario, but additionally they can manage meetings, providing Exchange Server 2016 (Cumulative Update 3), or later, is running on-premises with OAuth configured (preferably via the Exchange Hybrid Configuration Wizard) as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](https://docs.microsoft.com/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help). To enable calendar delegation for these users, you must also complete steps 2-3 as described in [Configure Integration and OAuth between Skype for Business Online and Exchange Server](https://docs.microsoft.com/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises); these steps will provide the Teams scheduling application the required permissions to confirm delegate permissions.

The following table provides a helpful quick reference to feature availability based on the Exchange environment.

**Actions supported:**

| User's mailbox is hosted in:                                        | eDiscovery       | Legal&nbsp;Hold    | Retention  | Team and Channel mgmt | Create and view meetings in Teams | Modify user profile picture | Call History | Manage Contacts | Access Outlook contacts | Voicemail  | Add and configure connectors | Add and configure tabs | Add and configure bots |
|---------------------------------------------------------------------|------------------|--------------------|------------|-----------------------|-----------------------------------|-----------------------------|--------------|-----------------|-------------------------|------------|------------------------------|------------------------|------------------------|
| **Exchange Online**                                                 | Yes <sup>1</sup> | Yes <sup>1</sup>   | Yes        | Yes                   | Yes                               | Yes<sup>7</sup>             | Yes          | Yes             | Yes <sup>6</sup>        | Yes        | Yes                          | Yes                    | Yes                    |
| **Exchange Online Dedicated vNext**                                 | Yes <sup>1</sup> | Yes <sup>1</sup>   | Yes        | Yes                   | Yes                               | Yes<sup>7</sup>             | Yes          | Yes             | Yes <sup>6</sup>        | Yes        | Yes                          | Yes                    | Yes                    |
| **Exchange Online Dedicated – Legacy** (Sync to Azure AD required)  | Yes <sup>1</sup> | Yes <sup>1,2</sup> | Yes <sup>3 | Yes                   | No                                | No                          | Yes          | Yes             | No                      | Yes <sup>4 | Yes <sup>5                   | Yes                    | Yes                    |
| **Exchange On-premises** (Sync to Azure AD & OAuth config required) | Yes <sup>1</sup> | Yes <sup>1</sup>   | Yes <sup>3 | Yes                   | Yes (Exchange 2016 CU3+)          | No                          | Yes          | Yes             | No                      | Yes <sup>4 | Yes <sup>5                   | Yes                    | Yes                    |

<sup>1</sup> eDiscovery and Legal Hold for compliance on channel messages is supported for all hosting options.

<sup>2</sup> Teams private chat messages are not yet supported for Legal Hold for this hosting option.

<sup>3</sup> Retention will use a shadow mailbox for the online user to store messages.

<sup>4</sup> Teams users with on-premises Exchange mailbox may use voicemail with Teams and receive voicemail messages in Outlook, but voicemail messages will not be available to view or play within the Teams client.

<sup>5</sup> If one of the owners of a team can add connectors, everyone else in that team will be able to do so, even if their mailboxes are homed on-premises.

<sup>6</sup> Only contacts in default contacts folder. Access to other contacts folders or sub-folders is not supported.

<sup>7</sup> Teams honors the [Outlook on the web mailbox policy](https://docs.microsoft.com/powershell/module/exchange/client-access/set-owamailboxpolicy) setting that's configured by tenant admins to control whether users can change their profile picture. If the **-SetPhotoEnabled** setting is turned off in the policy, users can't add, change, or remove their profile picture. For example, if a user uploads a profile picture that's approved by your organization's IT or HR department, no action is needed. However, if a user uploads a picture that's inappropriate, change the picture according to your organization's internal policies.

## Requirements to get the most out of Microsoft Teams

Microsoft Teams works with several Microsoft 365 and Office 365 services to provide users with a rich experience. To support this experience, you need to enable certain features or services and assign licenses.

- SharePoint Online is required to share and store files in team conversations. Microsoft Teams doesn't support SharePoint on-premises.

- Users must be assigned a SharePoint Online license if they want to share files in Chats. If users aren't assigned and enabled with SharePoint Online licenses, they don't have OneDrive for Business storage in Microsoft 365 or Office 365. File sharing will continue to work in Channels, but users are unable to share files in Chats without OneDrive for Business storage in Microsoft 365 or Office 365.

- Users must be enabled for Microsoft 365 group creation to create teams in Microsoft Teams.

- To let Microsoft Teams work with Exchange on-premises, you must configure the new Exchange OAuth authentication protocol, preferably by running the Exchange Hybrid Wizard, as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](https://docs.microsoft.com/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help). To make calendar access work for your on-premises mailboxes, Teams needs access to your Exchange on-premises organization for both Autodiscover and EWS, and mailboxes should be located on Exchange 2016 CU3 or later. To enable users with Exchange on-premises mailboxes to schedule Teams meetings on behalf of another user, you must also complete steps 2 and 3 as described in [Configure Integration and OAuth between Skype for Business Online and Exchange Server](https://docs.microsoft.com/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises).

> [!NOTE]
> The Outlook Teams add-in can be used to schedule a Teams meeting for mailboxes hosted in Exchange on-premises. However, scheduling a Teams meeting on behalf of another user with Exchange on-premises requires Exchange 2016 CU3 and above and the new Exchange OAuth authentication protocol. Both delegate and delegator must have a mailbox on Exchange on-premises.

> [!NOTE]
> For Exchange On-Premises and Teams integration, the required license needs to be assigned for the AAD synced user.  State what the required license is.

> [!IMPORTANT]
> If you uninstall the Skype for Business client after you move a user to **Teams Only** mode, presence may stop working in Outlook and other Office apps. Presence works fine in Teams. To resolve this issue, select your profile picture in the top right-hand corner of Microsoft Teams and then select **Settings**. On the **General** tab under **Application**, select **Register Teams as the chat app for Office (requires restarting Office applications)**. After you select this option, close and re-open all Office apps, including Outlook. After you open Outlook, presence information will be available.

## Additional considerations

Here are some extra things to think about as you implement Microsoft Teams in your organization.

- In Microsoft Teams, security and compliance features like eDiscovery, Content Search, archiving, and legal hold work best in Exchange Online and SharePoint Online environments. For channel conversations, messages are journaled to the group mailbox in Exchange Online, where they're available for eDiscovery. If SharePoint Online and OneDrive for Business (using work or school account) are enabled across the organization and for users, these compliance features are available for all files within Teams as well.

- Control and protect the configuration of compliance policies in Teams and Exchange using Conditional Access. For more information see [How do Conditional Access policies work for Teams?](security-compliance-overview.md#how-conditional-access-policies-work-for-teams) .

- If your organization has compliance requirements to ensure all meeting discussions are discoverable, you should disable private meetings if the organizer has an Exchange on-premises mailbox.

- In an Exchange hybrid deployment, content from chat messages is searchable regardless of whether chat participants have a cloud-based mailbox or an on-premises mailbox. To learn more, read [Searching cloud-based mailboxes for on-premises users](https://docs.microsoft.com/office365/securitycompliance/search-cloud-based-mailboxes-for-on-premises-users). To learn about searching for content in Teams, read [Content Search in the Microsoft 365 Compliance Center](https://docs.microsoft.com/Office365/SecurityCompliance/content-search#searching-microsoft-teams-and-office-365-groups).

> [!TIP]
> For information about how to use Azure AD Connect to synchronize with Azure Active Directory, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=854600).

## Requirements for on-premises Exchange mailbox user

If users want the capability to schedule a Teams meeting using Exchange, then you need to ensure the following:

- Both delegate and delegator must have a mailbox on the Exchange Server.

- Auto Discover (AutoD) V2 is required to allow the Teams service to perform an unauthenticated discovery of the user's mailbox. AutoD V2 is supported in Exchange 2016 CU3+.

- The Exchange Server must be configured with Auth Server for EVOSTS. This is automatically configured as part of the Hybrid Wizard for Exchange (HWA).

    If you don't want to run HWA, then you can manually create the Auth Server for EVO STS on the Exchange server following these instructions [Configure OAuth authentication between Exchange and Exchange Online organizations](https://docs.microsoft.com/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help). However, we recommend that you use the HWA.

- The Exchange server must have a Partner Application configured with an application ID of **Skype for Business online,00000004-0000-0ff1-ce00-000000000000**. The ID is used by the Teams scheduling service and a linked user account that has the following properties:

  - Hidden from the Exchange address book. It's a best practice to hide it from the address book because it's a disabled user account.

  - Exchange management role assignment of **UserApplication**.

To complete the integration, follow Steps 1-3 in [How do you configure OAuth authentication between your on-premises Exchange and Exchange Online organizations?](https://docs.microsoft.com/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help#how-do-you-configure-oauth-authentication-between-your-on-premises-exchange-and-exchange-online-organizations) Note that step 2 includes role assignment for ArchiveApplication which is not required for Delegation, but is for Archiving SfB Online Chat to an Exchange mailbox.


## Troubleshooting

For a full troubleshooting guide on the topic, make sure to check out [Troubleshoot Microsoft Teams and Exchange Server interaction issues](https://docs.microsoft.com/microsoftteams/troubleshoot/known-issues/teams-exchange-interaction-issue).
