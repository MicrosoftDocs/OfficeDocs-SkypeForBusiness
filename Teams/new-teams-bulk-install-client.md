---
title:  Bulk deploy the new Microsoft Teams desktop client
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 06/30/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Bulk deploy the new Microsoft Teams client.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Bulk deploy the new Microsoft Teams client 

>[!Note]
>**Coming soon:** The Bulk deploy feature will be released in early August 2023.

Direct or "bulk"  deployments are helpful because users don't need to manually download and install the Teams client. Microsoft provides an executable (.exe) file for the new Teams client so you can deploy the application directly to the computers in your organization using your choice of software management tools, such as Intune or Configuration Manager.

The Teams installer installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.

## How it works

**TeamsProvision** is a lightweight online installer with a headless command-line interface. It allows admins to ‘provision’ (install) the app for all users on a given target computer.

When **TeamsProvision.exe** is run on a computer:

- Admin downloads the Teams.exe
- Installs the new Teams app for **all users on the computer.** 

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
|Classic Teams app|Version 1.6.00.4472 or later to see the *Try the new Teams* toggle.<</br> </br>**Important:** Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client.|
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|

>[!Important]
>If you want
Learn more at [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).

## Deploy the new Teams application to your organization

>[!Important]
>The Bulk deploy feature will be released in early August, 2023. Please check back at that time.

>[!Note]
>All steps must be completed to successfully deploy the new Teams.


## Step 1: Download the new Teams installer

1. Download the .exe installer.

>[!Important]
>This download link will be available when the feature goes live in early August, 2023. Please check back then.

2. Open the Command Prompt as an Admin.
3. At the prompt enter: **./teamsprovision.exe -p**

4. A success or fail status displays. If you receive an error, learn more at [Common HRESULT values](/windows/win32/seccrypto/common-hresult-values).

   :::image type="content" source="media/new-teams-direct-reploy-cmd-feedback.png" alt-text="command prompt feedback when downloading executable for direct deployment":::

## Step 2: Deploy the app to your organization

Deploy this installer to a single computer, group of computers, or your entire organization using [Intune](/mem/intune/fundamentals/what-is-intune), [Microsoft Endpoint Configuration Manager](/configmgr/core/understand/introduction), [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or third-party distribution software, to deploy the new Teams.


## Step 3: Set Teams Admin Center policy

>[!Note]
>Admin policies may also be set using PowerShell. Learn more: [Set the policies to deploy the new Teams client - Powershell method](new-teams-deploy-using-policies.md)

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select **Teams > Teams Update** policies from the left pane.
3. Select Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below.

|Setting|Description|
|:-----|:-----|
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