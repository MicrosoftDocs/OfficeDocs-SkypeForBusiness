---
title: Upgrade strategies for IT administrators
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: The article is for IT administrators and describes strategies for implementing their upgrade from Skype for Business to Teams.
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

# Upgrade strategies for IT administrators

![Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage.](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is for IT administrators who want to implement their upgrade to Teams from Skype for Business.

Before implementing your upgrade, we recommend the following articles which describe important upgrade concepts and coexistence behaviors:

- [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)
- [Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md)
- [Teams client experience and conformance to coexistence modes](teams-client-experience-and-conformance-to-coexistence-modes.md)

## Upgrade options

This section describes how to implement your upgrade by using one of the following upgrade options:

- [Overlapping capabilities upgrade (using Islands mode)](#overlapping-capabilities-upgrade-using-islands-mode)
- [A select capabilities upgrade for an organization that has not yet started using Teams](#a-select-capabilities-upgrade-for-an-organization-that-has-not-yet-started-using-teams)
- [A select capabilities upgrade for an organization that is already using Teams in Islands mode](#a-select-capabilities-upgrade-for-an-organization-that-is-already-using-teams-in-islands-mode)

If you need more information about the options, make sure you have already read [Choose your upgrade journey from Skype for Business to Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md).

## Overlapping capabilities upgrade (using Islands mode)

For the overlapping capabilities upgrade option:

- Consider this option if you can do a fast upgrade for your overall organization.  Since there is potential risk of confusion for end users with running both clients, it's best if you can minimize the time period during which users must run both clients. You should ensure your users know to run both clients.

- This option is the out-of-the box model, and doesn't require administrator action to get started with Teams except to assign the Microsoft 365 or Office 365 license. If your users already have Skype for Business Online, you may already be in this model.

- It can be challenging getting out of overlapping capabilities mode and moving to TeamsOnly. Because upgraded
users only communicate via Teams, any other user in the organization communicating with that user must be using Teams.  If you have users that have not started using Teams, they will be exposed to missing messages. Furthermore, they won't see the TeamsOnly users online in Skype for Business. Some organizations choose to do a tenant-wide upgrade using the Tenant global policy to avoid this, however that requires upfront planning as well as waiting until all users are ready to be upgraded.

## A select capabilities upgrade for an organization that has not yet started using Teams

If your organization does not yet have any active users in Teams, the first step is to set the default tenant-wide policy for TeamsUpgradePolicy to one of the Skype for Business modes, for example, SfbWithTeamsCollab.  Users who have not yet started using Teams won't notice any difference in behavior. However, setting this policy at the tenant level makes it possible to start upgrading users to TeamsOnly mode, and ensures that the upgraded users can still communicate with non-upgraded users.  Once you have identified your pilot users you can upgrade them to TeamsOnly.  If they are on-premises, use Move-CsUser. If they are online, simply assign them TeamsOnly mode by using Grant-CsTeamsUpgradePolicy. By default, any Skype for Business meetings scheduled by these users will be migrated to Teams.

Following are the key commands:

1. Set the tenant-wide default to mode SfbWithTeamsCollab as follows:

   ```PowerShell
   Grant-CsTeamsUpgradePolicy -PolicyName SfbWithTeamsCollab -Global
   ```

2. Upgrade the pilot users to TeamsOnly as follows:

   - For a user who is online:

     ```PowerShell
     Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $username
     ```

   - For a user who is on-premises:

     ```PowerShell
     Move-CsUser -identity $user -Target sipfed.online.lync.com -MoveToTeams -credential $cred
     ```

**Notes**:

- Instead of setting the tenant-wide policy to SfbWithTeamsCollab, you could set it to SfbWithTeamsCollabAndMeetings. This causes all users to schedule all new meetings in Teams.
- By default, Skype for Business meetings are migrated to Teams when upgrading to TeamsOnly mode or when assigning SfbWithTeamsCollabAndMeetings mode.

> [!NOTE]
> In preparation for the upcoming retirement of Skype for Business Online, Microsoft has simplified how organizations move to Teams. It is no longer required to specify the `-MoveToTeams` switch in `Move-CsUser` to move users directly from on-premises directly to TeamsOnly. Previously, if this switch was not specified, users transitioned from being homed in Skype for Business Server on-premises to Skype for Business Online, and their mode remained unchanged. Now when moving a user from on-premises to the cloud with `Move-CsUser`, users are automatically assigned TeamsOnly mode and their meetings from on-premises are automtically converted to Teams meetings, just as if the `-MoveToTeams switch had been specified`, regardless of whether the switch is actually specified. This behavior is available on all versions of Skype For Business Server and Lync Server 2013 (which never had support for `-MoveToTeams`).

The diagram below shows the conceptual phases of select capabilities upgrade for an organization with no prior usage of Teams. The height of the bars represents number of users. During any phase of the upgrade, all users can communicate with each other.  Skype for Business users communicate with TeamsOnly users using Interop, and vice versa. Users in Islands mode must be sure to run both clients.

![Diagram showing select capabilities upgrade with no prior use of Teams.](media/teams-upgrade-1.png)

## A select capabilities upgrade for an organization that is already using Teams in Islands mode

If some users in your organization are actively using Teams in Islands mode, you probably do not want to remove functionality from existing users. Therefore, an extra step is required before changing the tenant-wide policy. The solution is to "grandfather" these existing active Teams users into Islands mode, before setting the tenant-wide policy to SfbWithTeamsCollab.  Once you've done that, you can proceed with deployment as above, however, you'll have two groups of users who are moving to TeamsOnly:  the users who were active in Teams will be in Islands mode, and the remaining users will be in SfbWithTeamsCollab mode. You can progressively move these users to TeamsOnly mode.

1. Find users who are active in Teams as follows:

   1. From the Microsoft 365 admin center, in the left-hand navigation, go to Reports, and then Usage.
   2. In the "Select a report" dropdown, choose Microsoft Teams, and then User Activity. This will provide an exportable table of users who have been active in Teams.
   3. Click Export, open Excel, and filter to show only the users who are active in Teams.

2. For each active Teams user found in step 1, assign them Islands mode in remote PowerShell. This allows you to go to the next step, and ensures you don't change the user experience.

   ```PowerShell
   $users=get-content "C:\MyPath\users.txt"
    foreach ($user in $users){
    Grant-CsTeamsUpgradePolicy -identity $user -PolicyName Islands}
   ```

3. Set the tenant-wide policy to SfbWithTeamsCollab:

   ```PowerShell
   Grant-CsTeamsUpgradePolicy -Global -PolicyName SfbWithTeamsCollab
   ```

4. Upgrade selected users to TeamsOnly mode. You can choose to upgrade either users in Islands mode or SfbWithTeamsCollab mode, although you might want to prioritize upgrading the users in Islands mode first to minimize the potential for confusion that can arise when users are in Islands mode.

   For users homed in Skype for Business Online:

   ```PowerShell
   Grant-CsTeamsUpgradePolicy -Identity $user -PolicyName UpgradeToTeams
   ```

   For users homed in Skype for Business Server on-premises:

   ```PowerShell
   Move-CsUser -Identity $user -Target sipfed.online.lync.com -MoveToTeams -credential $cred
   ```

The diagram below shows the conceptual phases of a select capabilities transition in which there are active Islands users at the start. The height of the bars represents the number of users. During any phase of the upgrade, all users can communicate with each other.  Skype for Business users communicate with TeamsOnly users using interop, and vice versa.

![Diagram showing select capabilities upgrade with active users in Islands mode.](media/teams-upgrade-2.png)

## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy)

[Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)
