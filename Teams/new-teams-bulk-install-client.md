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

Bulk deployments are useful because users don't need to download and install the Teams client manually. Microsoft provides .exe file for new Teams client so you can bulk deploy the application to the computers in your organization using your choice of software management tool, such as Intune or Configuration Manager.

Bulk deploying of new Teams is to individual computers, not users. Teams will not autolaunch; users will need to manually launch the app when they sign in.  

## How it works

@charlie to add 2-3 sentences about how the new .exe works on users machine
The Teams MSI places an installer in %SystemDrive%\Program Files\Teams Installer on 32-bit Windows and %SystemDrive%\Program Files (x86)\Teams Installer on 64-bit Windows. Whenever a user signs into a new Windows user profile, the installer is launched and a copy of the Teams app is installed in that user's %LocalAppData%\Microsoft\Teams folder. If a user already has the Teams app installed in the %LocalAppData%\Microsoft\Teams folder, the MSI installer skips the process for that user.
MSI files can't be used to deploy updates. The Teams client will auto-update when it detects a new version is available from the service. To re-deploy the latest installer, use the process of redeploying MSI described below. If you deploy an older version of the MSI file, the client will auto-update (except in VDI environments) when possible for the user. If a very old version gets deployed, the MSI will trigger an app update before the user is able to use Teams.

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

As an admin, you can now deploy this installer for a single computer, group of computers for your entire organization using any device management tools like Intune, SCCM etc. 

1.  <link to end point managers>
2. 


## Step 3: Set Team Admin Center policy

1. https://learn.microsoft.com/en-us/microsoftteams/new-teams-desktop-admin?tabs=powershell#how-to-roll-out-new-teams
Please go to Teams admin centre 
set to Microsoft choie
Is this the Use Group policy?


## Impact to end user

I What will be the experience when they log in? will teams boot automatically in the new Teams II can they switch back to classic Teams?

Steps:  
1.
2.
