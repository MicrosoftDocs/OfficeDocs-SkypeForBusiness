---
title: "Move users between on-premises and cloud"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom:
description: "Summary: In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and the cloud."
---

# Move users between on-premises and cloud

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and Teams. Whether a user is located on-premises or in the cloud is known as the user’s Skype for Business home:

- Users who are homed on premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with the Teams service.

*Teams users inherently have a Skype for Business home, whether they use Skype for Business or not.* If you have on-premises Skype for Business users that are also using Teams (side by side), those users are homed on premises. Teams users with Skype for Business on premises can't interoperate with Skype for Business users from their Teams client, nor can they communicate from Teams with users in a federated organization. Such functionality is fully available only after the user is moved from Skype for Business on-premises to online and made TeamsOnly. It’s  recommended that you move your users to TeamsOnly mode, which will ensure that routing of all incoming chats and calls lands in their Teams client. For more information, see [Teams coexistence with Skype for Business](/microsoftteams/coexistence-chat-calls-presence) and [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/microsoftteams/migration-interop-guidance-for-teams-with-skype).

## Prerequisites

Prerequisites to move a user to TeamsOnly mode:

- The organization must have Azure AD Connect properly configured and be syncing all relevant attributes for the user as described in [Configure Azure AD Connect](configure-azure-ad-connect.md).
- Skype for Business hybrid must be configured, as described in [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
- The user must be assigned a license for Teams and Skype for Business Online (Plan 2). Even after retirement of Skype for Business Online, the Skype for Business Online license is still required.  In addition:
    - If the user is enabled for dial-in conferencing in on premises, the user must also have an Audio Conferencing license assigned in Teams before you move the user online. Once migrated to the cloud, the user will be provisioned for audio conferencing in the cloud. 
    - If the user is enabled for Enterprise Voice in on premises, the user must have a Phone System license assigned in Teams before you move the user online. Once migrated to the cloud, the user will be provisioned for Phone System in the cloud. 


## Moving users

When a user is moved from on-premises to the cloud:

- Teams users become enabled for interoperability with Skype for Business users, and if they're TeamsOnly they can also federate with other organizations.

- Contacts from on premises are moved to Teams.

- Existing meetings they organized that are scheduled in the future are converted to Teams meetings. Migration of meetings happens asynchronously and begins approximately 90 minutes after moving the user.  To determine status of meeting migration, you can use [Get-csMeetingMigrationStatus](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md#managing-mms). Any content that was uploaded in advance of the meeting isn't moved.

To move users to Teams, use either the Move-CsUser cmdlet or the Skype for Business Admin Control Panel, both of which are on-premises tools. These tools support the following move paths:

- [From Skype for Business Server (on premises) directly to Teams Only](move-users-from-on-premises-to-teams.md).  The behavior to move directly from on premises to Teams Only is now automatic, regardless of which version of Skype for Business Server or Lync Server is used. It's no longer necessary to specify the `-MoveToTeams` switch to get this behavior.  
- [From online (whether Teams Only or not), to on premises](move-users-from-the-cloud-to-on-premises.md).

> [!NOTE] 
> It is no longer required to specify the -MoveToTeams switch in Move-CsUser to move users directly from on-premises to TeamsOnly. Previously if this switch was not specified, users transitioned from being homed in Skype for Business Server on-premises to Skype for Business Online, and their mode remained unchanged. Now when moving a user from on-premises to the cloud with Move-CsUser, users are automatically assigned TeamsOnly mode and their meetings from on-premises are automatically converted to Teams meetings, just as if the `-MoveToTeams` switch had been specified, regardless of whether the switch was actually specified. 
> 

## Required administrative credentials

To move users between on-premises and the cloud, you must use an account with sufficient privileges in both the on-premises Skype for Business Server environment and in the Teams organization. You can either use one account that has all the necessary privileges, or you can use two accounts. If you use two accounts, you would access the on-premises tools using on-premises credentials, and then in those tools you would supply additional credentials for a Teams administrative account.  

- In the on-premises environment, the user performing the move must have the CSServerAdministrator, CsUserAdministrator, and RTCUniversalUserAdmins roles in Skype for Business Server.
- In Teams, the user performing the move must be a member of at least one of the following roles:
  - Global Administrator role
  - Teams Administrator role
  - Skype for Business Administrator role.  

    > [!Important]
    > - If you are using the Skype for Business Admin Control Panel, you will be prompted to provide credentials for a Microsoft 365 account with the appropriate roles, as noted above. You must supply an account that ends in .onmicrosoft.com. If that is not possible, then use the Move-CsUser cmdlet.
    >- If you are using Move-CsUser in PowerShell, you can either use an account that ends in .onmicrosoft.com, or you can use any on-premises account that is synchronized into Azure AD, provided that you also specify the HostedMigrationOverrideUrl parameter in the cmdlet. The value of the hosted migration override URL is a variant of the following URL: https://adminXX.online.lync.com/HostedMigration/hostedmigrationService.svc<br>In the above URL, replace the XX with either two or three characters, determined as follows:
    >   - In a Teams PowerShell session, run the following cmdlet:<br>`Get-CsTenant | ft ServiceInstance`
    >   - The resulting value will be in the following format:<br>`MicrosoftCommunicationsOnline/YYYY-XX-ZZ`
    >   - The two- or three-character code is the XX contained in the section YYYY-XX-ZZ. If it’s a two-character code, it will be a digit followed by a number (such as 4A). If it’s a three-character code, it will be two letters followed by a digit (such as JP1). An example is NOAM-4A-S7.


## Voice configuration requirements

If users are configured for enterprise voice in on premises, you need to coordinate updating their voice configuration when you move them to online. Alternatively, you could migrate them without telephony capabilities. The available options depend on whether the user will be using the Teams or Skype for Business client once they're online:

- You can update a user’s telephony provider to use a [Microsoft Calling Plan](/microsoftteams/calling-plans-for-office-365). This is an option whether users will use Teams or Skype for Business clients.
- You can continue to use your on-premises PSTN provider:
  - Voice users who will use Teams must be configured for [Direct Routing](/microsoftteams/direct-routing-plan). Direct Routing is only available after the user is moved from on premises to online.
  - Voice users who will use the Skype for Business client after they're moved online must be configured for Skype for Business Hybrid Voice functionality.

For more information about telephony options in hybrid environments, including a supportability matrix, see [User accounts in a hybrid environment with PSTN connectivity](/microsoftteams/direct-routing-user-accounts-in-a-hybrid-environment).

## Other considerations

The policies (such as to control messaging, meeting, and calling behavior) in on-premises and online environments are independent. You may want to consider configuring any policies in the environment and assigning them to the user before you move that user from on premises to the cloud, so that they have the correct configuration as soon as they're migrated to online.

## See also

[Move users from on-premises to Teams](move-users-from-on-premises-to-teams.md)

[Setting up the Meeting Migration Service (MMS)](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md)

[Plan Direct Routing](/microsoftteams/direct-routing-plan)

[Move-CsUser](/powershell/module/skype/move-csuser)
