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

In an on-premises deployment of Skype for Business Server, users of Skype for Business may also use Teams, but not all Teams functionality is available to such users as long as they are configured to use the on-premises Skype for Business Server deployment. These users are said to be "homed" on-premises, and certain Teams functionality is not available while these users are homed on-premises, for example:
- Federated calling and chats via the user's Teams client with users in other organizations is not available
- Interop communication via the user's Teams client with other users in the organization who use Skype for Business client.
- PSTN calling functionality (if the user is assigned a Phone System license).

To gain full Teams functionality, these users must be moved from Skype for Business on-premises to the cloud, at which point the user becomes TeamsOnly. The act of moving a user from on-premises to the cloud will set the user's co-existence mode to TeamsOnly. Once users are moved to the cloud, they are TeamsOnly, which means all incoming chats and calls lands in their Teams client. For more information, see [Teams coexistence with Skype for Business](/microsoftteams/coexistence-chat-calls-presence) and [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/microsoftteams/migration-interop-guidance-for-teams-with-skype).

To move users from the on-premises Skype for Business Server deployment to the cloud requires the [configuration of Skype for Business hybrid](/skypeforbusiness/hybrid/plan-hybrid-connectivity).  Once the deployment is enabled for hybrid, you can move users from the on-premises environment to the cloud to make them TeamsOnly as described below. If necessary, you can also move TeamsOnly users back to the on-premises Skype for Bsuiness deployment. 



## Prerequisites

Prerequisites to move a user to TeamsOnly mode:

- The organization must have Azure AD Connect properly configured and be syncing all relevant attributes for the user as described in [Configure Azure AD Connect](configure-azure-ad-connect.md).
- Skype for Business hybrid must be configured, as described in [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
- The user must be assigned a license for Teams and Skype for Business Online (Plan 2). Even after retirement of Skype for Business Online, the Skype for Business Online license is still required.  In addition:
    - If the user is enabled for dial-in conferencing in on premises, the user must also have an Audio Conferencing license assigned in Teams before you move the user online. Once migrated to the cloud, the user will be provisioned for audio conferencing in the cloud. 
    - If the user is enabled for Enterprise Voice in on premises, the user must have a Teams Phone license assigned in Teams before you move the user online. Once migrated to the cloud, the user will be provisioned for Phone System in the cloud. 
  
As of July 31, 2022, to move users between an on-premises deployment and the cloud, you must be using the following minimum version of either Skype for Business Server or Lync Server:

</br>
</br>

|On-premises product|Required minimum version|Required minimum build|
|---|---|---|
|Skype for Business Server 2019| CU6 |7.0.2046.385|
|Skype for Business Server 2015| CU12|6.0.9319.619|
|Lync Server 2013| CU10 with Hotfix 7|5.0.8308.1182|
|||

</br>
</br>

## Moving users

When a user is moved from on-premises to the cloud:

- The user becomes a TeamsOnly user, which means the user:
   -  Receives and initiates all chats and calls in the Teams client.
   -  Schedules all meetings in Teams.
   -  Can't initiate chats or calls, or schedule meetings in Skype for Business.
   -  Can join Skype for Business meetings they already have or receive in the future. However, after Microsoft removes the Skype for Business Online infrastructure for a given TeamsOnly user, TeamsOnly users may only join Skype for Business meetings anonymously. Beginning October 2022, users moved from on-premises to Teams Only in hybrid organizations will no longer be provisioned with the Skype for Business Online infrastructure. If these users are invited to a Skype for Business meeting, they would need to join anonymously. For details, see [Guidance for Organizations with on-premises deployments of Skype for Business Server](/MicrosoftTeams/update-skype-for-business-online-retirement.md#guidance-for-organizations-with-on-premises-deployments-of-skype-for-business-server).

- Users become enabled for interoperability with Skype for Business users, and can also federate with other organizations.
- Contacts from on premises are moved to Teams.
- Existing meetings they organized that are scheduled in the future are converted to Teams meetings. Migration of meetings happens asynchronously and begins approximately 90 minutes after moving the user.  To determine status of meeting migration, you can use [Get-csMeetingMigrationStatus](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md#managing-mms). Any content that was uploaded in advance of the meeting isn't moved.
- Users who are assigned a Teams Phone license can access PSTN functionality once they are properly configured.
 
To move users to Teams, use either the Move-CsUser cmdlet or the Skype for Business Admin Control Panel, both of which are on-premises tools. These tools support the following move paths:

- [From Skype for Business Server (on premises) to Teams Only](move-users-from-on-premises-to-teams.md).
- [From online (whether Teams Only or not), to on premises](move-users-from-the-cloud-to-on-premises.md).


> [!NOTE] 
>  The behavior to move directly from on premises to Teams Only is automatic, regardless of which version of Skype for Business Server or Lync Server is used. It is no longer required to specify the -MoveToTeams switch in Move-CsUser to move users directly from on-premises to TeamsOnly. Previously if this switch was not specified, users transitioned from being homed in Skype for Business Server on-premises to Skype for Business Online, and their mode remained unchanged. Now when moving a user from on-premises to the cloud with Move-CsUser, users are automatically assigned TeamsOnly mode and their meetings from on-premises are automatically converted to Teams meetings, just as if the `-MoveToTeams` switch had been specified, regardless of whether the switch was actually specified. 


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

If users are configured for enterprise voice in on premises, you need to coordinate updating their voice configuration when you move them to online. Alternatively, you could migrate them without telephony capabilities. 
- You can update a user’s telephony provider to use a [Microsoft Calling Plan](/microsoftteams/calling-plans-for-office-365). This is an option whether users will use Teams or Skype for Business clients.
- You can continue to use your on-premises PSTN provider:
  - Voice users who will use Teams must be configured for [Direct Routing](/microsoftteams/direct-routing-plan). Direct Routing is only available after the user is moved from on premises to online.

For more information about telephony options in hybrid environments, including a supportability matrix, see [User accounts in a hybrid environment with PSTN connectivity](/microsoftteams/direct-routing-user-accounts-in-a-hybrid-environment).

## Other considerations

The policies (such as to control messaging, meeting, and calling behavior) in on-premises and online environments are independent. You may want to consider configuring any policies in the environment and assigning them to the user before you move that user from on premises to the cloud, so that they have the correct configuration as soon as they're migrated to online.

## See also

[Move users from on-premises to Teams](move-users-from-on-premises-to-teams.md)

[Setting up the Meeting Migration Service (MMS)](../../SfbOnline/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms.md)

[Plan Direct Routing](/microsoftteams/direct-routing-plan)

[Move-CsUser](/powershell/module/skype/move-csuser)
