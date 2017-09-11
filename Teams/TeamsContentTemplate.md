---
title: Article title goes here
author: LolaJacobsen
ms.author: lolaj
manager: serdar
ms.date: 08/10/2017
ms.topic: solution
ms.prod: teams
description: Describe the main intent of the article. This description shows up in internet search results and impacts SEO.
---

Article title goes here
=======================

To format text, use this mark up: **For bold, enclose the test in \****. For italics, *enclose the text in 1 asterisk*.

Use heading formatting to create hierarchy in articles. On docs.microsoft.com, level-2 headings automatically show up in an **In this article** section in the right rail, so you can use level-2 headings to automatically create navigation for your article.

# This is a Heading Level 1

## This is a Heading Level 2

### This is a Heading Level 3

###### Heading Level 6 is as deep as you can go

For a full list of all Markdown formatting & styles, see [Mastering Markdown](https://guides.github.com/features/mastering-markdown/). (By the way, this is what a link looks like. Use the Link button in Gauntlet to create internal or external links; you can also create links to a bookmark in this file or in other files.)

- Bulleted lists look like this
    - item 1 (TAB to indent one level)
    - item 2

1. Numbered lists look like this
    a. item 1 (again, TAB to indent one level)
    b. item 2

Tables are easy to create, but they definitely have some limitations. Best advice: Keep your tables simple. No merged cells, no nesting. 

|Column 1 heading  |Column 2 heading  |Column 3 heading  |
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
\* If you want to use a plain ol' asterisk, preceed it with a \ character.

\*\*Same thing for 2 asterisks...


| | |
|---------|---------|
|![](media/Assign_roles_and_permissions_in_Microsoft_Teams_image1.png) <br></br>Note     |Here's how to do an image with a note.         |

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

    b. 	If this is not true, run the Set-MsolCompanySettings  cmdet **to set it to True**.
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

