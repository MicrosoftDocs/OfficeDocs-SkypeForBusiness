---
title: Use Fluid Framework for Teams chat
author: cichur
ms.author: v-cichur
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: michalbr
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Fluid Framework in Teams chat.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Set Fluid Framework for Teams chat

Live components are built with Microsoft Fluid Framework. You'll need the [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) module to enable or disable all Fluid Experiences across your Office 365 tenant.

Microsoft Fluid Framework defaults to **ON** for all targeted release tenants. Because live components are designed for collaboration, the components are always shared as editable by others, even if your tenant is set to default to view-only for other file types. See the **Learn more** link next to the setting for more details. 

Microsoft Fluid Framework preview releases across all targeted release tenants with default **ON** state and will be overriding the view-only by default setting for newly created `.fluid` files and for files forwarded by the user. This setting won't apply to `.fluid` files with a **Learn more** link right next to the setting. The setting won't be applied to files shared through the OneDrive for Business **Share** dial.

## Check if Fluid Framework is enabled through SharePoint Online PowerShell Cmdlet 

1. Connect to SharePoint Online PowerShell.

2. Check if Fluid Framework is enabled by running the get cmdlet without any arguments.

   `Get-SPOTenant`

4. Look for the value of IsFluidEnabled, and verify it is **true**.

## Enable Fluid Framework through SharePoint Online PowerShell Cmdlet  

1. Connect to SharePoint Online PowerShell.  

2. Enable Fluid using the Set-SPOTenant cmdlet.

   `Set-SPOTenant -IsFluidEnabled $true`  

The change will take some time to apply across your tenancy.  

## Disable Fluid Framework through SharePoint Online PowerShell Cmdlet  

1. Connect to SharePoint Online PowerShell.  

2. Disable Fluid using the Set-SPOTenant cmdlet.  

   `Set-SPOTenant -IsFluidEnabled $false`

The change should take some time to apply across your tenancy.  

If you need to re-enable this capability, you can use the SharePoint Online PowerShell Cmdlets.  
 
For Example:

```
PS C:\WINDOWS\system32> Connect-SPOService 
cmdlet Connect-SPOService at command pipeline position 1 
```

Supply values for the following parameters:

Url: `https://a830edad9050849822e21011208-admin.sharepoint.com/`

`PS C:\WINDOWS\system32> set-SPOTenant -isFluidEnabled $false`

`PS C:\WINDOWS\system32>`

## Known limitations 

Live components appear in search results from Teams and Office.com as files. Searching for live components within messages is not yet available.

Guest users in federated chats won't be able to collaborate with live components. 

### Storage of `.fluid` files** 

**What happens if owner of file leaves the company?** 

The same policies as apply to other content created by the user, like other Office files.  

**How are .fluid files shared?** 

Components in Teams chat can be copied from within Teams and pasted in other chats (but not yet channels). They default to the existing permissions, but users can change the permissions before sending to ensure everyone has access.

Opening components in Teams chat in Office.com offers share functionality at the top of the window, similar to the sharing options offered for other Office documents. You can also share by copying part of the file, choosing **Link to Selection** from the margin, and then pasting into Teams chats so recipients can edit inline in the message.

**What if a `.fluid` file becomes corrupted or damaged?** 

Version History allows you to review and copy from previous versions of the file.  

**What apps can open and edit `.fluid files` after they’ve been created by the “experience”?** 

`.fluid` files can only be opened as links in your browser, such as in Office.com, and as embedded live components in Teams chat. If downloaded, they can't be opened without first uploading them back to OneDrive for Business or SharePoint Online. 

## Related topics

[Manage Fluid Framework preview](/office365/troubleshoot/access-management/manage-fluid-framework-preview-access)