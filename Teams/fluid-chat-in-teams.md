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

Live components in Microsoft Teams chat offer a new way to ideate, create, and make decisions together. Send a component, such as a table, task list, or paragraph, that everyone in your chat can edit inline, and see changes as they’re made. This means you can gather ideas and feedback from your team while holding fewer meetings and minimizing the need for long chat threads.

- Get tasks done faster together. Crowd-source an agenda, track a group's action items, or take notes collectively. These are just a few scenarios made easier with live components.
- Share components. In this release, you can share live components into different Teams chats. Recipients can edit from wherever they are and see updates instantly no matter where the changes were made. In future releases, live components will be supported in Teams meeting notes and channels, Outlook, and eventually across all Microsoft Office 365 applications.
- Start in chat and build from there. Every component you create from Teams chat is automatically saved to a file in Microsoft OneDrive. So, you might begin collaborating in chat then later move to the file, where you have a larger visual space for editing and can add as many components as you like.

## Clients and platforms

Early September, the feature will be available globally. In late September, the feature will be available for Government Community Cloud (GCC).

## Settings management

The feature will be available on Teams Windows Desktop, Mac, iOS, Android.

Live components are built with Microsoft Fluid Framework. You'll need the [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps) module to enable or disable all Fluid Experiences across your Office 365 tenant.

Microsoft Fluid Framework defaults to **ON** for all targeted release tenants. Because live components are designed for collaboration, the components are always shared as editable by others, even if your tenant is set to default to view-only for other file types. See the **Learn more** link next to the setting for more details.

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

- Creating a table or a task list as the first component first time after the Teams app is restarted may take some extra time.
- Other chat members will receive an email notification when mentioned with ‘@’. At-mentions notifications in Teams activity feed will be available soon.
- Searching for live components within Teams search will return a link to the component in office.com, not the chat message itself.
- Live components are disabled in federated chats and are enabled for regular chats with Guest account (using Azure B2B).
- While you can share a component in Teams channels and other Microsoft 365 apps, recipients simply get a link in most places at this time. Inline editing is planned for more experiences in the future.

### Storage of `.fluid` files**

**How are .fluid files stored?**

Collaborative components created in Teams are backed by a .fluid file stored in the creator’s OneDrive for Business. Being a file in OneDrive for Business means that users can create, discover, and manage collaborative components (.fluid file) as easily as any Office document.

- Users can search for content in .fluid files are searchable from Office.com, and OneDrive UI.
- Data governance features like eDiscovery, audit logs, legal hold will continue to work with .fluid files
- Users activities are recorded in auditing logs.
- .fluid will now appear on Office.com and OneDrive for Business, such as in the recent and recommended areas.
- .fluid files can be restored to previous versions from OneDrive for Business.

Chat participants are required to have OneDrive account to create collaborative components. Without a valid OneDrive account, chat participants might still be able to collaborate on a component created by other users who have a valid OneDrive account.

**What happens if owner of file leaves the company?**

- The same policies as apply to other content created by the user, like other Microsoft Office files.
- The same OneDrive for Business retention policies applies to .fluid files just like other content created by the user.

**How are .fluid files shared?**

Components in Teams chat can be inserted or copied from within Teams and pasted in other chats (but not yet channels). They default to the tenant’s existing permissions set to OneDrive for Business or SharePoint Online files, but users can change the permissions before sending to ensure everyone has access.

Opening components in Teams chat using Office.com offers share functionality at the top of the window, similar to the sharing options offered for other Microsoft Office documents. You can also share by copying part of the file, choosing **Link to Selection** from the margin, then pasting into Teams chats so recipients can edit inline in the message.

**What if a `.fluid` file becomes corrupted or damaged?**

Version History allows you to review and copy from previous versions of the file.  

**What apps can open and edit `.fluid files` after they’ve been created by the “experience”?**

`.fluid` files can only be opened as links in your browser, such as in Office.com, and as embedded live components in Teams chat. If downloaded, they can't be opened without first uploading them back to OneDrive for Business or SharePoint Online.

## Related topics

[Manage Fluid Framework preview](/office365/troubleshoot/access-management/manage-fluid-framework-preview-access)
