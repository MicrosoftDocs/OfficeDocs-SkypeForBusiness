---
title: Tools for upgrading to Teams from a Skype for Business on-premises deployment
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Tools for upgrade from Skype for Business to Teams 
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Tools for upgrading to Teams &mdash; for IT administrators

This article describes tools for upgrading to Teams from Skype for Business. 

Before beginning your upgrade, Microsoft recommends the following articles that describe important upgrade concepts and coexistence behaviors:

- [Coexistence of Teams and Skype for Business](teams-and-skypeforbusiness-coexistence-and-interoperability.md)
- [Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md)
- [Teams client experience and conformance to coexistence modes](teams-client-experience-and-conformance-to-coexistence-modes.md)

## Tools for managing the upgrade

Whichever upgrade method you choose, for users that already have Skype for Business Online, you manage the transition to TeamsOnly using [TeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps), which controls a user’s coexistence mode. For users with an on-premises account in Skype for Business Server, you also use `Move-CsUser` to [move them to the cloud](/skypeforbusiness/hybrid/move-users-between-on-premises-and-cloud).  For more information on each of the modes, see [Coexistence modes](migration-interop-guidance-for-teams-with-skype.md).

> [!NOTE]
> If you are currently using Skype for Business Online Connector to manage your services, you will need to move to the Teams PowerShell module and update your existing PowerShell scripts. See [Move from Skype for Business Online Connector to the Teams PowerShell module](teams-powershell-move-from-sfbo.md) for more information.

Whether you perform a select capabilities transition using Skype for Business modes or simply upgrade to TeamsOnly mode from the default Islands configuration, TeamsUpgradePolicy is the primary tool.Like any other policy in Teams, you can assign TeamsUpgradePolicy directly to a user. You can also set the policy as the tenant-wide default. Any assignment to a user takes precedence over the tenant default setting.  You can manage the policy in the Teams Admin Console and in PowerShell.

You can assign any mode of TeamsUpgradePolicy, except for TeamsOnly mode, to users homed in Skype for Business on-premises. Conversely, users homed in the cloud can only be assigned TeamsOnly mode. **TeamsOnly mode can only be assigned to a user who is already homed in the cloud** because interop and federation with Skype for Business users as well as Microsoft 365 Phone System functionality are only possible if the user is homed in Skype for Business Online.  Further, **you can't assign TeamsOnly mode as the tenant-wide default if you have a Skype for Business on-premises deployment** (which is detected by presence of a lyncdiscover DNS record that points to location other than Office 365. For details, see [Disable your hybrid configuration to complete migration to Teams Only](/SkypeForBusiness/hybrid/cloud-consolidation-disabling-hybrid).

Users with Skype for Business accounts homed on-premises [must be moved online](/SkypeForBusiness/hybrid/move-users-from-on-premises-to-teams) to Teams Only mode using Move-CsUser in the Skype for Business on-premises toolset. 

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
Move-CsUser -identity $user -Target sipfed.online.lync.com -credential $cred
```

To change the mode for all users in the tenant, except those who have an explicit per-user grant (which takes precedence), run the following command:

```PowerShell
Grant-CsTeamsUpgradePolicy -PolicyName SfbWithTeamsCollab -Global
```


>[!NOTE]
>If you have any users with Skype for Business accounts on-premises, you cannot assign TeamsOnly mode at the tenant level. You must move these users individually to Teams Only mode using Move-CsUser.


## Using notifications in Skype for Business clients

Administrators have the option to provide end user notifications in the Skype for Business client to inform users that they will soon be upgraded to Teams, as shown in the following diagram. For example, a week before the administrator plans to upgrade a group of users to TeamsOnly mode, the administrator might want to turn on these notifications for that group of users. These notifications are enabled using an instance of TeamsUpgradePolicy with NotifySfbUsers=true.  For all modes other than TeamsOnly, there are actually two instances per mode, corresponding to the two values of NotifySfbUsers.  For all modes other than TeamsOnly, there are actually two instances per mode, corresponding to the two values of NotifySfbUsers. 

![Diagram showing notifications](media/teams-upgrade-sfb-with-notifications.png)

If your users are homed in Skype for Business Online, simply assign the policy instance that has the same mode as the user, but with NotifySfbUsers=true. 

If your users are homed in Skype for Business Server on-premises, you’ll need to use the on-premises toolset and you’ll need Skype for Business Server 2019 or CU8 for Skype for Business Server 2015. For users homed in Skype for Business Server on-premises, the mode property from the online instance of TeamsUpgradePolicy is honored, but the NotifySfbUsers property is not. If notifications are desired, you must create an on-premises instance of TeamsUpgradePolicy to control the client behavior. 

In the on-premises PowerShell window, create a new instance of TeamsUpgradePolicy with NotifySfbUsers=true:

```PowerShell
New-CsTeamsUpgradePolicy -Identity EnableNotification -NotifySfbUsers $true
```

Then, using the same on-premises PowerShell window, assign that new policy to the desired users:

```PowerShell
Grant-CsTeamsUpgradePolicy -Identity $user -PolicyName EnableNotification
```

## Meeting migration

When a user is migrated to TeamsOnly mode, by default their existing Skype for Business meetings that they organized will be converted to Teams. You can optionally disable the default behavior when assigning TeamsOnly mode to a user. When moving users from on-premises, meetings must be migrated to the cloud to function with the online user account, but if you do not specify -MoveToTeams, the meetings will be migrated as Skype for Business meetings, rather than converted to Teams. 

When assigning TeamsOnly mode at the tenant level, meeting migration is not triggered for any users. If you wish to assign TeamsOnly mode at the tenant level and migrate meetings, you can use PowerShell to get a list of users in the tenant (for example, using Get-CsOnlineUser with whatever filters are needed) and then loop through each of these users to trigger meeting migration using Start-CsExMeetingMigration. For details, see [Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).



## Related links

[Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)
