---
title: Archive or delete a team in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
audience: admin 
ms.service: msteams
ms.reviewer: jastark
search.appverid: MET150
description: Learn how to archive or permanently delete a team.
localization_priority: Normal
ms.custom:
- NewAdminCenter_Update
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Archive or delete a team in Microsoft Teams
===========================================

Over time, a team created in Microsoft Teams might fall out of use or you might want to archive or delete a team at the end of a project. If you are a Microsoft Teams admin, follow the steps in this article to archive or delete a team that is no longer needed. When you archive a team, all activity for that team ceases, but you can still add or remove members and update roles and you can still view all the team activity in channels, files, and chats. When you delete a team, team activity in associated channels, files, and chats is also deleted. 

> [!IMPORTANT]
> Archived teams can be reactivated, but you can’t directly undelete a team that has been deleted. Consider archiving the team first, and postpone the deletion until you're sure that you no longer need the team.

## Archive a team

Follow these steps to archive a team.

1. In the Microsoft Teams admin center, select **Teams**.
2. Select a team by clicking the team name.
3. Select **Archive**. The following message will appear.

    ![Screenshot of Teams archive message](media/teams-archive-message.png)

4. If you would like to make the SharePoint site for the team read-only, select the check box.
5. Select **Archive** to archive the team. The team’s status will change to **Archived**.

## Make an archived team active

Follow these steps to make an archived team active again.

1. In the Microsoft Teams admin center, select **Teams**.
2. Select a team by clicking the team name.
3. Select **Unarchive**. The team’s status will change to **Active**.

## Delete a team

If the team will not be required in the future, then you can delete it rather than archiving it. Follow these steps to delete a team.

1.	In the Microsoft Teams admin center, select **Teams**.
2.	Select a team by clicking the team name.
3.	Select **Delete**. A confirmation message will appear.
4.	Select **Delete** to permanently delete the team.

## Restore a deleted team

Follow these steps to restore a deleted team by restoring the Office 365 group that's associated with the team. By default, a deleted Office 365 group is retained for 30 days. This 30-day period is called "soft-delete" because you can restore the group. To learn more, see [Restore a deleted Office 365 Group](https://docs.microsoft.com/office365/admin/create-groups/restore-deleted-group).

### Install the AzureADPreview module

1. Open Windows PowerShell as an admin.
2. If you have an earlier version of the AzureADPreview module installed or the AzureAD module installed, uninstall it by running one of the following:

    ``` 
    Uninstall-Module AzureADPreview
    ```

    ```
    Uninstall-Module AzureAD
    ```
3. Install the latest version of the AzureADPreview module by running the following:

    ```
    Install-Module AzureADPreview
    ```    

### Restore the deleted Office 365 group

1. Connect to Azure AD by running the following:
    ```
    Connect-AzureAD
    ```
    When you're prompted, sign in using your admin account and password.  
2. Run the following to display a list of all soft-deleted Office 365 groups that are still within the 30-day retention period. Use the **-All $True** parameter if you have a lot of groups.
    ```
    Get-AzureADMSDeletedGroup
    ``` 
3. Find the group that you want to restore, and then make a note of the Id.
4. Run the following to restore the group, where [Id] is the group Id.
    ```
    Restore-AzureADMSDeletedDirectoryObject -Id [Id]
    ```
5.  Run the following to verify the group was successfully restored, where [Id] is the group Id.
    ```
    Get-AzureADGroup -ObjectId [Id]
    ```

    It can take up to 24 hours for the changes to take effect and for the team to be displayed in Teams.
