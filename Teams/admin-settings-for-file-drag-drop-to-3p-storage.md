---
title: Admin settings for file drag-drop to 3P storage 
author: CarolynRowe
ms.author: ellisonj2024
ms.reviewer: v-ellisonj
ms.date: 04/18/2024
manager: v-midet
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: 
description: Learn how to change the default storage backend of Teams
ms.localizationpriority: medium
f1.keywords: 
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
appliesto: 
  - Microsoft Teams
---

# Admin settings for file drag-drop to 3P storage

With the goal of making Teams an open platform we are enabling Teams admins to change the default storage backend of Teams (OneDrive and SharePoint) to a 3P storage provider app of their choice. This feature provides two things...

1. For Teams Admins - Setting to change default storage app for drag drop when uploading files on Teams desktop.

2. For Teams app developers (3p) – Ability to utilize this capability for their Teams app using Teams SDK.  
Hence this functionality only works for select supported apps where app developer has utilized such capability for Teams app. This document explains policies names, syntaxes, and how Tenants can change the default Drag-drop storage destination to a 3P storage provider.  


## Tenant level policy
Admin can use PowerShell command to set a default Teams app to handle drag drop files  Set-CsTeamsFilesPolicy -Identity Global -DefaultFileUploadAppId  "<appId>" 
 
Admin can use PowerShell command to revert back for ODSP to handle drag drop files Set-CsTeamsFilesPolicy -Identity Global -DefaultFileUploadAppId  "" 

• Identity – Global ?? 
 
End user side error conditions:

• App not installed -> “Default app set by your org admin is not installed.”

• App does not supported drag drop ->  “Default app setup by your org admin doesn’t support file upload.” (May not be in our control)  … Fallback to “Generic error” 

## To check the status of a tenant
Get-CsTeamsFilesPolicy 

## To enable or disable native file upload point
Get-CsTeamsFilesPolicy 

## To remove the policy for the complete list of users
Remove-CsTeamsFilesPolicy 

## User level policy
New-CsTeamsFilesPolicy -Identity UserPolicy -NativeFileEntryPoints Disabled 
• Identity - UserPolicy 

## To grant a policy to user
Grant-CsTeamsFilesPolicy  -identity "Mayur Kale" -PolicyName UserPolicy

## To update the policy user
Set-CsTeamsFilesPolicy -Identity UserPolicy -NativeFileEntryPoints Enabled

## To remove the policy user
Remove-CsTeamsFilesPolicy

## Mixed code
Behaviour with mixed mode admin settings highlighted below: 


|NativeFileEntryPoints |DefaultFileUploadAppID |Expected behavior
|---------|---------|---|
|ODSP Enabled     |Enabled*       |Paperclip>Upload from device - Goes to ODSP Drag-Drop - Goes to the configured 3P app*|
|ODSP Enabled    |Not enabled      |Paperclip>Upload from device - Goes to ODSP Drag-drop - Goes to ODSP|
|ODSP Disabled    |Enabled*      |Paperclip (Attach) - Hidden Drag-Drop - Goes to the configured 3P app|
|ODSP Disabled    |Not Enabled      |Paperclip (Attach) - Hidden Drag-Drop - No op|

## Out of scope
Teams Mobile support for DefaultFileUploadAppId policy is not applicable. 
Also note that image or media copy paste is today treated as part of Teams message payload and not a cloud file so is not impacted by this policy. 

Documentation for Admin 
-	Admin would have to refer to app description or 3p app documentation regarding supporting this policy 
-	Have a list of supported apps and add to our official documentation. Call out that it is an indicative list only with pointer on how we can add more apps to the list o Box  o Egnyte  
-	Reach out directly to App Developer if not sure regarding this functionality

Documentation for Developers (like Box) 
-	“DragAndDropFileCallback” support in Teams SDK  
-	@microsoft/teams-js package - Teams | Microsoft Learn 
-	Guidance to App Developers add this capability to their app description and publish in their documentation 








