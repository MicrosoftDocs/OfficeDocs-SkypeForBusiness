---
title: Admin settings for file drag-drop to 3P storage 
author: MicrosoftHeidi
ms.author: heidip
ms.reviewer: shkarri,sasood
ms.date: 04/18/2024
manager: heidip
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: 
description: Learn how to change the default storage backend of Teams.
ms.localizationpriority: medium
f1.keywords: 
ms.collection:
appliesto: 
  - Microsoft Teams
---

# Admin settings for file drag-drop to 3P storage

To help Teams become an open platform, Teams admins can change the default storage backend of Teams (for OneDrive and SharePoint) to a 3P storage-provider app of their choice. This change allows you to do the following:

- **For Teams admins** The ability to change the default storage app for drag-drop when uploading files on the Teams desktop.

- **For Teams app developers (3P)** The ability to use this capability for Teams apps using the Teams SDK.

This functionality works only for Teams apps which have been built with the intent to support this configurability. This article explains policy names, syntax, and how tenants can change the default drag-drop storage destination to a 3P storage provider.

## Check the status of your tenant
To view the current status of your tenant's Teams Files policy, use the *Get-CsTeamsFilesPolicy* Cmdlet:
- *Get-CsTeamsFilesPolicy -Identity Global*

## Configure the 3P app
Admins can use the following PowerShell command to set a 3P cloud storage to handle drag-drop files.

```powershell
Set-CsTeamsFilesPolicy -Identity Global -DefaultFileUploadAppId  "<appId>"
```

Admins can use following PowerShell command to revert this setting.

```powershell
Set-CsTeamsFilesPolicy -Identity Global -DefaultFileUploadAppId  ""
```

## Remove the policy for your users
 To remove the Teams Files policy for your users, use the *Remove-CsTeamsFilesPolicy* Cmdlet:
- *Remove-CsTeamsFilesPolicy -Identity Global*

For more information on user-level policy changes, see [Turn off Teams Native File Upload policy](/microsoftteams/turn-off-teams-native-file-upload-policy)

### User side-error conditions
A user side error could occur due to the following reasons:
- App is configured but not installed
- Configured app does not support drag-drop

### To remove the policy for the complete list of users
*Remove-CsTeamsFilesPolicy*

### Mixed mode
The following behavior occurs with mixed-mode admin settings:

|*NativeFileEntryPoints* |*DefaultFileUploadAppID* |Expected behavior
|---------|---------|---|
|Enabled     |Enabled*       |Paperclip>Upload from device (goes to OneDrive/SharePoint)<br>Drag-Drop (**goes to the configured 3P app***)|
|Enabled    |Not enabled      |Paperclip>Upload from device  (goes to OneDrive/SharePoint)<br>Drag-drop (goes to OneDrive/SharePoint)|
|Not enabled    |Enabled*      |Paperclip (Attach) - Hidden<br>Drag-Drop (**goes to the configured 3P app***)|
|Not enabled    |Not Enabled      |Paperclip (Attach) - Hidden<br>Drag-Drop (**no op**)|

> [!NOTE]
> To make this policy work, *NativeFileEntryPoints* should be disabled. For more information on making related changes, see [Turn off Teams Native File Upload policy](/microsoftteams/turn-off-teams-native-file-upload-policy).

### Out of scope
Teams Mobile support for the *DefaultFileUploadAppId* policy isn't applicable. Also note that image or media copy and paste is today treated as part of the Teams message payload and not as a cloud file. This policy doesn't impact the image or media copy and paste.

## Documentation for admins
Admins should refer to the app description or 3P app documentation for information about App ID for this policy.

- Currently, Box is the only supported app. Box should be contacted for its App ID.
- For new app support, contact your desired 3P storage provider for the compatible app.

## Documentation for developers (3P storage apps)

- Use latest version of the Teams SDK.
- The app manifest should have the first action as **Upload**.
- 3P app to call thirdPartyCloudStorage API to get the drag-dropped files with the following parameters:
  1. Concatenate two values to get the unique id/cache id:<br>**const uniqueIdForChats = replyToId + id** (i.e., thread id)<br>Note, if **replyToId** is **""** then the uniqueID will be **""+threadId**
  2. Callback: (files: FilesFor3PStorage[], error?: SdkError): void;**

- For more API information, see [thirdPartyCloudStorage module](/javascript/api/@microsoft/teams-js/thirdpartycloudstorage).

- For more information about the Teams SDK, see [@microsoft/teams-js package](/javascript/api/@microsoft/teams-js).
