---
title: Upgrade Skype for Business on-premises to Microsoft Teams
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Learn how to upgrade your organization to Microsoft Teams from a Skype for Business on-premises deployment.  
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom:
- Teams-upgrade-guidance
- seo-marvel-apr2020
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrade from Skype for Business on-premises to Teams

![Upgrade journey diagram, emphasizing Deployment and Implementation](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you've completed the following activities:

-   [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
-   [Defined your project scope](./upgrade-define-project-scope.md)
-   [Understood coexistence and interoperability of Skype for Business and Teams](./teams-and-skypeforbusiness-coexistence-and-interoperability.md)
-   [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
-   [Prepared your environment](./upgrade-prepare-environment.md)
-   [Prepared your organization](./upgrade-prepare-organization.md)
-   [Conducted a pilot](./pilot-essentials.md)

If you've deployed Skype for Business Server or Microsoft Lync on-premises and your organization wants to upgrade to Teams, follow the guidance in this article. You need to set up hybrid connectivity with your Microsoft 365 or Office 365 organization, and determine coexistence requirements if you are moving your users to Teams in phases.

Before you begin, IT Pros and administrators should review the [Important considerations for organizations with Skype for Business Server on-premises](#important-considerations-for-organizations-with-skype-for-business-server-on-premises) later in this article.

> [!IMPORTANT]
> Skype for Business Online will be retired on July 31, 2021, after which it will no longer be accessible or supported. To maximize benefit realization and ensure your organization has proper time to implement your upgrade, we encourage you to begin your journey to Microsoft Teams today. Remember that a successful upgrade aligns technical and user readiness, so be sure to leverage the guidance herein as you navigate your journey to Microsoft Teams.

## Step 1: Configure hybrid connectivity 

The key prerequisite for upgrading your on-premises users to Teams is to configure hybrid connectivity for your Skype for Business Server on-premises deployment. 

Start by reading [Plan hybrid connectivity](/SkypeForBusiness/hybrid/plan-hybrid-connectivity?toc=%2fSkypeForBusiness%2fsfbhybridtoc%2ftoc.json) and then follow the tasks outlined in [Configure hybrid connectivity](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity).


## Step 2: Set transitional coexistence mode (optional)

Coexistence and interoperability between Skype for Business and Teams clients and users are defined by Teams Upgrade modes.  By default, organizations are in Islands mode, which allows users to use both Teams and Skype for Business clients side by side.

For an organization moving to Teams, TeamsOnly mode is the final destination for each user--though not all users need to be assigned TeamsOnly (or any other mode) at the same time.

Prior to users reaching TeamsOnly mode, organizations can optionally use any of the Skype for Business coexistence modes to ensure predictable communication between users who are in TeamsOnly mode and users who aren't yet.  The purpose of the Skype for Business coexistence modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings) is to provide a simple, predictable experience for end users as organizations transition from Skype for Business to Teams. 

When a user is in any of the Skype for Business modes, all incoming chats and calls are routed to the user's Skype for Business client. To avoid end-user confusion and ensure proper routing, calling and chat functionality in the Teams client is disabled when a user is in any of the Skype for Business modes. Similarly, meeting scheduling in Teams is explicitly disabled when users are in the SfBOnly or SfBWithTeamsCollab modes, and explicitly enabled when a user is in the SfBWithTeamsCollabAndMeetings mode.

Depending on your requirements, you can assign the appropriate coexistence mode based on the upgrade path that your organization has chosen. For more information, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) and [Setting your coexistence and upgrade settings](./setting-your-coexistence-and-upgrade-settings.md).


## Step 3: Move users from Skype for Business on-premises to Teams Only

Ultimately, you'll want to move your users to TeamsOnly mode. This might involve one or two steps depending on your on-premises environment.  

For more information, see [Move users between on-premises and the cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud) and [Move users from on-premises to Teams](/SkypeForBusiness/hybrid/move-users-from-on-premises-to-teams). 

## Step 4: Disable hybrid to complete your migration to the cloud

After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment. For more information, see [Disable hybrid to complete migration to the cloud](/skypeforbusiness/hybrid/cloud-consolidation-disabling-hybrid).


## Phone System and PSTN connectivity options

Phone System with Teams is supported after the user is in TeamsOnly mode. (If the user is in Islands mode, Phone System is only supported with Skype for Business.) 

### PSTN connectivity options

When considering Public Switched Telephone Network (PSTN) connectivity options, there are two possible scenarios when moving from Skype for Business on premises to TeamsOnly mode:

- A user in Skype for Business on-premises with Enterprise Voice, who will be moving to online and using a Microsoft Calling plan. Migrating this user to Teams requires moving the user’s on-premises Skype for Business account to the cloud, and coordinating that move with either A) the port of that user’s phone number to a Microsoft Calling Plan or B) assigning a new subscriber number from available regions.  For more information, see [From Skype for Business Server on-premises, with Enterprise Voice, to Microsoft Calling Plan](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-server-on-premises-with-enterprise-voice-to-microsoft-calling-plan).

- A user in Skype for Business on-premises with Enterprise Voice, who will be moving to online and keeping on-premises PSTN connectivity. Migrating this user to Teams requires moving the user’s on-premises Skype for Business account to the cloud, and coordinating that move with migration of the user to Direct Routing. For more information, see [From Skype for Business Server on-premises, with Enterprise Voice, to Direct Routing](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-server-on-premises-with-enterprise-voice-to-direct-routing).


## Important considerations for organizations with Skype for Business Server on-premises

- The following articles describe important upgrade concepts and coexistence behaviors:
    - [Coexistence of Teams and Skype for Business](teams-and-skypeforbusiness-coexistence-and-interoperability.md)
    - [Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md)
    - [Teams client experience and conformance to coexistence modes](teams-client-experience-and-conformance-to-coexistence-modes.md)

- Setting up Skype for Business hybrid is a prerequisite to migrate to TeamsOnly mode. While it is possible for on-premises Skype for Business Server users to use Teams in Islands mode without hybrid, the transition to TeamsOnly mode cannot be made without moving the user to the cloud using [Move-CsUser](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud), for which hybrid connectivity is required. For more information, see [Configure hybrid connectivity](/skypeforbusiness/hybrid/configure-hybrid-connectivity). Also, the upcoming retirement of Skype for Business Online will not change this requirement. For organizations to move from Skype for Business Server to Teams, they must still set up and configure hybrid using the same toolset, *exactly as before the retirement*.

- To move an on-premises user to the cloud, use `Move-CsUser` in the on-premises administration tools. Currently if this switch is not specified, users transition from being homed in Skype for Business Server on-premises to Skype for Business Online, their mode remains unchanged, and meetings they organized in Skype for Business Server are migrated to Skype for Business Online. Because of the upcoming retirement of Skype for Business Online, it will soon no longer be required to specify the `-MoveToTeams` switch in `Move-CsUser` to move users directly from on-premises to TeamsOnly.  After retirement, when moving a user from on-premises to the cloud with `Move-CsUser`, users will automatically be assigned TeamsOnly mode and their meetings from on-premises will be automtically converted to Teams meetings, just as if the `-MoveToTeams switch had been specified`, regardless of whether the switch is actually specified. We expect to release this functionality before the actual retirement of July 31, 2021.

- If your organization has Skype for Business Server and you have not configured hybrid connectivity but you still want to use Teams, to administer Teams functionality you must use an administrative account that has an .onmicrosoft.com domain. Without hybrid connectivity, the administrative tools won't recognize your on-premises domains. 

- Teams users who have a Skype for Business account on-premises (that is, they have not yet been moved to the cloud by using Move-CsUser) cannot interoperate with any Skype for Business users, nor can they federate with external users. This functionality is only available once the users are moved to the cloud and are TeamsOnly users. 

- If you have any users with Skype for Business accounts on-premises or if you still have a lyncdiscover DNS record for an on-premises deployment, you cannot assign TeamsOnly mode at the tenant level. You must first move all users with on-premises Skype for Business accounts to the cloud using `Move-CsUser` and then follow the steps described in [Disable hybrid to complete migration to the cloud](/skypeforbusiness/hybrid/cloud-consolidation-disabling-hybrid) which includes removal of DNS entries.  `Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams` will not work at the tenant level if a lyncdiscover DNS record is detected that points to a location other than Office 365.

- You must ensure your users are properly synchronized into Azure AD with the correct Skype for Business attributes. These attributes are all prefixes with “msRTCSIP-”. If users are not synchronized properly to Azure AD, the management tools in Teams will not be able to manage these users. (For example, you won’t be able to assign Teams policies to on-premises users unless you are properly syncing these attributes.) For more information, see [Configure Azure AD Connect for Teams and Skype for Business](/SkypeForBusiness/hybrid/configure-azure-ad-connect).

- To create a new TeamsOnly or Skype for Business Online user in a hybrid organization, *you must first enable the user in Skype for Business Server on-premises*, and then move the user from on-premises to the cloud using Move-CsUser.  Creating the user in on-premises first ensures that any other remaining on-premises Skype for Business users will be able route to the newly created user. Once all users have been moved online, it is no longer necessary to first enable users in on-premises.

- If you would like display notifications in the Skype for Business client for on-premises users, you must use TeamsUpgradePolicy in the on-premises toolset. Only the NotifySfbUsers parameter is relevant for on-premises users.  On-premises users receive their mode from the online instances of TeamsUpgradePolicy. See the notes in [Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps). 

>[!NOTE]
> Any new tenants created after Sept 3, 2019 are created as TeamsOnly tenants unless the organization already has an on-premises deployment of Skype for Business Server. Microsoft uses DNS records to identify on-premises Skype for Business Server organizations. If your organization has on-premises Skype for Business Server with no public DNS entries, you will need to call Microsoft Support to have your new tenant downgraded. 

## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)
