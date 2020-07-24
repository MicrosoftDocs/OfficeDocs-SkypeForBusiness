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

## Tools for managing the upgrade

For either of the methods described above, administrators manage the transition to TeamsOnly using [TeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps), which controls a user’s coexistence mode. For more information on each of the modes, see [Coexistence modes](migration-interop-guidance-for-teams-with-skype.md#coexistence-modes).

Whether the administrator performs a select capabilities transition using Skype for Business modes or simply upgrades to TeamsOnly mode from the default Islands configuration, TeamsUpgradePolicy is the primary tool.  Like any other policy in Teams, TeamsUpgradePolicy can be assigned directly to a user, and it can also be set as the tenant-wide default. Any assignment to a user takes precedence over the tenant default setting.  It can be managed both in the Teams Admin Console and in PowerShell.

Administrators can assign any mode of TeamsUpgradePolicy to users whether the user is homed in Skype for Business Online or on-premises, except that TeamsOnly mode can only be assigned to a user who is already homed in Skype for Business Online. This is because interop with Skype for Business users and federation are only possible if the user is homed in Skype for Business Online.

Users with Skype for Business accounts homed on-premises [must be moved online](https://docs.microsoft.com/SkypeForBusiness/hybrid/move-users-from-on-premises-to-teams) (either to Skype for Business Online or direct to Teams) using Move-CsUser in the Skype for Business on-premises toolset. These users can be moved to TeamsOnly in either 1 or 2 steps:

-	1 step:  Specify the -MoveToTeams switch in Move-CsUser. This requires Skype for Business Server 2019 or Skype for Business Server 2015 with CU8.

-	2 steps: After running Move-CsUser, grant TeamsOnly mode to the user using TeamsUpgradePolicy.

Unlike other policies, it is not possible to create new instances of TeamsUpgradePolicy in Microsoft 365 or Office 365. All the existing instances are built into the service.  (Note that mode is a property within TeamsUpgradePolicy, rather than the name of a policy instance.) In some--but not all--cases, the name of the policy instance is the same as mode. In particular, to assign TeamsOnly mode to a user, you will grant the “UpgradeToTeams” instance of TeamsUpgradePolicy to that user. To see a list of all instances, you can run the following command:

```PowerShell
Get-CsTeamsUpgradePolicy|ft Identity, Mode, NotifySfbUsers
```

To upgrade an online user to TeamsOnly mode, assign the “UpgradeToTeams” instance: 

```PowerShell
Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $user 
```

To upgrade an on-premise Skype for Business user to TeamsOnly mode, use Move-CsUser in the on-premises toolset:

```PowerShell
Move-CsUser -identity $user -Target sipfed.online.lync.com -MoveToTeams -credential $cred
```

To change the mode for all users in the tenant, except those who have an explicit per-user grant (which takes precedence), run the following command:

```PowerShell
Grant-CsTeamsUpgradePolicy -PolicyName SfbWithTeamsCollab -Global
```


>[!NOTE]
>If you have any users with Skype for Business accounts on-premises, you should not assign TeamsOnly mode at the tenant level, unless you explicitly assign some other mode to all users with on-premises Skype for Business accounts.


## Using notifications in Skype for Business clients

Administrators have the option to provide end user notifications in the Skype for Business client to inform users that they will soon be upgraded to Teams, as shown in the following diagram. For example, a week before the administrator plans to upgrade a group of users to TeamsOnly mode, the administrator might want to turn on these notifications for that group of users. These notifications are enabled using an instance of TeamsUpgradePolicy with NotifySfbUsers=true.  For all modes other than TeamsOnly, there are actually two instances per mode, corresponding to the two values of NotifySfbUsers.  For all modes other than TeamsOnly, there are actually two instances per mode, corresponding to the two values of NotifySfbUsers. 

![Diagram showing notifications](media/teams-upgrade-sfb-with-notifications.png)

If your users are homed in Skype for Business Online, simply assign the policy instance that has the same mode as the user, but with NotifySfbUsers=true. 

If your users are homed in Skype for Business Server on-premises, you’ll need to use the on-premises toolset and you’ll need Skype for Business Server 2019 or CU8 for Skype for Business Server 2015. In the on-premises PowerShell window, create a new instance of TeamsUpgradePolicy with NotifySfbUsers=true:

```PowerShell
New-CsTeamsUpgradePolicy -Identity EnableNotification -NotifySfbUsers $true
```

Then, using the same on-premises PowerShell window, assign that new policy to the desired users:

```PowerShell
Grant-CsTeamsUpgradePolicy -Identity $user -PolicyName EnableNotification
```

## Meeting migration

When a user is migrated to TeamsOnly mode, by default their existing Skype for Business meetings that they organized will be converted to Teams. You can optionally disable the default behavior when assigning TeamsOnly mode to a user. When moving users from on-premises, meetings must be migrated to the cloud to function with the online user account, but if you do not specify -MoveToTeams, the meetings will be migrated as Skype for Business meetings, rather than converted to Teams. 

When assigning TeamsOnly mode at the tenant level, meeting migration is not triggered for any users. If you wish to assign TeamsOnly mode at the tenant level and migrate meetings, you can use PowerShell to get a list of users in the tenant (for example, using Get-CsOnlineUser with whatever filters are needed) and then loop through each of these users to trigger meeting migration using Start-CsExMeetingMigration. For details, see [Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).


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

