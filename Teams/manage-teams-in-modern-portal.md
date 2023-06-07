---
title: Manage teams in the Microsoft Teams admin center
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
search.appverid: MET150
ms.reviewer: islubin, jastark
ms.date: 06/06/2023
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - seo-marvel-apr2020
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
description: Learn how to view or update the teams that your organization has set up for collaboration in the Microsoft Teams admin center.
---

# Manage teams in the Microsoft Teams admin center

This article provides an overview of the management tools for Teams in the Microsoft Teams admin center.

As an admin, you may need to view or update the teams in your organization, or you might need to perform remediation actions such as assigning owners for ownerless teams. You can manage teams through both the Microsoft Teams PowerShell module and the Microsoft Teams admin center. You can access the admin center at <a href="https://admin.teams.microsoft.com" target="_blank">https://admin.teams.microsoft.com</a>. For full administration capabilities using these two toolsets, you should make sure that you're assigned one of the following roles:

- Global administrator
- Teams administrator

You can learn more about admin roles in Teams in [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md), and you can read more about how to use the PowerShell cmdlets for managing teams in the [Microsoft Teams cmdlet reference](/powershell/teams/).

## Teams overview grid

Management tools for teams are under the **Teams** node in the Microsoft Teams admin center. (In the admin center, select **Teams** > **Manage teams**.) Each team is backed by a Microsoft 365 group, and this node provides a view of groups that have been Microsoft Teams-enabled in your organization.

![Screenshot of the Teams overview grid.](media/manage-teams-in-modern-portal-grid.png)  

The grid displays the following properties:

- **Team name**
- **Standard channels** - a count of the standard channels in the team.
- **Private channels** - a count of the private channels in the team.
- **Shared channels** - a count of the shared channels in the team.
- **Team members** - a count of total users, including owners, guests, and members from your tenant.
- **Owners** - a count of owners for this team.
- **Guests** - a count of Azure Active Directory B2B guests who are members of this team.
- **Privacy** - whether the team is public or private.
- **Status** - the Archived or Active status for this team. Learn more about archiving teams in [Archive or restore a team](https://support.office.com/article/dc161cfd-b328-440f-974b-5da5bd98b5a7).
- **Description** - the description of the team.
- **Sensitivity** - the sensitivity label associated with the team. (This columnn may be called *classification* if you haven't set up sensitivity labels.)
- **GroupID** - the unique GroupID of the team.
- **Expiration date** - the date the team is scheduled to expire if the team has an [expiration policy](/microsoft-365/solutions/microsoft-365-groups-expiration-policy).

If you don't see all these properties in the grid, click the **Edit columns** icon. In the **Edit columns** pane, you can use the toggles to turn on or turn off columns in the grid. When you're finished, click **Apply**.

### Add

To add a new team, click **Add**. In the **Add a new team** pane, give the team a name and description, set whether you want to make it a private or public team, and set the sensitivity if needed.

This video shows the steps to create a new team and a channel for them.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE53TXG?autoplay=false]

### Edit

To edit group and team-specific settings, select the team by clicking to the left of the team name, and then select **Edit**.

This video shows the steps to view and edit the details of an existing team.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE53JpG?autoplay=false]

### Archive

[Archiving a team](archive-or-delete-a-team.md) puts the team into read-only mode within Teams. To archive a team, select the team by clicking to the left of the team name, and then select **Archive**.

### Deleted Teams

To restore a deleted team in the Teams admin center, do the following:

 1. Go to the **[Teams Admin center](https://admin-dev.teams.microsoft.net/teams/manage)** > **Teams** > **Manage teams**.
 
 2. Expand **Actions** menu on the top right corner, click **View deleted teams**.
  
 3. Select the team that you want to restore from the list, and then click **Restore**. You can also select multiple teams and restore them.
 
 > [!NOTE]
 > If you do not find the team's detail updated immediately, select **Refresh**. Note that it might take sometime for the team to appear in the **Manage Teams** list.

### Expiring Teams

If you're a Global administrator or a Teams administrator, to renew an expiring team in the Teams admin center, do the following:

 1. Go to the **[Teams Admin center](https://admin-dev.teams.microsoft.net/teams/manage)** > **Teams** > **Manage teams**.
 
 2. Select **Filter**, and in the **Filter** section, do the following:
 
     1. Select **Match all these conditions**. 
     
     2. Choose the **Expiration Date** and select one of values from the list (for example: in the next 7 days, in the next 14 days, or in the next 30 days).
     
     3. Click **Apply**.
 
 4. Select the expiring team that you want to renew, and then click **Renew**. You can also select multiple teams and renew them. 

 > [!NOTE]
 > If you do not find the team's detail updated immediately, select **Refresh**. Note that it might take sometime for the team's details and expiration date to get updated.

### Search

Search currently supports the string "Begins with" and searches the **Team name** field.

## Team profile

You can navigate to the team profile page of any team from the main teams overview grid by clicking  the team name. The team profile page shows the members, owners, and guests that belong to the team (and its backing Microsoft 365 group), as well as the team's channels and settings. From the team profile page, you can:

- Add or remove members and owners.
- Add or remove channels (note that you can't remove the General channel).
- Change team and group settings.
 
![Screenshot of an example team profile.](media/manage-teams-in-modern-portal-team-profile-page.png)

## Making changes to teams

On the team's profile page, you can change the following elements of a team:

- **Members** - add or remove members and promote or demote owners.
- **Channels** - add new channels, and edit or remove existing channels. Remember that you can't delete the default General channel.
- **Team name**
- **Description**
- **Privacy** - set whether the team is public or private.
- **Classification** - this is backed by your Microsoft 365 group classifications. Choose **Confidential**, **Highly Confidential**, or **General**.
- **Conversations settings** - set whether members can edit and delete sent messages.
- **Channels settings** - set whether members can create new channels and edit existing ones, and add, edit, and remove tabs, connectors, and apps.

The changes that you make to a team are logged. If you're modifying group settings (changing the name, description, photo, privacy, classification, or team members), the changes are attributed to you through the audit pipeline. If you're performing actions against Teams-specific settings, your changes are tracked and attributed to you in the General channel of the team.

## Troubleshooting

**Issue: Teams missing from the Team overview grid**

Some of your teams are missing from the list of teams in the Teams overview grid.

**Cause**: This issue occurs when the team was incorrectly (or not yet) profiled by the system, which can lead to a missing property for it to be recognized.

**Resolution: Manually set the property to the correct value via MS Graph**

Replace **{groupid}** in the Query for the actual GroupId in question, which you can get via the Exchange Online PowerShell, with the **"[Get-UnifiedGroup](/powershell/module/exchange/users-and-groups/get-unifiedgroup)"** cmdlet, as the "**ExternalDirectoryObjectId**" attribute.

1. Access [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

2. Sign in to Graph Explorer on the right of the top menu.

3. Change the query line to: PATCH > v1.0 > https://graph.microsoft.com/v1.0/groups/{groupid}.

4. Add the following value on the request body: {"resourceProvisioningOptions": ["Team"]}.

5. Run the query on the top-right.

6. Confirm the team appears correctly in the Microsoft Teams admin center - Team Overview.

## Related topics

[Teams cmdlet reference](/powershell/teams/)  

[Use Teams administrator roles to manage Teams](using-admin-roles.md)

[Plan for lifecycle management in Teams](plan-teams-lifecycle.md)

[Overview of the Microsoft 365 admin center](/microsoft-365/admin/admin-overview/admin-center-overview)
