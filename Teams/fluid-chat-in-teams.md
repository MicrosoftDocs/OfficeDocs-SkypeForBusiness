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

Microsoft Fluid Framework preview releases across all targeted release tenants with default **ON** state and will be overriding the view-only by default setting for newly created `.fluid` files and for files forwarded by the user. This setting will not apply to `.fluid` files with a “learn more” link right next to the setting and will not be applied to files shared through the OneDrive for Business ‘Share’ dial 

## Check if Fluid Framework is enabled through SharePoint Online PowerShell Cmdlet 

1. Connect to SharePoint Online PowerShell. 

2. Check if Fluid Framework is enabled by running the get cmdlet without any arguments. 

3. Get-SPOTenant 

4. Look for the value of IsFluidEnabled, and verify it is “true”. 
 
## Enable Fluid Framework through SharePoint Online PowerShell Cmdlet  

1. Connect to SharePoint Online PowerShell.  

2. Enable Fluid using the Set-SPOTenant cmdlet. 

3. Set-SPOTenant -IsFluidEnabled $true  

The change should take approximately 60 minutes to apply across your tenancy.  


## Disable Fluid Framework through SharePoint Online PowerShell Cmdlet  

1. Connect to SharePoint Online PowerShell.  

2. Disable Fluid using the Set-SPOTenant cmdlet.  

3. Set-SPOTenant -IsFluidEnabled $false  

The change should take approximately 60 minutes to apply across your tenancy.  

If you need to re-enable this capability, that can also be done through SharePoint Online PowerShell Cmdlets.  
 
For Example: 

PS C:\WINDOWS\system32> Connect-SPOService 


cmdlet Connect-SPOService at command pipeline position 1 

Supply values for the following parameters: 

Url: `https://a830edad9050849822e21011208-admin.sharepoint.com/` 

PS C:\WINDOWS\system32> set-SPOTenant -isFluidEnabled $false 

PS C:\WINDOWS\system32> 

## Related topics

[Manage Fluid Framework preview](/office365/troubleshoot/access-management/manage-fluid-framework-preview-access)