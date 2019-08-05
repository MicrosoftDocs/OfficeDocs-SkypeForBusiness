---
title: Install the StaffHub PowerShell module
author: LanaChin
ms.author: v-lanac
ms.reviewer: lisawu
manager: serdars
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Learn how to install and connect to the Microsoft StaffHub PowerShell module.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Install the Microsoft StaffHub PowerShell module

> [!IMPORTANT]
> Effective October 1, 2019, Microsoft StaffHub will be retired. We’re building StaffHub capabilities into Microsoft Teams. Today, Teams includes the Shifts app for schedule management and additional capabilities will roll out over time. StaffHub will stop working for all users on October 1, 2019. Anyone who tries to open StaffHub will be shown a message directing them to download Teams. To learn more, see [Microsoft StaffHub to be retired](microsoft-staffhub-to-be-retired.md).  

Use the steps in this article to install and connect to the Microsoft StaffHub PowerShell module. You'll need this to manage StaffHub by using PowerShell and to move your StaffHub teams to Microsoft Teams.

## Install the Microsoft StaffHub PowerShell module

1. Open Windows PowerShell 3.0 or later as an admin. To do this, click **Start**, type **Windows PowerShell**, right-click **Windows PowerShell**, and then select **Run as administrator**.
    > [!NOTE]
    > To get the latest version of Windows PowerShell, see [Installing Windows PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell). 
2. Run the following to install stable version:

    ```
    Install-Module -Name MicrosoftStaffHub
    ```
    
    Or run this command in case you would like to install the latest unstable version `Install-Module -Name MicrosoftStaffHub -AllowPrerelease`

     > [!NOTE]
     > Run this command in case if you will receive an error during unstable version installation `Install-Module PowershellGet -Force`

3. Optional step. You could see the warning message

    ```
    Untrusted repository - You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from 'PSGallery'?
    ```

Type `Y` and click `Enter`.
 
4. Exit Windows PowerShell.

## Connect to the Microsoft StaffHub PowerShell module

1. Run the following:

    ```
    Connect-StaffHub
    ```

2. When you're prompted, log in as a global admin.

## Related topics

- [Microsoft StaffHub PowerShell reference](https://docs.microsoft.com/en-us/powershell/module/staffhub/?view=staffhub-ps)
- [Move your Microsoft StaffHub teams to Shifts in Teams](move-staffhub-teams-to-shifts-in-teams.md)
