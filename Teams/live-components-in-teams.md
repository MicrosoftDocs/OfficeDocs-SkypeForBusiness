---
title: Manage live components in Teams
author: HowlinWolf-92
ms.author: v-mahoffman
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: michalbr
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to Manage live components in Teams.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Manage live components in Teams

Live components in Teams chat offer a new way to ideate, create, and make decisions together. Send a component—like a table, task list, or paragraph—where everyone in your chat can edit inline and see changes as they’re made. This means you can gather ideas and feedback from your team while holding fewer meetings and minimizing the need for long chat threads.
> [!Note]
> Live components is the first feature of the [Microsoft Loop app](https://www.microsoft.com/en-us/microsoft-loop) to become available in Teams. Please note that "Live components" will be renamed "Loop components" in early 2022.

**Get tasks done faster together.** Crowd-source an agenda, track a group's action items, or take notes collectively. These are just a few scenarios made easier with live components.

**Share components.** In this release, you can share live components into different Teams chats. Recipients can edit from wherever they are and see updates instantly no matter where the changes were made. In future releases, live components will be supported in Teams meeting notes and channels, Outlook, and eventually across all Microsoft 365 applications.

**Start in chat, build from there.** Every component you create from Teams chat is automatically saved to a file in OneDrive. So, you might begin collaborating in chat then later move to the file, where you have a larger visual space for editing and can add as many components as you like.

## Clients and platforms

Available on Teams apps on Windows, Mac, Linux, iOS, and Android.

## Settings management

Live components are built with Microsoft Fluid Framework supported across Microsoft 365 suite and controlled from SharePoint Online and not from the Teams admin center.

You'll need the latest version of [SharePoint Online PowerShell module](/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell) to enable or disable all Fluid Experiences across your Office 365 tenant. Microsoft Fluid Framework defaults to **ON** for all targeted release tenants. Because live components are designed for collaboration, the components are always shared as editable by others, even if your tenant is set to default to view-only for other file types. See the **Learn more** link next to the setting for more details.

## Checking if the Fluid Framework is enabled through the SharePoint Online PowerShell Cmdlet

1. [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps#to-connect-with-a-user-name-and-password). 

2. Check if Fluid Framework is enabled by running the Get-SPOTenant cmdlet without any arguments.

3. Verify the value of IsFluidEnabled is **true**.

## Enabling the Fluid Framework through the SharePoint Online PowerShell Cmdlet

1. [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps#to-connect-with-a-user-name-and-password). 

2. Enable Fluid using the cmdlet Set-SPOTenant -IsFluidEnabled $true 
   
   The change will take a short time to apply across your tenancy. 

The feature will be available on Teams Windows Desktop, Mac, iOS, Android. When enabled, users will see a new option for inserting live components in the message compose experience for these clients.

## Disabling Fluid Framework through SharePoint Online PowerShell Cmdlet

1. [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

2. Disable Fluid using the Set-SPOTenant cmdlet Set-SPOTenant -IsFluidEnabled $false. 

   The change will take a short time to apply across your tenancy. 

If you need to re-enable this capability, you can use SharePoint Online PowerShell Cmdlets.

```powershell
C:\\WINDOWS\\system32&gt; Connect-SPOService
cmdlet Connect-SPOService at command pipeline position 1

Supply values for the following parameters:
Url: <https://a830edad9050849822e21011208-admin.sharepoint.com/>
PS C:\\WINDOWS\\system32&gt; set-SPOTenant -isFluidEnabled $true
PS C:\\WINDOWS\\system32&gt;
```
## Known issues

- Live components in chat cannot be edited via Office app when using Teams on Android.

- If tenant default file permissions are set to **Specific people (only the people the user specifies)**, and the sender removes some users from the Specific people list in the permissions dialog when creating a component, those users may still have access to the content. This issue is due to the access management limitation of the permission dialog and will be fixed in the future release.

- If the tenant's Conditional Access Policy settings prevent client network to connect to `https://pushchannel.1drv.ms`,  live components will not work as expected for saving real time changes to the service.

## Known limitations

- Searching for live components in Teams search will return a link to the component in office.com, not the chat message itself.

- Live components are disabled in federated chats.

- B2B guests will not be able to collaborate on a live component that is shared with them via Company Share Link unless the tenant sets an external access option to allow B2B guests to have the same access level as tenant members. For more information, see [Configure B2B external collaboration settings](/azure/active-directory/external-identities/delegate-invitations#configure-b2b-external-collaboration-settings).

- Teams Web client full support of Live components will be available soon.

- Live components are not supported in Teams channels yet, but their inline editing in channels is planned for more experiences in the future.

- With tenant default file permissions set to **Specific people (only the people the user specifies)**, copying link to live component and pasting in another chat requires the sender to use permissions dialog and add the recipients in the Specific people option to grant access properly.

- With tenant default file permissions set to **Specific people (only the people the user specifies)**, creating a live component in group chat with more than 20 members will require the sender to manually select the permission options for the component.

- Live components in chat will not load only if file was moved to different library. If file is moved to different folder then it will continue to load in chat.

## How to check your tenant's default file permissions

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/).

2. At the left, under **Admin centers**, select **SharePoint**.

3. Select **Policies** > **Sharing**, and under **File and folder links**, view your tenant's default file permissions.

## Storage of `.fluid` files

**How `.fluid` are stored?**

Live components created in Teams are backed by a `.fluid` file stored in the creator’s OneDrive for Business. Being a file in OneDrive for Business means that users can create, discover, and manage live components (`.fluid` files) as easily as any Office document.

Users can search for content in `.fluid` files from Office.com and OneDrive for Business.
`.fluid` files work with data governance features like eDiscovery, auditing, reporting, and legal hold.

`.fluid` files will now appear on Office.com and OneDrive for Business, such as in the Recent and Recommended areas.
`.fluid` files can be restored to previous versions from OneDrive for Business.

Chat participants must have a OneDrive account to create live components. Without a valid OneDrive account, chat participants might still be able to collaborate on a component created by other users who have a valid OneDrive account, but cannot create their own.

[Moving](https://support.microsoft.com/en-us/office/move-files-and-folders-between-onedrive-and-sharepoint-5916f90d-f58a-4bf9-b135-10853f516d0b) a `.fluid` file from OneDrive to a SharePoint site will result in the live component failing to load in Teams chat.

**What happens if the owner of the file leaves the company?**

[OneDrive retention policies](/microsoft-365/compliance/retention-policies-sharepoint?view=o365-worldwide#when-a-user-leaves-the-organization) apply to `.fluid` files just as they do to other content created by the user.

**How are `.fluid` files shared?**

Live components can be inserted in Teams chat or copied from one chat to another. (Live components aren't yet supported in channels.) They default to the tenant’s existing permissions, but users can change permissions before sending to ensure everyone has access.

Opening components from Teams chat in Office.com offers share functionality at the top of the window, similar to the sharing options offered for other Office documents.

**What if a `.fluid` file becomes corrupted or damaged?**

Version History allows you to review and copy from previous versions of the file.

**What apps can open and edit `.fluid` files?**

`.fluid` files can only be opened as links in your browser, such as Office.com, and as live components in Teams chat. If downloaded, they can't be opened again without first uploading them back to OneDrive for Business or SharePoint Online.
