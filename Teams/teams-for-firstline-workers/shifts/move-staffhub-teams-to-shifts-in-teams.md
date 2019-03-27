---
title: Move your StaffHub teams to Shifts in Microsoft Teams
author: LanaChin
ms.author: v-lanac
ms.reviewer: lisawu
manager: serdars
ms.date: 1/10/2019
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Learn how to migrate your Microsoft StaffHub teams and schedule data to Shifts in Microsoft Teams.
localization_priority: Normal
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Move your Microsoft StaffHub teams to Shifts in Microsoft Teams

> [!IMPORTANT]
> Effective October 1, 2019, Microsoft StaffHub will be retired. We’re building StaffHub capabilities, including schedule and task management, into Microsoft Teams. Additional capabilities for firstline workers will roll out over time. StaffHub will stop functioning for all users on October 1, 2019 and users who try to open it will be shown a message directing them to download Teams.  

With the Shifts app in Microsoft Teams, firstline managers in your organization can create and manage schedules and firstline workers can view their upcoming shifts, set availability, request to swap or offer a shift, and request time off, all from their mobile devices.  

This article walks you through how to move your organization’s StaffHub teams and schedule data to Shifts in Teams. Whether you’re a small business with one or two StaffHub teams or a large enterprise with hundreds of StaffHub teams, here you’ll find the admin guidance you need to help make your transition to Teams successful.

## What you need to know about the move to Teams

### When to move to Teams

### What is moved to Teams

When you move a StaffHub team to Shifts in Teams, here's what happens:

- Every StaffHub team needs an Office 365 Group. If a StaffHub team doesn't have an Office 365 Group, an Office 365 Group is automatically created for you to support the move to Teams. The team name in Teams uses the Office 365 Group name, so you'll see a different name when you switch over to Teams.
- The following is moved to Teams:
    - Team membership
    - Team schedule and time clock data
    - Chat data from the last 90 days
    - Files from the last 90 days

After you move a StaffHub team to Teams, members of that team will no longer be able access their schedule in StaffHub. They will be redirected to Shifts in Teams.

## Prepare

Here are the steps to take to prepare for the move to Teams.

### Assign Teams licenses

Teams is enabled by assigning Teams licenses to users. Firstline workers and managers in your organization must have a Teams license, which gives them access to Teams. Shifts is available in all Office 365 subscriptions that include Teams with the exceptions of US Government Cloud Community (GCC) and Teams free.

You manage Teams licenses in the Microsoft 365 admin center. To learn more, see [Office 365 licensing for Teams](../../Office-365-licensing.md) and [Manage user access to Teams](../../user-access.md).

> [!NOTE]
> If your organization uses Skype for Business and you’re not ready to move all your users to Teams, you can enable Teams for your firstline workers and managers who can then run Teams alongside Skype for Business. In this coexistence mode, called *Islands*, each client app operates as a separate solution. To learn more, see [Understand Teams and Skype for Business coexistence and interoperability](../../teams-and-skypeforbusiness-coexistence-and-interoperability.md).

### Provision accounts for StaffHub users who don't have an identity in Azure AD

Each firstline worker and manager must have an identity in Azure Active Directory (Azure AD). If they don't already have an identity in Azure AD, provision an Office 365 account for them. Here's how.

- StaffHub team owners/managers can convert a dummy/inactive accounts and link them with a provisioned account in StaffHub by going to the team settings page and updating the e-mail address to a valid UPN.
- Administrators can run the Add-StaffHubMember and Remove-StaffHubUser cmdlets to remove a non-provisioned account from a StaffHub team and add them back with their UPN.

#### Firstline managers and team owners

#### Admins
Before you start you'll need to install and connect to the StaffHub PowerShell modules. Instructions on installing the StaffHub module can be found here: https://www.powershellgallery.com/packages/MicrosoftStaffHub/1.0.0-alpha 

Here you will find all of the Microsoft StaffHub PowerShell help topics. The reference documentation can be found here: https://docs.microsoft.com/powershell/module/staffhub/?view=staffhub-ps

#### How to move a StaffHub team
When moving a StaffHub team the request will check all of the pre-requisites listed above. The following list provides a list of reasons why a move request would fail.
- Logged in user is not a global admin
- Microsoft Teams is disabled in the tenant
- Office 365 Groups creation is disabled in the tenant
- The StaffHub teamId is not valid or has no members
- There are members on the StaffHub that are not linked to an Azure Active Directory account

##### Move a StaffHub team in your organization

```
Move-StaffHubTeam -Identity <String>
```

After you submit the request you will get the following sample response
```
    jobId   teamId                                      teamAlreadyInMicrosofteams  
    -----   ------                                      ------------          
        1   TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f   True
```
To check the status of your move job you can use this commandlet
```
Get-TeamMigrationJobStatus <Int32>
```
The following is an example response
```
    jobId   status       teamId                                     isO365GroupCreated  Error
    -----   ------       ------                                     ------------------  -----    
        1   InProgress   TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f  True                None
```

##### Move your organization's StaffHub teams
To move more than one team from StaffHub to Microsoft teams, below is an example of how you can use the Move-StaffHubTeam commandlet to move more than one team at a time.

Move all the StaffHub teams in your organization of teams.

##### Get a list of all of your StaffHub teams in your organization

```
$StaffHubTeams = Get-StaffHubTeamsForTenant 
```

Submit the request to move all teams. 
```
$StaffHubTeams | foreach {Move-StaffHubTeam -Identity {$_.Id}}
```

After you submit the request you will get the following sample response
```
    jobId   teamId                                      teamAlreadyInMicrosofteams  
    -----   ------                                      ------------          
        1   TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f   True
        2   TEAM_81b1f191-3e19-45ce-ab32-3ef51f100000   False
```
To move a list of teams from your organization you'll want to create a comma-delimited file and save a list of the Ids of the teams you want to move.

For example:

Id
TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f
TEAM_81b1f191-3e19-45ce-ab32-3ef51f100000
TEAM_b42d0fa2-0fc9-408b-85ff-c14a26700000
TEAM_b42d0fa2-0fc9-408b-85ff-c14a26700000

After you save the file, you can reference the file to move more than one team. Here is an example

```
Import-Csv .\teams.txt | foreach {Move-StaffHubTeam -Identity {$_.Id}}
```

### 
### Get Teams clients

Teams has clients for desktop (Windows and Mac), web, and mobile (iOS and Android). To learn more, go to [Get clients for Teams](../../get-clients.md).

## Monitor Teams usage

## Related topics
- [Microsoft StaffHub to be retired](microsoft-staffhub-to-be-retired.md)
- [Manage the Shifts app for your organization in Microsoft Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
