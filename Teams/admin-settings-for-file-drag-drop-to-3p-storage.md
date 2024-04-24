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
To view the current status of your tenant's Teams files policy, use the *Get-CsTeamsFilesPolicy* cmdlet:

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
 To remove the Teams Files policy for your users, use the Remove-CsTeamsFilesPolicy cmdlet:

- *Remove-CsTeamsFilesPolicy -Identity Global*

For more information on user-level policy changes, see [Turn off Teams Native File Upload policy](/microsoftteams/turn-off-teams-native-file-upload-policy)



### User side-error conditions
- App not installed: “Default app set by your org admin isn't installed.”

- App does not support drag-drop: “Default app setup by your org admin doesn’t support file upload.” (May not be in our control. Use “Generic error”?)

### To check the status of a tenant
*Get-CsTeamsFilesPolicy*

### To enable or disable native file upload point
*NativeFileEntryPoints : Disabled*

### To remove the policy for the complete list of users
*Remove-CsTeamsFilesPolicy*

## User-level policy
*New-CsTeamsFilesPolicy -Identity UserPolicy -NativeFileEntryPoints Disabled*
- *Identity - UserPolicy*

### To grant a policy to user
*Grant-CsTeamsFilesPolicy  -identity "Mayur Kale" -PolicyName UserPolicy*

### To update the policy user
*Set-CsTeamsFilesPolicy -Identity UserPolicy -NativeFileEntryPoints Enabled*

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
> The policy will apply to both T1 and T2.1.

### Out of scope
Teams Mobile support for the *DefaultFileUploadAppId* policy isn't applicable. Also note that image or media copy and paste is today treated as part of the Teams message payload and not as a cloud file. This policy doesn't impact the image or media copy and paste.

## Documentation for admins
Admins should refer to the app description or the 3P app documentation for information about supporting this policy.

- Have a list of supported apps and add to our official documentation.
- Call out that it's an indicative list only with a pointer on how we can add more apps to the list (for Box or Egnyte).
- Reach out directly to App Developer if you're sure about this functionality.

## Documentation for developers (like Box)

-	“DragAndDropFileCallback” support in Teams SDK.

- [thirdPartyCloudStorage module](/javascript/api/@microsoft/teams-js/thirdpartycloudstorage)
- [@microsoft/teams-js package](/javascript/api/@microsoft/teams-js)

- @microsoft/teams-js package - Teams | Microsoft Learn.
-	Guidance to App Developers add this capability to their app description and publish in their documentation.
