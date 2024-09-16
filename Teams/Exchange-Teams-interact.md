---
title: How Exchange and Microsoft Teams interact
author: MicrosoftHeidi 
ms.author: heidip 
manager: jtremper
ms.date: 10/24/2023
ms.topic: conceptual
audience: admin
ms.service: msteams
description: Learn what functionality exists between Microsoft Teams and the various Exchange setups such as creating and joining teams, creating channels, and more.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# How Exchange and Microsoft Teams interact

> [!TIP]
> Watch the following session to learn how Teams interacts with Microsoft Entra ID, Microsoft 365 Groups, Exchange, SharePoint and OneDrive for Business: [Foundations of Microsoft Teams](https://aka.ms/teams-foundations)

For the full Teams experience, every user should be enabled for Exchange Online, SharePoint Online, and Microsoft 365 Group creation.

Users' Exchange mailboxes can be hosted online or on-premises.

Users hosted on Exchange Online or Exchange Dedicated vNext can use all the features of Teams. They can

- Create and join teams and channels
- Create and view meetings
- Call and chat
- Modify user profile pictures (if the Outlook on the web mailbox policy allows them to do so)
- Add and configure connectors, tabs, and bots

For a more comprehensive list of available features, see the **Actions supported** table in this article.

Users hosted on Exchange Online Dedicated (Legacy) must be synchronized to Microsoft Entra ID on Microsoft 365 or Office 365. They can:

- Create and join teams and channels
- Add and configure tabs and bots
- Make use of the chat and calling features

However, they can't:

- Modify profile pictures
- Manage meetings
- Access outlook contacts
- Manage connectors

> [!IMPORTANT]
> For integration with on-premises, it's highly recommended that you have an Exchange full Classic Hybrid deployment with Exchange Server 2016 or later. Modern Hybrid support is limited to Free/Busy and won't provide calendar integration from Teams to mailboxes on-premises, for example. For more information about setting up a hybrid deployment, see [Exchange Server hybrid deployments](/exchange/exchange-hybrid).

Users with mailboxes hosted on-premises must be synchronized to Microsoft Entra ID. They can make use of all the features in the above scenario, but additionally, they can manage meetings if the requirements listed on [Requirements for mailboxes hosted on-premises](#requirements-to-create-and-view-meetings-for-mailboxes-hosted-on-premises) section are met.

The following table provides a helpful quick reference to feature availability based on the Exchange environment.

**Actions supported:**

|User's mailbox is hosted in: |eDiscovery |Legal Hold |Retention |Team and Channel management |Create and view meetings in Teams |Modify user profile picture |Call History |Manage Contacts |Access Outlook contacts |Voicemail |Add and configure connectors |Add and configure tabs |Add and configure bots |Modify Out of Office settings |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|**Exchange Online**|Yes <sup>1</sup>|Yes <sup>1</sup>|Yes|Yes|Yes|Yes<sup>7</sup>|Yes|Yes|Yes <sup>6</sup>|Yes|Yes|Yes|Yes|Yes|
|**Exchange Online Dedicated vNext**|Yes <sup>1</sup>|Yes <sup>1</sup>|Yes|Yes|Yes|Yes<sup>7</sup>|Yes|Yes|Yes <sup>6</sup>|Yes|Yes|Yes|Yes|Yes|
|**Exchange Online Dedicated – Legacy** (Sync to Microsoft Entra ID required)|Yes <sup>1</sup>|Yes <sup>1,2</sup>|Yes <sup>3</sup>|Yes|No|No|Yes|Yes|No|Yes <sup>4</sup>|Yes <sup>5</sup>|Yes|Yes|Yes|
|**Exchange On-premises** (Sync to Microsoft Entra ID)|Yes <sup>1,9</sup>|Yes <sup>1</sup>|Yes <sup>3</sup>|Yes|Yes <sup>8</sup>|Yes<sup>10</sup>|Yes|Yes|No|Yes <sup>4</sup>|Yes <sup>5</sup>|Yes|Yes|No|

<sup>1</sup> eDiscovery and Legal Hold for compliance on channel messages is supported for all hosting options.

<sup>2</sup> Teams private chat messages aren't yet supported for Legal Hold for this hosting option.

<sup>3</sup> Retention uses a shadow mailbox for the online user to store messages.

<sup>4</sup> Teams users with on-premises Exchange mailbox can use voicemail with Teams and receive voicemail messages in Outlook, but voicemail messages won't be available to view or play within the Teams client.

<sup>5</sup> If one of the owners of a team can add connectors, everyone else in that team will be able to do so, irrespective of whether their mailbox is homed on-premises or online.

<sup>6</sup> Only contacts in default contacts folder. Access to other contacts folders or subfolders is not supported.

<sup>7</sup> Teams honors the [Outlook on the web mailbox policy](/powershell/module/exchange/client-access/set-owamailboxpolicy) setting that's configured by tenant admins to control whether users can change their profile picture. If the **-SetPhotoEnabled** setting is turned off in the policy, users can't add, change, or remove their profile picture, so the profile picture won't be synced to teams if the admin changes the photo.

<sup>8</sup> You need to meet the requirements listed in the [Requirements to create and view meetings for mailboxes hosted on-premises](#requirements-to-create-and-view-meetings-for-mailboxes-hosted-on-premises) section.

<sup>9</sup> A minimum of an Exchange Online Plan 1 license is also required. For more information, see [Search for Teams chat data for on-premises users](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users).

<sup>10</sup> On-premises users can use Teams to update their profile picture even if the `SetPhotoEnabled` Outlook on the Web mailbox policy is set to `false`.
 > [!NOTE]
 > Setting Out of Office (OOF) via the Teams client is currently not supported for users whose mailboxes are hosted on-premises; these users should perform this action via the Outlook client.

## Requirements to get the most out of Microsoft Teams

Microsoft Teams works with several Microsoft 365 and Office 365 services to provide users with rich experience. To support this experience, you need to enable certain features or services and assign licenses.

- Users must be assigned an Exchange Online license.

- SharePoint Online is required to share and store files in team conversations. Microsoft Teams doesn't support SharePoint on-premises.

- Users must be assigned a SharePoint Online license if they want to share files in Chats. If users aren't assigned and enabled with SharePoint Online licenses, they don't have OneDrive for Business storage in Microsoft 365 or Office 365. File sharing continues to work in Channels, but users are unable to share files in Chats without OneDrive for Business storage in Microsoft 365 or Office 365.

- Users must be enabled for Microsoft 365 group creation to create teams in Microsoft Teams.

  > [!IMPORTANT]
  > If you uninstall the Skype for Business client after you move a user to **Teams Only** mode, presence may stop working in Outlook and other Office apps. Presence works fine in Teams. To resolve this issue, select the ellipses button at the left of your profile picture in the top right-hand corner of Microsoft Teams and then select **Settings**. On the **General** tab under **Application**, select **Register Teams as the chat app for Office (requires restarting Office applications)**. After you select this option, close and re-open all Office apps, including Outlook. After you open Outlook, presence information will be available.

## Requirements to create and view meetings for mailboxes hosted on-premises

If mailboxes are hosted on-premises, to create and view meetings, the following requirements must be met:

- The required Teams license needs to be assigned for the Microsoft Entra ID synced user.

- Users must be synchronized to Microsoft Entra ID. For information about how to use Microsoft Entra Connect to synchronize with Microsoft Entra ID, see [Hybrid identity documentation](/azure/active-directory/hybrid/).

- Mailboxes are hosted in Exchange Server 2016 Cumulative Update 3 or later.

- Autodiscover and Exchange Web Services are published externally. For information about which Microsoft 365 services need access to on-premises Autodiscover and Exchange Web Services endpoints, see [Other endpoints not included in the Office 365 IP Address and URL Web service](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

- OAuth authentication is configured preferably via the Exchange Hybrid Configuration Wizard running a full hybrid configuration (Classic or Modern). If you aren't able to use the Hybrid Configuration Wizard, configure OAuth as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help).

  > [!NOTE]
  > Exchange trusts OAuth Token from Teams service which is known as EvoSTS. Step 1 should be enough, but just the EvoSTS; ACS is used for Free/Busy lookup in the calendar.

- The checkbox for the Exchange Hybrid Deployment feature in Microsoft Entra Connect is set. For more information, see [Exchange hybrid writeback](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized#exchange-hybrid-writeback).

- For calendar app support and Teams Outlook Add-In for Mac, Exchange Web Service URLs must be configured as SPNs in Tenant Microsoft Entra ID for the Exchange Service Principal. This step is done with Hybrid Configuration Wizard or following [manual steps for Hybrid Modern Authentication](/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication#add-on-premises-web-service-urls-as-spns-in-azure-ad).

To enable calendar delegation for these users:

- You must also complete steps as described in [Configure Integration and OAuth between Skype for Business Online and Exchange Server](/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises); these steps provide the Teams scheduling application the required permissions to confirm delegate permissions.

  > [!NOTE]
  > Step 2 includes role assignment for ArchiveApplication, which is not required for delegation.

- The Teams Scheduling add-in for Outlook requires Exchange 2013 CU19 or later when scheduling a meeting on behalf of someone else. This requirement is needed to support the unauthenticated discovery of the mailbox by our service to check delegate permissions against the delegator mailbox. The delegate and delegator location could be Exchange 2013 or later, or Exchange online, but Autodiscover must resolve to Exchange 2013 CU19 or later.

## Changed behavior of island user for Outlook integration

Because the menu option is hidden for Skype for Business users, if you want to use Teams for integration, it's recommended that the tenant admin set the default IM provider with a Windows policy. To do this, use the following value:

[HKEY_CURRENT_USER\Software\IM Providers] "DefaultIMApp"="**MsTeams**"

|Co-existance of IM providers  |Existing IM provider  |Expected behavior |Comment |
|---------|---------|---------|---------|
|SFB + Teams (T1 or T2.1) |Teams (T1 or T2.1)  |T2.1 automatically registers and starts as the IM provider.<br>Menu option on Settings is not available.  |This option is for users who upgrade from T1 or older version of T2.1, and are already using Teams as the IM provider. |
|SFB + Teams (T1 or T2.1)  |SFB  |SFB is the IM provider.<br>Menu option on Settings is not available. |Because the menu isn't available, other means are needed to use Teams as the IM provider. Admins can push out a registry change by using a Windows policy or script. End users can also modify the registry directly.<br>Admins can also migrate users to TeamsOnly mode. |
|Third party + Teams (T1 or T2.1) |Third party  |A third party is the IM provider.<br>Menu option is available on Settings.  |Admins can push out a registry change by using a Windows policy or script.<br>End users can select Teams as the IM provider from Settings.  |

## Additional considerations

Here are some extra things to think about as you implement Microsoft Teams in your organization.

- In Microsoft Teams, security and compliance features like eDiscovery, Content Search, archiving, and legal hold work best in Exchange Online and SharePoint Online environments. For channel conversations, messages are journaled to the group mailbox in Exchange Online, where they're available for eDiscovery. If SharePoint Online and OneDrive for Business (using work or school account) are enabled across the organization and for users, these compliance features are available for all files within Teams as well.

- Control and protect the configuration of compliance policies in Teams and Exchange using Conditional Access. For more information, see [How do Conditional Access policies work for Teams?](security-compliance-overview.md#how-conditional-access-policies-work-for-teams)

- If your organization has compliance requirements to ensure all meeting discussions are discoverable, you should disable private meetings if the organizer has an Exchange on-premises mailbox. For more information, see [Private meeting scheduling](./manage-who-can-schedule-meetings.md).

- In an Exchange hybrid deployment, content from chat messages is searchable regardless of whether chat participants have a cloud-based mailbox or an on-premises mailbox. To learn more, read [Searching cloud-based mailboxes for on-premises users](/office365/securitycompliance/search-cloud-based-mailboxes-for-on-premises-users). To learn about searching for content in Teams, read [Content Search in the Microsoft Purview compliance portal](/Office365/SecurityCompliance/content-search#searching-microsoft-teams-and-office-365-groups).

- For presence status, Microsoft Teams must check whether the mailbox is hosted on Exchange Online or on-premises. The service then decides where to access the mailbox. To enable the Teams service to check the mailbox location through the REST API call to the Exchange Online service, you have to deploy an Exchange hybrid environment by running the Exchange Hybrid Configuration wizard, as described in [Create a hybrid deployment with the Hybrid Configuration wizard](/exchange/hybrid-deployment/deploy-hybrid).

>[!Important]
>**GCC-H customers:** *Delegated Teams meeting scheduling* is not supported for GCC-High environments when the user's mailbox is hosted in on-premises Exchange Server.

## Troubleshooting

For a full troubleshooting guide on the topic, make sure to check out [Troubleshoot Microsoft Teams and Exchange Server interaction issues](/microsoftteams/troubleshoot/known-issues/teams-exchange-interaction-issue).
