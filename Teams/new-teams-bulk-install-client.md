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

Direct or "bulk"  deployments are useful because users don't need to download and install the Teams client manually. Microsoft provides an executable (.exe) file for new Teams client so you can deploy the application directly to the computers in your organization using your choice of software management tool, such as Intune or Configuration Manager.

Bulk deployments are useful because users don't need to download and install the Teams client manually.  Teams is deployed to the computer  (not autolaunched) and users will have to manually launch the app. Microsoft provides exe file for new Teams client so you can bulk deploy the application on a machine

The Teams installer will install the Teams MSIX package on a target machine, but will also ensure that Teams can interoperate correctly with Office and other Microsoft software.


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

1. As an admin, you can now deploy this installer for a single computer, group of computers for your entire organization using [Intune](/mem/intune/fundamentals/what-is-intune), [Microsoft Endpoint Configuration Manager](/configmgr/core/understand/introduction), [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or third-party distribution software, to deploy new Teams to your organization.


## Step 3: Set Team Admin Center policy

1. https://learn.microsoft.com/en-us/microsoftteams/new-teams-desktop-admin?tabs=powershell#how-to-roll-out-new-teams
Please go to Teams admin centre 
set to Microsoft choie
Is this the Use Group policy?


## Impact to end user

After new Teams is deployed to your target computers, users will sign in as usual. For first use, the user must manually launch new Teams:

1. I What will be the experience when they log in? will teams boot automatically in the new Teams II can they switch back to classic Teams?


