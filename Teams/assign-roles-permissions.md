<<<<<<< HEAD:Teams/Assign_roles_and_permissions_in_Microsoft_Teams.md
---
title: Assign roles and permissions in Microsoft Teams | Microsoft Support
author: LolaJacobsen
ms.author: lolaj
manager: serdar
ms.date: 08/10/2017
ms.topic: solution
ms.prod: teams
description: Learn to assign team owner and member roles and permissions in Microsoft Teams including permissions to create teams.
---

Assign roles and permissions in Microsoft Teams
===============================================

Within Microsoft Teams there are two roles: **Owner** and **Member**. By default, a user that creates a new team is granted the Owner status. If a team is created from an existing Office 365 Group, permissions are inherited.

The table below shows the difference in permissions between an owner and a member:

|  |Team Owner  |Team Member  |
|---------|---------|---------|
|**Create team**     |Yes        |No         |
|**Leave team**     |Yes         |Yes         |
|**Edit team name/description**      |Yes         |No         |
|**Delete team**      |Yes         |No         |
|**Add channel**      |Yes         |Yes*         |
|**Edit channel name/description**      |Yes         |Yes*         |
|**Delete channel**      |Yes         |Yes*         |
|**Add members**      |Yes**         |No         |
|**Add tabs**      |Yes         |Yes*         |
|**Add connectors**      |Yes         |Yes*         |
|**Add bots**      |Yes         |Yes*         |
\* These items can be turned off by an owner at a team level, in which case members would not have access to that.

\*\*After adding a member to a team, an Owner can also promote a Member to Owner status. It is also possible for an Owner to demote their own status to a Member.


| | |
|---------|---------|
|![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image1.png) <br></br>Note     |Owners can make other members owners in the View teams option. A team can have up to 10 owners.         |

Permissions to create teams
---------------------------

By default, all users with a mailbox in Exchange Online have permissions to create Office 365 groups and therefore a team within Microsoft Teams. You can have tighter control and restrict the creation of new teams and thus the creation of new Office 365 groups by delegating group creation and management rights to a set of users.

If your organization is interested in doing this, the instructions below outlines the tasks required to do so.

1.  Identify or create a security group (SG) of users who will have delegated permissions to create Office 365 groups.

    a.  **Action:** Set up a security group in Office 365 so you can add your users who can create Office 365 groups.

    b.  For more information, see [Create, edit, or delete a security group in the Office 365 admin center](https://support.office.com/article/Create-edit-or-delete-a-security-group-in-the-Office-365-admin-center-55c96b32-e086-4c9e-948b-a018b44510cb).

2.  Verify that the company-wide control for users to create groups is enabled.

    a.  **Action:** Run the following PowerShell script and verify UsersPermissiontoCreateGroupsEnabled parameter is set to **True.**

    Connect-MsolService

    Get-MsolCompanyInformation

    b. 	If this is not true, run the Set-MsolCompanySettings  cmdlet **to set it to True**.
Set-MsolCompanySettings -UsersPermissionToCreateGroupsEnabled $True


    c. For more information, see: [Manage Office 365 Group Creation](https://support.office.com/en-us/article/Manage-Office-365-Group-Creation-4c46c8cb-17d0-44b5-9776-005fced8e618?ui=en-US&rs=en-001&ad=US#checkclevelsettings).

<!-- -->

3.  Configure Office 365 Group settings to allow only identified security group has permissions to create groups

    a.  **Action:** Create a group settings object that contains the configuration settings of the group that will be assigned delegated permissions to create groups. 

    Connect-AzureAD

    $Template = Get-AzureADDirectorySettingTemplate -Id 62375ab9-6b52-47ed-826b-58e47e0e304b

    $Setting = $template.CreateDirectorySetting()

    $setting["EnableGroupCreation"] = "false"

    $setting["GroupCreationAllowedGroupId"] = "&lt;ObjectId of Group Allowed to Create Groups>"

    New-AzureADDirectorySetting -DirectorySetting $settings

    b. For more information, see: [Manage Office 365 Group Creation](https://support.office.com/en-us/article/Manage-Office-365-Group-Creation-4c46c8cb-17d0-44b5-9776-005fced8e618?ui=en-US&rs=en-US&ad=US#step3)


||||
|---------|---------|---------|
| ![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image2.png)     |Decision Point         |Will all Microsoft Teams users be able to create Teams (recommended)?         |
| ![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image3.png)    |Next Steps         |Modify the default permissions for who can create Office 365 groups if you need to limit who can create Teams         |

=======
---
title: Assign roles and permissions in Microsoft Teams | Microsoft Support
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
description: Learn to assign team owner and member roles and permissions in Microsoft Teams including permissions to create teams.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Assign roles and permissions in Microsoft Teams
===============================================

Within Microsoft Teams there are two roles: **Owner** and **Member**. By default, a user that creates a new team is granted the Owner status. If a team is created from an existing Office 365 Group, permissions are inherited.

The table below shows the difference in permissions between an owner and a member:

|  |Team Owner  |Team Member  |
|---------|---------|---------|
|**Create team**     |Yes        |No         |
|**Leave team**     |Yes         |Yes         |
|**Edit team name/description**      |Yes         |No         |
|**Delete team**      |Yes         |No         |
|**Add channel**      |Yes         |Yes*         |
|**Edit channel name/description**      |Yes         |Yes*         |
|**Delete channel**      |Yes         |Yes*         |
|**Add members**      |Yes**         |No         |
|**Add tabs**      |Yes         |Yes*         |
|**Add connectors**      |Yes         |Yes*         |
|**Add bots**      |Yes         |Yes*         |
\* These items can be turned off by an owner at a team level, in which case members would not have access to that.

\*\*After adding a member to a team, an Owner can also promote a Member to Owner status. It is also possible for an Owner to demote their own status to a Member.


| | |
|---------|---------|
|![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image1.png) <br></br>Note     |Owners can make other members owners in the View teams option. A team can have up to 10 owners.         |

Permissions to create teams
---------------------------

By default, all users with a mailbox in Exchange Online have permissions to create Office 365 groups and therefore a team within Microsoft Teams. You can have tighter control and restrict the creation of new teams and thus the creation of new Office 365 groups by delegating group creation and management rights to a set of users.

If your organization is interested in doing this, the instructions below outlines the tasks required to do so.

1.  Identify or create a security group (SG) of users who will have delegated permissions to create Office 365 groups.

    a.  **Action:** Set up a security group in Office 365 so you can add your users who can create Office 365 groups.

    b.  For more information, see [Create, edit, or delete a security group in the Office 365 admin center](https://support.office.com/article/Create-edit-or-delete-a-security-group-in-the-Office-365-admin-center-55c96b32-e086-4c9e-948b-a018b44510cb).

2.  Verify that the company-wide control for users to create groups is enabled.

    a. **Action:** Run the following PowerShell script and verify: UsersPermissiontoCreateGroupsEnabled parameter is set to **True.**

    Connect-MsolService

    Get-MsolCompanyInformation
   
    b. If this is not true, run the Set-MsolCompanySettings  cmdet **to set it to True**.
    Set-MsolCompanySettings -UsersPermissionToCreateGroupsEnabled $True
   
    c. For more information, see: [Manage Office 365 Group Creation](https://support.office.com/en-us/article/Manage-Office-365-Group-Creation-4c46c8cb-17d0-44b5-9776-005fced8e618?ui=en-US&rs=en-US&ad=US#checkclevelsettings)

    
    

3.  Configure Office 365 Group settings to allow only identified security group has permissions to create groups

    a.  **Action:** Create a group settings object that contains the configuration settings of the group that will be assigned delegated permissions to create groups. 

    Connect-AzureAD

    $Template = Get-AzureADDirectorySettingTemplate -Id 62375ab9-6b52-47ed-826b-58e47e0e304b

    $Setting = $template.CreateDirectorySetting()

    $setting["EnableGroupCreation"] = "false"

    $setting["GroupCreationAllowedGroupId"] = "&lt;ObjectId of Group Allowed to Create Groups>"

    New-AzureADDirectorySetting -DirectorySetting $settings

    b. For more information, see: [Manage Office 365 Group Creation](https://support.office.com/en-us/article/Manage-Office-365-Group-Creation-4c46c8cb-17d0-44b5-9776-005fced8e618?ui=en-US&rs=en-US&ad=US#step3)


||||
|---------|---------|---------|
| ![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image2.png)     |Decision Point         |Will all Microsoft Teams users be able to create Teams (recommended)?         |
| ![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image3.png)    |Next Steps         |Modify the default permissions for who can create Office 365 groups if you need to limit who can create Teams         |

>>>>>>> 050834e1dcfde1608159b950fd45e68dc633e021:Teams/assign-roles-permissions.md
