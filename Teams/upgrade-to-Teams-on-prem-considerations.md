---
title: Upgrade to Teams from a Skype for Business on-premises deployment - Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 10/22/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Upgrade from Skype for Business to Teams  
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrade from Skype for Business to Teams &mdash; for IT administrators

This article describes additional considerations for organizations with Skype for Business Server on-premises. This article is the fourth of several that describe upgrade concepts and implementation for IT administrators.  

- [Overview](upgrade-to-teams-on-prem-overview.md)
- [Upgrade methods](upgrade-to-teams-on-prem-upgrade-methods.md)
- [Tools for managing your upgrade](upgrade-to-teams-tools.md)
- **Additional considerations for organizations with Skype for Business on-premises** (this article)
- [Implementing your upgrade](upgrade-to-teams-implement.md)
- [Public Switched Telephone Network (PSTN) considerations](upgrade-to-teams-pstn-considerations.md)

In addition, the following articles describe important upgrade concepts and coexistence behaviors:

- [Coexistence of Teams and Skype for Business](upgrade-to-teams-coexistence.md)
- [Migration and interoperability with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)
- [Teams client experience and conformance to coexistence modes](teams-client-experience-and-conformance-to-coexistence-modes.md)



## Additional considerations for organizations with Skype for Business Server on-premises

- Setting up Skype for Business hybrid is a prerequisite to migrate to TeamsOnly mode. While it is possible to use Teams in Islands mode without hybrid, the transition to TeamsOnly mode cannot be made until the user is moved from Skype for Business on-premises to Skype for Business Online (using [Move-CsUser](https://docs.microsoft.com/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)). For more information, see [Configure hybrid connectivity](https://docs.microsoft.com/skypeforbusiness/hybrid/configure-hybrid-connectivity).

- Teams users who have a Skype for Business account on-premises (that is, they have not yet been moved to the cloud by using Move-CsUser) cannot interoperate with any Skype for Business users, nor can they federate with external users. This functionality is only available once the users are moved to the cloud (either in Islands mode, or as TeamsOnly users). 

- If you have any users with Skype for Business accounts on-premises, you should not assign TeamsOnly mode at the tenant level, unless you explicitly assign some other mode to all users with on-premises Skype for Business accounts. 

- You must ensure your users are properly synchronized into Azure AD with the correct Skype for Business attributes. These attributes are all prefixes with “msRTCSIP-”. If users are not synchronized properly to Azure AD, the management tools in Teams will not be able to manage these users. For more information, see [Configure Azure AD Connect for Teams and Skype for Business](https://docs.microsoft.com/SkypeForBusiness/hybrid/configure-azure-ad-connect).

- To create a new TeamsOnly or Skype for Business Online user in a hybrid organization, *you must first enable the user in Skype for Business Server on-premises*, and then move the user from on-premises to the cloud using Move-CsUser.  Creating the user in on-premises first ensures that any other remaining on-premises Skype for Business users will be able route to the newly created user. Once all users have been moved online, it is no longer necessary to first enable users in on-premises.

- When a user is moved from on-premises to the cloud, meetings organized by that user are migrated to either Skype for Business Online or Teams--depending on whether or not the -MoveToTeams switch is specified.

- If you would like display notifications in the Skype for Business client for on-premises users, you must use TeamsUpgradePolicy in the on-premises toolset. Only the NotifySfbUsers parameter is relevant for on-premises users.  On-premises users receive their mode from the online instances of TeamsUpgradePolicy. See the notes in [Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps). 

>[!NOTE]
> Any new tenants created after Sept 3, 2019 are created as TeamsOnly tenants unless the organization already has an on-premises deployment of Skype for Business Server. Microsoft uses DNS records to identify on-premises Skype for Business Server organizations. If your organization has on-premises Skype for Business Server with no public DNS entries, you will need to call Microsoft Support to have your new tenant downgraded. 



















## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](https://docs.microsoft.com/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](https://docs.microsoft.com/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)

