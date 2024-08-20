---
title: Admin settings for file drag-drop to third-party storage 
author: MicrosoftHeidi
ms.author: heidip
ms.reviewer: shkarri,sasood
ms.date: 04/18/2024
manager: heidip
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: 
description: Learn how to change the default storage backend of Teams (for OneDrive and SharePoint).
ms.localizationpriority: medium
f1.keywords: 
ms.collection:
appliesto: 
  - Microsoft Teams
---

# Admin settings for file drag-drop to third-party storage

To help Teams become an open platform, Teams admins can change the default storage backend of Teams (for OneDrive and SharePoint) to a third-party storage-provider app of their choice. This change gives you:

- **For Teams admins** The ability to change the default storage app for drag-drop when uploading files on the Teams desktop.

- **For Teams app developers (third party)** The ability to use this capability for Teams apps using the Teams SDK.

This functionality works only for Teams apps built to support this configurability. This article explains policy names, syntax, and how tenants can change the default drag-drop storage destination to a third-party storage provider.

## Check the status of your tenant
To view the current status of your tenant's Teams Files policy, use the *Get-CsTeamsFilesPolicy* Cmdlet:

```powershell
Get-CsTeamsFilesPolicy -Identity Global
```

## Configure the third-party app
Admins can use the following PowerShell command to set a third-party cloud storage to handle drag-drop files.

```powershell
Set-CsTeamsFilesPolicy -Identity Global -DefaultFileUploadAppId  "<appId>"
```

Admins can use the following PowerShell command to revert this setting.

```powershell
Set-CsTeamsFilesPolicy -Identity Global -DefaultFileUploadAppId  ""
```

## Remove the policy for your users
 To remove the Teams Files policy for your users, use the *Remove-CsTeamsFilesPolicy* Cmdlet:

```powershell
Remove-CsTeamsFilesPolicy -Identity Global
```

### User side-error conditions
A user side error could occur due to the following reasons:
- The app is configured but not installed

- The configured app doesn't support drag-drop

### Remove the policy for the complete list of users
To remove the policy for the complete list of users, use the *Remove-CsTeamsFilesPolicy* Cmdlet:

```powershell
Remove-CsTeamsFilesPolicy
```

### Out of scope
Teams Mobile support for the *DefaultFileUploadAppId* policy isn't applicable. Also note that image or media copy and paste is today treated as part of the Teams message payload and not as a cloud file. This policy doesn't impact the image or media copy and paste.

## Documentation for admins
Admins should refer to the app description or third-party app documentation for information about App ID for this policy.

- For new app support, contact your desired third-party storage provider for the compatible app.

## Documentation for developers (third-party storage apps)
In order for Teams apps to support drag-drop:
- Use the latest version of the Teams SDK.
- The app manifest should have the first action as Upload.
- The third-party app calls thirdPartyCloudStorage API to get the drag-dropped files with the following parameters:
  1. Concatenate two values to get the unique ID/cache ID:<br>**const uniqueIdForChats = replyToId + id** (that is, thread ID)<br>Note, if **replyToId** is **""** then the unique ID is **""+threadId**
  2. Callback: (files: FilesFor3PStorage[], error?: SdkError): void;**

- For more API information, see [thirdPartyCloudStorage module](/javascript/api/@microsoft/teams-js/thirdpartycloudstorage).
- For more Teams SDK information, see [@microsoft/teams-js package](/javascript/api/@microsoft/teams-js).
