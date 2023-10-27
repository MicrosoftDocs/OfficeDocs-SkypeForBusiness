---
title:  Bulk deploy the new Microsoft Teams desktop client
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 10/27/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Bulk upgrade to the new Microsoft Teams client.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Bulk upgrade to the new Microsoft Teams client 

Direct or "bulk" upgrades are helpful because users don't need to manually download and install the Teams client. Microsoft provides an executable (.exe) file for the new Teams client so you can upgrade the application directly to the computers in your organization using your choice of software management tools, such as Intune or Configuration Manager.

The Teams installer installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.

>[!Note]
>**New.** An offline install method is now avaiable. Learn more: [Download and install new Teams using an offline installer](#option-1b-download-and-install-new-teams-using-an-offline-installer)

## How it works

**TeamsBootstrapper** is a lightweight online installer with a headless command-line interface. It allows admins to provision (install) the app for all users on a given target computer.

When **teamsbootstrapper.exe** is run on a computer:

- The installer downloads the latest Teams MSIX package from Microsoft
- The installer installs the Teams application for all users on the computer, and any users who may be added afterwards.

>[!Important]
>Users who have installed a different Teams version will have their version replaced with the provisioned version.

- Modifies the registry to allow Teams to work with Office and other computer applications.
- Displays success or failure message on the command line


## Prerequisites for target computers

For new Teams to be successfully installed, computers must meet the minimum requirements listed here.

##### Required system and app requirements

|Requirement|Version|
|:-----|:-----|
|Windows| Windows 10 version 10.0.19041 or higher|
|Classic Teams app|Version 1.6.00.4472 or later to see the *Try the new Teams* toggle.</br>**Important:** Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client.|
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|
|Webview2|Update to the most current version. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|App sideloading enabled|Ensure that sideloading is enabled on every computer you install on.  Learn more: [Sideload line of business (LOB) apps in Windows client devices](/windows/application-management/sideload-apps-in-windows-10)
|Delivery optimization (DO)|Learn more at [Delivery Optimization](/windows/deployment/do/waas-delivery-optimization)|

>[!Note]
>Learn more: [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).

## Step 1: Upgrade the new Teams application

All steps must be completed to successfully upgrade to the new Teams.

#### Option 1A: Download and install new Teams for a single computer

To install new Teams on a single computer with many users, follow these steps:

1. [Download the .exe installer](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409)
2. Open the Command Prompt as an Admin.
3. At the prompt enter: **.\teamsbootstrapper.exe -p**
4. A success or fail status displays. If you receive an error, learn more at [Common HRESULT values](/windows/win32/seccrypto/common-hresult-values).
</br>
   :::image type="content" source="media/new-teams-direct-deploy-cmd-feedback.png" alt-text="command line prompt feedback":::


#### Option 1B: Download and install new Teams using an offline installer

Admins can also use a local teams MSIX to provision new Teams. This option minimizes the amount of bandwidth used for the initial installation. The MSIX can exist in a local path, UNC, or URI.

1. [Download the .exe installer.](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409)
2. [Download the MSIX.](https://go.microsoft.com/fwlink/?linkid=219606)
3. Open the Command Prompt as an Admin.
4. Depending on where your MSIX is located, do the following:
</br>

 **For local path, enter:** *.\teamsbootstrapper.exe -p -o "c:\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-localpath.png" alt-text="local path location for offline installer"::: 
 
   **For UNC, enter:** *.\teamsbootstrapper.exe -p -o "\\unc\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-unc.png" alt-text="offline location using unc":::
 
   **For URI, enter:**  *.\teamsbootstrapper.exe -p -o https://location_of_teams.com/...*
 
   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-uri.png" alt-text="uri location for offline installer":::
 

#### Option B: Upgrade to the new Teams across your organization

To deploy this installer to a group of computers, or your entire organization, follow these steps:

1. [Download the .exe installer](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409).
2. Use [Intune](/mem/intune/fundamentals/what-is-intune), [Microsoft Endpoint Configuration Manager](/configmgr/core/understand/introduction), [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or third-party distribution software, to distribute the installer to your target computers.
3. Run the installer on each computer.  


## Step 2: Set new Teams as the default 

>[!Note]
>Admin policies may also be set using PowerShell. Learn more: [Set the policies to upgrade to the new Teams client - Powershell method](new-teams-deploy-using-policies.md)

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select **Teams > Teams Update policies** from the left navigation pane.
3. Select Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below.

|Setting|Description|
|:-----|:-----|
|New Teams as default|Sets the new Teams as default. **Note:** This option is currently being rolled out|
|Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch displays to let users opt into the new Teams and switch back if needed.| 

>[!Note]
>This option was previously called **Users can choose**.

5. Once the policy is defined, you can assign it to a **user or user group** with the Group policy assignment. To assign it to a group, select **Group policy assignment** and then **Add**,  or select one of the groups listed.  Select a policy to assign to the group.
6. Once the policy is defined, you can assign it to a specific user under **Users> Manage users**.

>[!Note]
>If you update the policy setting in the Teams Admin Center, the new setting goes into effect within one minute. The user doesn't have to restart the app.

## End user experience:  Launching the new Teams 

After new Teams is deployed to your target computers, users will sign in as usual. For first use, the user can launch new Teams in one of two ways:

I. Users can launch classic Teams, and then switch the toggle to go to new Teams.

OR

II.  Users can directly launch new Teams:
1. In Windows, select **Start** **> new Microsoft Teams**.
2. Select "Yes" at the confirmation prompt screen. 
3. Once confirmed, the new Teams launches and is the default version.
