---
title:  Bulk install the new Microsoft Teams desktop client
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 03/30/2023
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
description: Bulk install the new Microsoft Teams desktop client for Windows. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Bulk deploy new Microsoft Teams desktop client 

Direct or "bulk"  deployments are useful because users don't need to download and install the Teams client manually. Microsoft provides an executable (.exe) file for the new Teams client so you can deploy the application directly to the computers in your organization using your choice of software management tool, such as Intune or Configuration Manager.

The Teams installer installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.

## How it works

**TeamsProvision** is a lightweight online installer with a headless command-line interface. It allows admins to ‘provision’ (install) the app for all users on a given target computer.
When TeamsProvision is run on a computer it does:
- Downloads the latest Teams MSIX package from our CDN.
- Installs the Teams MSIX application for all users on the computer. Note that any users who have installed a different Teams version will have their version replaced with the provisioned version.
- Modifies the registry to ensure that Teams can interoperate with Office and other applications on the computer.
- Returns machine-readable JSON output on the command line, indicating whether the operation was successful.

    :::image type="content" source="media/new-teams-direct-reploy-cmd-feedback.png" alt-text="command prompt feedback when downloading executable for direct deployment":::


## Prerequisites for target computers

Computers must meet the minimum requirements listed here.

##### Required system and app requirements

|Requirement|Version|
|:-----|:-----|
|Windows| Windows 10 version 10.0.19041 or higher|
|Teams app|Version 1.6.00.4472 to see the *Try the new Teams* toggle.</br></br>If you are at a lower version, select the overflow menu **(…) > Check for updates > Update**. Then restart your app. |
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|

<br>

##### Required Microsoft 365 Apps Security Updates

|Channel|Version & Build|
|:-----|:-----|
|Semi-Annual Enterprise Channel| Version 2302 (Build 16130.20306)</br>Version 2208 (Build 15601.20578)</br>Version 2202 (Build 14931.20944)</br> |
|Monthly Enterprise Channel|Version 2301 (Build 16026.20222)</br>Version2212 (Build 15928.20294)</br> |
|Windows LTSB|Version 2018 (Build 10396.20023)</br>Version 2021 (Build 14332.20481)</br>|

</br>

Learn more at [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).


## Step 1: Download the new Teams installer

1. Download the .exe installer -- add link
2. Open the Command Prompt as an Admin.
3. Run the downloaded setup.exe. Success or fail status will display.

<Screenshot of cmd prompt>


## Step 2: Deploy the app to your organization

As an admin, you can now deploy this installer for a single computer or a group of computers for your entire organization using [Intune](/mem/intune/fundamentals/what-is-intune), [Microsoft Endpoint Configuration Manager](/configmgr/core/understand/introduction), [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or third-party distribution software, to deploy new Teams to your organization.


## Step 3: Set Team Admin Center policy

>[!Note]
>Admin policies may also be set using PowerShell. Learn more: [Rollout new Teams using Powershell](new-teams-desktop-admin.md#powershell)

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select **Teams > Teams Update** policies from the left pane.
3. Select Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below.

   |Setting|Description|
   |:-----|:-----|
   |Not enabled|Use this value to hide the new Teams toggle switch. Users won't be able to opt in to the new Teams.|
   |Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch will display to let users opt into the new Teams and switch back if needed. **Note:** This option was previously called *Users can choose*.|
   |Microsoft controlled| Default. The value lets Microsoft control whether the new Teams toggle switch is shown or not based on product readiness|


5. Once the policy is defined, you can assign it to a **user or user group** with the Group policy assignment. To assign it to a group, select **Group policy assignment** and then **Add**,  or select one of the groups listed.  Select a policy to assign to the group.
6. Once the policy is defined, you can assign it to a specific user under **Users> Manage users**.

>[!Note]
>If you update the policy setting in the Teams Admin Center, the new setting goes into effect within one minute. The user doesn't have to restart the app.

## Impact to end user

After new Teams is deployed to your target computers, users will sign in as usual. For first use, the user must manually launch new Teams:

1.</br>
2.</br>
3.