---
title: PSTN considerations when upgrading to Teams from Skype for Business
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Voice considerations for upgrade from Skype for Business to Teams  
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
- M365-collaboration
appliesto:
- Microsoft Teams
---

# PSTN considerations for upgrading to Teams from Skype for Business on-premises

This article describes Public Switched Telephone Network (PSTN) considerations when upgrading to Teams.

[!INCLUDE [sfbo-retirement-skype](../Skype/Hub/includes/sfbo-retirement.md)]

The following articles describe important upgrade concepts and coexistence behaviors:

- [Coexistence of Teams and Skype for Business](teams-and-skypeforbusiness-coexistence-and-interoperability.md)
- [Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md)
- [Teams client experience and conformance to coexistence modes](teams-client-experience-and-conformance-to-coexistence-modes.md)


 > [!NOTE]
 > - Using Phone System with Teams is only supported when the user's account is assigned a Teams upgrade policy with Teams Only mode.  
 > - Using Phone System with Skype for Business is only supported when the user's account is assigned a Teams upgrade policy with an SfB mode. 
 > - Phone System is not supported when the user's account is assigned a Teams upgrade policy with Islands mode.
 > - Any call forwarding, team-call group, and delegation settings from Skype for Business are not migrated and will need to be re-recreated for Teams.
 > - For a general overview of Microsoft Teams cloud voice features, and help deciding which Microsoft voice solution is right for your organization, see [Plan your Teams voice solution](cloud-voice-landing-page.md).


## PSTN calling scenarios

There are four possible calling scenarios when moving to TeamsOnly mode:

- [A user in Skype for Business Online, with a Microsoft Calling Plan](#from-skype-for-business-online-with-microsoft-calling-plans). Upon upgrade, this user will continue to have a Microsoft Calling plan.

- [A user in Skype for Business Online, with on-premises voice functionality](#from-skype-for-business-online-with-on-premises-voice) through Skype for Business on-premises or Cloud Connector Edition. To ensure the TeamsOnly user has PSTN functionality, you must coordinate the user’s upgrade to Teams with the user's migration to Direct Routing.

- [A user in Skype for Business on-premises with Enterprise Voice](#from-skype-for-business-server-on-premises-with-enterprise-voice-to-direct-routing), who will be moving to online and keeping on-premises PSTN connectivity.  To migrate this user to Teams, you must move the user’s on-premises Skype for Business account to the cloud, and coordinate that move with migration of the user to Direct Routing. 

- [A user in Skype for Business on-premises with Enterprise Voice](#from-skype-for-business-server-on-premises-with-enterprise-voice-to-microsoft-calling-plan), who will be moving to online and using a Microsoft Calling plan.  To migrate this user to Teams, you must move the user’s on-premises Skype for Business account to the cloud. You must coordinate the move with either A) the port of that user’s phone number to a Microsoft Calling Plan or B) assigning a new subscriber number from available regions.

This article provides a high-level overview only. For more information, see [Phone System Direct Routing](direct-routing-landing-page.md) and [Calling Plans](calling-plan-landing-page.md). 

## From Skype for Business Online with Microsoft Calling Plans 

This scenario is the simplest upgrade scenario involving voice. 

1. Make sure users have been assigned a Teams license. By default, when you assign a Microsoft 365 or Office 365 license, Teams is enabled. Unless you previously disabled the Teams license, no action should be necessary.

2.  If users already have a Microsoft Calling Plan with a phone number, the only required change is to assign the user TeamsOnly mode in TeamsUpgradePolicy. Before assigning TeamsOnly mode, incoming PSTN calls will land in the user’s Skype for Business client. After the upgrade to TeamsOnly mode, incoming PSTN calls will land in the user’s Teams client.  

## From Skype for Business Online with on-premises voice

In this scenario, the user is already in Skype for Business Online. The user's PSTN connectivity is on-premises, either using Skype for Business Server in hybrid mode or Cloud Connector Edition. To migrate these users to TeamsOnly mode with PSTN functionality, you must enable the users for Direct Routing. With Direct Routing, PSTN trunks connect directly to the Direct Routing service through your on-premises Session Border Controller (SBC).

The basic steps are listed below.  Steps 1-4 are listed in the suggested sequence, but they can be done in any order. These steps should be completed before Step 5.

1. If you're setting the tenant-wide policy to one of the Skype for Business modes, be sure to grandfather any existing Islands users by explicitly assigning them Islands mode, as previously described.

2. Configure your tenant for Direct Routing. See [Summary of per-tenant configuration of Direct Routing](#summary-of-per-tenant-configuration-of-direct-routing).

3. If desired, configure various Teams policies for these users (for example, TeamsMessagingPolicy, TeamsMeetingPolicy, and so on). You can configure poicies at any time. However, if you want to ensure that users have the correct configuration when they are upgraded, configure these policies before the user is upgraded to 
TeamsOnly mode.

4. Prepare select users for voice migration: 
   - If necessary, assign the Teams license.  Assuming the user is already functional in Skype for Business Online on-premises voice, the user already has Skype for Business Plan 2 and Microsoft Phone System. Leave both those plans enabled, including the Skype for Business Online Plan 2 license.  
   - Assign the desired OnlineVoiceRoutingPolicy. 

5. Upgrade the user: These steps should be coordinated. 

   - In Microsoft 365 or Office 365, upgrade the user to TeamsOnly mode (Grant-CsTeamsUpgradePolicy).
   - On the SBC, configure voice routing to enable incoming calls by sending calls to Direct Routing instead of to the on-premises Mediation Server.


## From Skype for Business Server on-premises, with Enterprise Voice, to Direct Routing

In this scenario, the user is still homed in Skype for Business on-premises. The user's PSTN connectivity is also on-premises. To migrate this user to TeamsOnly mode with PSTN functionality, you must enable the user for Direct Routing, and then move the user to the cloud. 
 
The basic steps are listed below. Steps 1-5 are listed in the suggested sequence, but they can be done in any order. You must complete Steps 1-5 before Step 6.

1. If you will be setting the tenant-wide policy to one of the Skype for Business modes, be sure to grandfather existing Islands users by explicitly assigning them Islands mode, as previously described.

2. If you haven’t already done so, [configure the organization for Skype for Business hybrid](/SkypeForBusiness/hybrid/configure-hybrid-connectivity).

3. Configure your tenant for Direct Routing. See [Summary of per-tenant configuration of Direct Routing](#summary-of-per-tenant-configuration-of-direct-routing).

4. If desired, configure various Teams policies for these users (for example, TeamsMessagingPolicy, TeamsMeetingPolicy). You can configure policies at any time. However, if you want to ensure that users have the correct configuration when they are upgraded, configure these policies before the user is upgraded to TeamsOnly.

5. Assign the Microsoft 365 or Office 365 licenses if necessary.  The user should have both Teams and Skype for Business Online Plan 2 and Phone System. If the Skype for Business Online Plan 2 is disabled, re-enable it.  

6. Upgrade the user: These steps should be coordinated. 

   - Using the on-premises Skype for Business tools, run Move-CsUser with -MoveToTeams switch. If you're using a version of Skype for Business Server that does not support the -MoveToTeams switch, first run Move-CsUser and then assign TeamsOnly mode in tenant remote PowerShell or Teams Admin Console.

   - On the SBC, configure voice routing to enable incoming calls by sending calls to Direct Routing instead of to the on-premises Mediation Server. 

   - In Microsoft 365 or Office 365: Assign the relevant OnlineVoiceRoutingPolicy to enable outgoing calls. 


## From Skype for Business Server on-premises, with Enterprise Voice, to Microsoft Calling Plan

In this scenario, the user is still homed in Skype for Business on-premises. The user's PSTN connectivity is also on-premises. To migrate this user to TeamsOnly mode with PSTN functionality, you must move the user to the cloud, and either port their number from the old carrier to a Microsoft Calling plan, or assign a new number to the user. 

The basic steps are listed below.  Steps 1-5 are listed in the suggested sequence, but they can be done in any order. You must complete Steps 1-5 before Step 6. 

1. If you will be setting the tenant-wide policy to one of the Skype for Business modes, be sure to grandfather existing Islands users by explicitly assigning them Islands mode, as previously described. 

2. If you haven’t already done so, [configure the organization for Skype for Business hybrid](/SkypeForBusiness/hybrid/configure-hybrid-connectivity). 

3. If desired, configure various Teams policies for these users (for example, TeamsMessagingPolicy, TeamsMeetingPolicy, and so on). You can configure policies at any time. However, if you want to ensure that users have the correct configuration when they are upgraded, configure these policies before the user is upgraded to TeamsOnly. 

4. Assign the Microsoft 365 or Office 365 licenses if necessary.  The user should have both Teams and Skype for Business Online Plan 2 and Phone System. If the Skype for Business Online Plan 2 is disabled, re-enable it.  

5. Get phone numbers for your users. (For details see [Manage phone numbers for your organization](./manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).)

   - If you will be reusing the numbers, submit a porting request to your carrier.  
   - Alternatively, you can acquire new numbers directly from Microsoft. 

6. Upgrade the user and if needed assign LineUri. Using the on-premises Skype for Business tools, run Move-CsUser with the -MoveToTeams switch.  

    - If you are porting numbers to Microsoft, you should coordinate the timing of this operation to occur when the port occurs. 

    - If you are using new numbers from Microsoft, you’ll need to change the LineUri for the user after the user is moved online by using Set-CsPhoneNumberAssignment.  

## Summary of per-tenant configuration of Direct Routing 

1. Ensure that your Session Border Controller (SBC) is supported with Direct Routing by reviewing [this list](direct-routing-border-controllers.md). Also ensure that you have the correct version of firmware.  

2. Pair your on-premises SBC with the Teams Direct Routing service. For details, see [Pair the SBC to the Direct Routing service of Phone System](direct-routing-configure.md). 

3. This configuration is essentially a mirror of the on-premises configuration. The online configuration consists of: 
   - OnlineVoiceRoutingPolicy (based on the on-premises VoiceRoutingPolicy if migrating users from Skype for Business   Online, and based on VoicePolicy if migrating users from on-premises with Enterprise Voice).
   - OnlinePSTNUsage objects (based on on-premises PSTN usage). 
   - OnlineVoiceRoute objects (based on-premises VoiceRoute). 

For more information, see [Configure Direct Routing](direct-routing-configure.md). 

## Manage EnterpriseVoiceEnabled property during migration 

Whether using Direct Routing or a Microsoft Calling plan, a user must have EnterpriseVoiceEnabled=true in Azure AD for the user to have PSTN functionality.  EnterpriseVoiceEnabled (“EV-enabled”) is a property (not a policy) that exists in both an on-premises directory and in the cloud. The value in the cloud is what matters for Teams.  The exact logic for how EV-enabled gets set to true depends on the following scenario: 

- If the user is EV-enabled in on-premises Skype for Business Server and a Phone System license is assigned to the user prior to moving the user to the cloud with Move-CsUser, the online user will be provisioned with EV-enabled=true. 

- If an existing TeamsOnly or Skype for Business Online user is assigned a Phone System license, EV-enabled is not set to true by default. This also is the case if an on-premises user is moved to the cloud prior to assigning the Phone System license. In either case, the admin must specify the following cmdlet: 

  ```PowerShell
  Set-CsPhoneNumberAssignment -EnterpriseVoiceEnabled $True 
  ```

## Related links

[Plan your Teams voice solution](cloud-voice-landing-page.md)

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)
