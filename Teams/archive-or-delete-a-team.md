---
title: Archive or delete a team in Microsoft Teams
author: SerdarSoysal
ms.author: mikeplum
author: MikePlumleyMSFT
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.reviewer: jastark
search.appverid: MET150
description: In this article, you will learn about how to archive or permanently delete a team in Microsoft Teams.
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
---

# Archive or delete a team in Microsoft Teams

Over time, a team created in Microsoft Teams might fall out of use or you might want to archive or delete a team at the end of a project. If you're a Microsoft Teams admin, follow the steps in this article to archive or delete a team that's no longer needed.

When you archive a team, all activity for that team ceases. Archiving a team also archives private channels in the team and their associated site collections.  However, you can still add or remove members and update roles and you can still view all the team activity in standard and private channels, files, and chats.

When you delete a team, team activity in standard and private channels (and associated site collections), files, and chats are also deleted.

> [!IMPORTANT]
> Archived teams can be reactivated, but you can't directly restore a team that has been deleted. Consider archiving the team first, and postpone the deletion until you're sure that you no longer need the team.

## Archive a team

Follow these steps to archive a team. You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. In the admin center, select **Teams**.
2. Select a team by clicking the team name.
3. Select **Archive**. The following message will appear.

    ![Screenshot of Teams archive message.](media/teams-archive-message.png)

4. To prevent people from editing the content in the SharePoint site and Wiki tab associated with the team, select **Make the SharePoint site read-only for team members**. (Teams owners will still be able to edit this content.)
5. Select **Archive** to archive the team. The team's status will change to **Archived**, it will be moved inside **Hidden teams** located at the bottom of the teams list, and a small icon representing the archived state will be added next to it.

## Make an archived team active

Follow these steps to make an archived team active again.

1. In the admin center, select **Teams**.
2. Select a team by clicking the team name.
3. Select **Restore**. The team's status will change to **Active**. Note that it will not be moved back inside **Your teams** automatically.

## Delete a team

If the team will not be required in the future, then you can delete it rather than archiving it. Follow these steps to delete a team.

1. In the admin center, select **Teams**.
2. Select a team by clicking the team name.
3. Select **Delete**. A confirmation message will appear.
4. Select **Delete** to permanently delete the team.

## Restore a deleted team

Follow these steps to restore a deleted team by restoring the Microsoft 365 group that's associated with the team. Restoring the Microsoft 365 group for a team restores team content, including tabs, standard channels, and private channels and their associated site collections.

By default, a deleted Microsoft 365 group is retained for 30 days. This 30-day period is called "soft-delete" because you can restore the group. To learn more, see [Restore a deleted Group](/microsoft-365/admin/create-groups/restore-deleted-group).

### Install the AzureADPreview module

1. Open Windows PowerShell as an admin.
2. If you have an earlier version of the AzureADPreview module installed or the AzureAD module installed, uninstall it by running one of the following:

    ```PowerShell
    Uninstall-Module AzureADPreview
    ```

    ```PowerShell
    Uninstall-Module AzureAD
    ```

3. Install the latest version of the AzureADPreview module by running the following:

    ```PowerShell
    Install-Module AzureADPreview
    ```

### Restore the deleted Microsoft 365 group

1. Connect to Azure AD by running the following:

    ```PowerShell
    Connect-AzureAD
    ```

    When you're prompted, sign in using your admin account and password.

1. Run the following to display a list of all soft-deleted Microsoft 365 groups that are still within the 30-day retention period. Use the **-All $True** parameter if you have many groups.

    ```PowerShell
    Get-AzureADMSDeletedGroup
    ```

1. Find the group that you want to restore, and then make a note of the `Id`.
1. Run the following to restore the group, where `[Id]` is the group ID.

    ```PowerShell
    Restore-AzureADMSDeletedDirectoryObject -Id [Id]
    ```

1. Run the following to verify the group was successfully restored, where `[Id]` is the group ID.

    ```PowerShell
    Get-AzureADGroup -ObjectId [Id]
    ```

    It can take up to 24 hours for the restore process to complete, after which the team and content associated with the team, including tabs and channels, is displayed in Teams.

## Related topics

- [Archive or restore a team](https://support.microsoft.com/office/archive-or-restore-a-team-dc161cfd-b328-440f-974b-5da5bd98b5a7)

