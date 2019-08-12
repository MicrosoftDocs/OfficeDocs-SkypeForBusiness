---
title: "Move users between on-premises and cloud"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom:
description: "Summary: In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and the cloud (whether to Microsoft Teams or to Skype for Business Online).."
---

# Move users between on-premises and cloud

In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and the cloud (whether to Microsoft Teams or to Skype for Business Online). Whether a user is located on-premises or in the cloud is known as the user’s Skype for Business home:

- Users who are homed on premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with Skype for Business Online service.

*Teams users inherently have a Skype for Business home, whether they use Skype for Business or not.* If you have on-premises Skype for Business users that are also using Teams (side by side), those users are homed on premises. Teams users with Skype for Business on premises do not have the ability to interoperate with Skype for Business users from their Teams client, nor can they communicate from Teams with users in a federated organization. Such functionality is only available after the user is moved from Skype for Business on premises to online. When you move a user to online, you can either allow them to use Skype for Business Online (and, optionally, Teams) or you can make them Teams Only. If your organization is already using Teams, it’s strongly recommended that you move them to Teams Only mode, which will ensure that routing of all incoming chats and calls lands in their Teams client. For more details, see [Teams coexistence with Skype for Business](/microsoftteams/coexistence-chat-calls-presence) and [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/microsoftteams/migration-interop-guidance-for-teams-with-skype).

## Prerequisites

Prerequisites to move a user to the cloud (whether to Skype for Business Only or Teams Only mode):

- The organization must have Azure AD Connect properly configured and be syncing all relevant attributes for the user as described in [Configure Azure AD Connect](configure-azure-ad-connect.md).
- Skype for Business hybrid must be configured, as described in [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
- The user must be assigned a license for Skype for Business Online (Plan 2), and if they will be using Teams, they must also have a Teams license.  In addition:
    - If the user is enabled for dial-in conferencing in on premises, by default the user must also have an Audio Conferencing license assigned in Office 365 before you run move the user online. Once migrated to the cloud, the user will be provisioned for audio conferencing in the cloud. If for some reason you want to move a user to the cloud, but not use audio conferencing functionality, you can override this check by specifying the `BypassAudioConferencingCheck` parameter in `Move-CsUser`.
    - If the user is enabled for Enterprise Voice in on premises, by default the user must have a Phone System license assigned in Office 365 before you move the user online. Once Migrated to the cloud, the user will be provisioned for Phone System in the cloud. If for some reason you want to move a user to the cloud but not use Phone System functionality, you can override this check by specifying the `BypassEnterpriseVoiceCheck`parameter in `Move-CsUser`.


## Moving users

When a user is moved from on-premises to the cloud:

- The user starts using Skype for Business Online services in the cloud for any Skype for Business functionality.
- Teams users become enabled for interoperability with Skype for Business users, and they can also federate with other organizations.
- Contacts from on premises are moved to the cloud (either Skype for Business or Teams).
- Existing meetings they organized that are scheduled in the future are migrated to online: If users are moved directly to TeamsOnly (see below),  meetings are converted to Teams meetings, otherwise meetings remain Skype for Business but will be migrated so they are hosted online instead of on-premises.  Migration of meetings happens asynchronously and begins approximately 90 minutes after moving the user.  To determine status of meeting migration, you can use [Get-csMeetingMigrationStatus](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md#managing-mms). Note that any content that was uploaded in advance of the meeting is not moved.

To move users between on premises and the cloud (whether to Teams or to Skype for Business Online), use either the Move-CsUser cmdlet or the Skype for Business Admin Control Panel, both of which are on-premises tools. These tools support three different move paths:

- [From Skype for Business Server (on premises) to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).
- [From Skype for Business Server (on premises) directly to Teams Only](move-users-from-on-premises-to-teams.md) (which also moves them to Skype for Business Online).  The option to move directly from on premises to Teams Only is available in Skype for Business Server 2019 as well as Cumulative Update 8 for Skype for Business Server 2015. Organizations using earlier versions of Skype for Business Server can move users to Teams Only by first moving them to Skype for Business Online, and then applying the TeamsOnly mode to these users once they are online.
- [From online (whether Teams Only or not), to on premises](move-users-from-the-cloud-to-on-premises.md).

## Required administrative credentials

To move users between on premises and the cloud, you must use an account with sufficient privileges in both the on-premises Skype for Business Server environment as well as in the Office 365 tenant. You can either use one account that has all the necessary privileges, or you can use two accounts, in which case you would access the on-premises tools using on-premises credentials, and then in those tools you would supply additional credentials for an Office 365 administrative account.  

- In the on-premises environment, the user performing the move must have the CSServerAdminstrator role in Skype for Business Server.
- In Office 365, the user performing the move must either be a Global Administrator or it must have both Skype for Business Administrator and User Administrator roles.  

    > [!Important]
    > - If you are using the Skype for Business Admin Control Panel, you will be prompted to provide credentials for an Office 365 account with the appropriate roles, as noted above. You must supply an account that ends in .onmicrosoft.com. If that is not possible, then use the Move-CsUser cmdlet.
    >- If you are using Move-CsUser in PowerShell, you can either use an account that ends in .onmicrosoft.com, or you can use any on-premises account that is synchronized into Azure AD, provided that you also specify the HostedMigrationOverrideUrl parameter in the cmdlet. The value of the hosted migration override URL is a variant of the following URL: https://adminXX.online.lync.com/HostedMigration/hostedmigrationService.svc<br>In the above URL, replace the XX with either two or three characters, determined as follows:
    >   - In a Skype for Business Online PowerShell session, run the following cmdlet:<br>`Get-CsTenant|ft identity`
    >    - The resulting value will be in the following format:<br>`OU=<guid>,OU=OCS Tenants,DC=lyncXX001,DC=local`
    >    - The two- or three-digit code is the XX contained in the section, DC=lyncXX001. If it’s a two-character code, it will be a digit followed by a number (such as 0a). If it’s a three-character code, it will be two letters followed by a digit (such as jp1). In all cases, you’ll see 001 immediately after the XX code.


## Voice configuration requirements

If users are configured for enterprise voice in on premises, you will need to coordinate updating their voice configuration when you move them to online, or, alternatively, you could migrate them without telephony capabilities. The available options depend on whether the user will be using the Teams or Skype for Business client once they are online:

- You can update a user’s telephony provider to use a [Microsoft Calling Plan](/microsoftteams/calling-plans-for-office-365). This is an option whether users will use Teams or Skype for Business clients.
- You can continue to use your on-premises PSTN provider:
  - Voice users who will use Teams must be configured for [Direct Routing](/microsoftteams/direct-routing-plan). Direct Routing is only available after the user is moved from on premises to online.
  - Voice users who will use the Skype for Business client after they are moved online must be configured for Skype for Business Hybrid Voice functionality.

For more details about telephony options in hybrid environments, as well as a supportability matrix, see [User accounts in a hybrid environment with PSTN connectivity](/microsoftteams/direct-routing-user-accounts-in-a-hybrid-environment).

## Other considerations

The policies (such as to control messaging, meeting, and calling behavior) in on-premises and online environments are independent. You may want to consider configuring any policies in the environment and assigning them to the user before you move that user from on premises to the cloud, so that they have the correct configuration as soon as they are migrated to online.

## See also

[Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md)

[Move users from on-premises to Teams](move-users-from-on-premises-to-teams.md)

[Setting up the Meeting Migration Service (MMS)](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md)

[Plan Direct Routing](/microsoftteams/direct-routing-plan)

[Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/move-csuser)
