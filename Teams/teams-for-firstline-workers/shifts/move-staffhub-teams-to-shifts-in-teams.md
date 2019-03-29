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
> Effective October 1, 2019, Microsoft StaffHub will be retired. We’re building StaffHub capabilities into Microsoft Teams. Today, Teams includes the Shifts app for schedule management and additional capabilities will roll out over time. StaffHub will stop working for all users on October 1, 2019. Anyone who tries to open StaffHub will be shown a message directing them to download Teams.  

The Shifts app in Teams provides a simple approach to managing schedules and the constant flow of shift swaps and cancellations that occur on a daily basis. Team members can access their schedule and shift information directly in the app and across their devices to set their preferences, manage their schedules, and request time off.

This article walks you through how to move your organization’s StaffHub teams and schedule data to Shifts in Teams. Whether you’re a small business with one or two StaffHub teams or a large enterprise with hundreds of StaffHub teams, here you’ll find the admin guidance you need to help make your transition to Teams successful. 

You must be a global admin to perform the steps in this article. If you haven't already done so, have a look through the [StaffHub retirement FAQ](microsoft-staffhub-to-be-retired.md) to get answers to any questions you may have. 

## What you need to know about the move to Teams

### When to move to Teams

Effective October 1, 2019, StaffHub will be retired. We encourage you to start using Teams today and begin to transition your organization's teams and users from StaffHub. With schedule management being the most commonly-used feature in StaffHub, we recommend you use the Shifts app in Teams moving forward.

### What is moved to Teams

User details, schedule information, and chat and file data are transitioned to Teams. This includes team membership, team schedules, and chats and files from the last 90 days.

Every StaffHub team needs a corresponding Office 365 Group. If a StaffHub team doesn't have an Office 365 Group associated with it, one is automatically created for you to support the transition. Given the difference in team and group naming between Teams and StaffHub, you may see a different team name in Teams.

As you transition teams from StaffHub to Teams, users will no longer have access to their schedules in StaffHub and are redirected to Shifts in Teams. We recommend you communicate this change across your organization to minimize disruption and to encourage users to adopt and explore Teams.

## Prepare

Here's how to prepare for the move to Teams.

### Assign Teams licenses

Each user must have an active Microsoft 365 or Office 365 license from [an eligible plan ](microsoft-staffhub-to-be-retired.md#which-plans-is-shifts-available-in) and must be assigned a Teams license. Assigning a Teams license to users gives them access to Teams.

You manage Teams licenses in the Microsoft 365 admin center. To learn more, see [Manage user access to Teams](../../user-access.md).

> [!NOTE]
> If your organization uses Skype for Business and you’re not ready to move all your users to Teams, you can enable Teams for your Firstline Workers who can then run Teams alongside Skype for Business. In this coexistence mode, called *Islands*, each client app operates as a separate solution. To learn more, see [Understand Teams and Skype for Business coexistence and interoperability](../../teams-and-skypeforbusiness-coexistence-and-interoperability.md).

### Provision accounts for StaffHub users who don't have an identity in Azure AD

Each manager and team member must have an identity in Azure Active Directory (Azure AD). If a user doesn't already have an identity in Azure AD, provision an account for them. Here's how.

- StaffHub team owners and managers can convert a dummy or inactive account and link it to a provisioned account in StaffHub by changing the user's email address to a valid UPN on the StaffHub team settings page.

- Admins can run the [Add-StaffHubMember](https://docs.microsoft.com/powershell/module/staffhub/add-staffhubmember?view=staffhub-ps) and [Remove-StaffHubUser](https://docs.microsoft.com/powershell/module/staffhub/Remove-StaffHubUser?view=staffhub-ps) cmdlets to remove a non-provisioned account from a StaffHub team and add the account back by using the UPN.

## Run a pilot

We recommend you start by moving two or three StaffHub teams for a select group of early adopters. Running a pilot helps you refine your transition plan and ensure you're ready to move all your organization's StaffHub teams to Teams. It also identifies champions who can help drive adoption across your organization. If you're a small business who doesn't need a phased approach, the steps in this section may be all you need to make the switch from StaffHub to Teams.

- **Identify pilot teams**. Reach out to identify two or three pilot teams. All team members should commit to using Shifts in Teams to manage their schedules and communicate and collaborate with each other.
- **Identify team champions**. Identify champions across pilot teams and enlist them to help evangelize and drive adoption of Shifts. Team champions are passionate about what they do, sharing their own learnings to offer support and guidance to team members. Team champions can be the team owner or manager.

When you've identified your pilot teams and team champions, you're ready to transition them to Shifts in Teams. You might want to hold a kickoff meeting with team champions to discuss the pilot and get them to experience Shifts. 

Team champions should ensure team members are set up by dedicating time for everyone to [get Teams clients](../../get-clients.md), check out their schedules in Shifts, and start chatting with each other. Users who are already familiar with StaffHub will be up and running quickly in Shifts. You can also point them to [Shifts Help](https://support.office.com/article/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b) for additional help.

## Make the transition from StaffHub to Shifts

### Raise awareness

When you're ready to go beyond your pilot teams and move your organization's StaffHub team to Teams, it's important to communicate the change across your organization.

### Move your StaffHub teams

### Monitor Teams usage

Usage reports can help you better understand usage patterns and give you insights on where to prioritize training and communication efforts across your organization. Because Shifts is an app in Teams, you can view usage through Teams reports. For more information, see [Teams reporting in the Microsoft Teams admin center](../../teams-analytics-and-reports/teams-reporting-reference.md) and [Teams activity reports in the Microsoft 365 admin center](../../teams-activity-reports.md).

++++++++

## Before you start

Install and connect to the [StaffHub PowerShell module](https://www.powershellgallery.com/packages/MicrosoftStaffHub/1.0.0-alpha).

When you move a StaffHub team, the move request checks for prerequisites. Here's reasons why a move request may fail:

- The signed in user is not a global admin
- Teams is disabled in the tenant
- Office 365 Groups creation is disabled in the tenant
- The StaffHub teamId is not valid or has no members
- The StafffHub team includes members that aren't linked to an Azure AD account  

## Move a StaffHub team

Run the following to move a StaffHub team.

```
Move-StaffHubTeam -Identity <String>
```
Here's an example of the response you receive when a team is moved to Teams. 
```
    jobId   teamId                                      teamAlreadyInMicrosofteams  
    -----   ------                                      ------------          
        1   TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f   True
```
To check the status of a move request, run the following.
```
Get-TeamMigrationJobStatus <Int32>
```
Here's an example of the response you receive when a move is in progess.
```
    jobId   status       teamId                                     isO365GroupCreated  Error
    -----   ------       ------                                     ------------------  -----    
        1   InProgress   TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f  True                None
```

## Move your organization's StaffHub teams

Use these steps to move more than one StaffHub team at a time. You can move all your organization's StaffHub teams or move specific StaffHub teams.

### Move all StaffHub teams

Run the following to get a list of all StaffHub teams in your organization.

```
$StaffHubTeams = Get-StaffHubTeamsForTenant 
```
Run the following to submit the request to move all teams. 
```
$StaffHubTeams | foreach {Move-StaffHubTeam -Identity {$_.Id}}
```
Here's an example of the response you get. 
```
    jobId   teamId                                      teamAlreadyInMicrosofteams  
    -----   ------                                      ------------          
        1   TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f   True
        2   TEAM_81b1f191-3e19-45ce-ab32-3ef51f100000   False
```
### Move specific StaffHub teams

Run the following to get a list of all StaffHub teams in your organization.

```
$StaffHubTeams = Get-StaffHubTeamsForTenant 
```
Create a comma-separated values (CSV) file and add the IDs of the teams you want to move.
Here's an example.

```
Id
TEAM_4bbc03af-c764-497f-a8a5-1c0708475e5f
TEAM_81b1f191-3e19-45ce-ab32-3ef51f100000
TEAM_b42d0fa2-0fc9-408b-85ff-c14a26700000
TEAM_b42d0fa2-0fc9-408b-85ff-c14a26700000
```

Then, run the following to move the teams you specified in the CSV file.

```
Import-Csv .\teams.txt | foreach {Move-StaffHubTeam -Identity {$_.Id}}
```

## Related topics
- [Microsoft StaffHub to be retired](microsoft-staffhub-to-be-retired.md)
- [Manage the Shifts app for your organization in Microsoft Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
- [StaffHub PowerShell reference](https://docs.microsoft.com/powershell/module/staffhub/?view=staffhub-ps).
