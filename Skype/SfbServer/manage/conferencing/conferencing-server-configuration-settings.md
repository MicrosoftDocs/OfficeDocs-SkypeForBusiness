---
title: "Manage conferencing server configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 36bed690-6e22-4e11-88c1-b40a20836c6a
description: "Summary: Learn how to manage conferencing server configuration settings in Skype for Business Server."
---

# Manage conferencing server configuration settings in Skype for Business Server
 
**Summary:** Learn how to manage conferencing server configuration settings in Skype for Business Server.
  
This topic describes how to manage conferencing configuration settings. For more information about how to plan and deploy conferencing, see [Plan for conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/conferencing.md) and [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md).
  
Conferencing configuration settings determine such things as the maximum allowed size for meeting content and handouts; maximum amount of bandwidth for the Application Sharing Conferencing service; storage limits and expiration periods; the URLs for the internal and external downloads of the supported client; pointers to internal and external URLs where users can obtain conferencing help and resources; and the ports used for application sharing, client audio, file transfers, and media traffic. These settings allow you to manage the actual servers themselves. These settings can be set by using Skype for Business Server Management Shell.
  
When you install Skype for Business Server, the system provides you with a single collection of conferencing configuration settings (the global collection). If you need to create custom settings for a site or service, you can do so using the **New-CsConferencingConfiguration** cmdlet. Note that new settings can be applied only at the site or service scope; you cannot create a new global collection of conferencing configuration settings, but you can modify the global collection by using the **Set-CsConferencingConfiguration** cmdlet. In addition, no site or service can host more than one collection of settings. If you try to create new settings for the Redmond site and the Redmond site already hosts a collection of conferencing configuration settings, then your command will fail.
  
## Manage conferencing configuration settings by using Skype for Business Server Management Shell

To manage conferencing configuration settings by using Skype for Business Server Management Shell, use the following cmdlets:
  
**Conferencing configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csconferencingconfiguration?view=skype-ps) <br/> |Returns information about the conferencing configuration settings for your organization.  <br/> |
|[New-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csconferencingconfiguration?view=skype-ps) <br/> |Creates a new collection of conferencing configuration settings.  <br/> |
|[Remove-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csconferencingconfiguration?view=skype-ps) <br/> |Removes the specified collection of conferencing configuration settings.  <br/> |
|[Set-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csconferencingconfiguration?view=skype-ps) <br/> |Modifies an existing collection of conferencing configuration settings.  <br/> |
   
The following command creates a new collection of conferencing configuration settings for the Redmond site (site:Redmond). In this example, one additional parameter is included (Organization) which is used to set the value of the Organization property to Litwareinc: 
  
```
New-CsConferencingConfiguration -Identity site:Redmond -Organization Litwareinc
```

Note that you can have only one such collection per site, so this command would fail if the Redmond site already has a collection of conferencing configuration settings. 
  
The next example defines a new collection of conferencing configuration settings, which are stored in memory initially, and then applied to the Redmond site at a later time. 
  
The first command uses the **New-CsConferencingConfiguration** cmdlet to create a new, in-memory collection of settings stored in the variable $x. The InMemory parameter specifies that the collection should be created in memory rather than immediately applied to the Redmond site.
  
After the collection has been created, the second command sets the value of the Organization property to Litwareinc. 
  
Finally, the third command uses the **Set-CsConferencingConfiguration** cmdlet to actually apply the new settings to the Redmond site:
  
```
$x = New-CsConferencingConfiguration -Identity site:Redmond -InMemory
$x.Organization = "Litwareinc"
Set-CsConferencingConfiguration -Instance $x
```

If you do not call the **Set-CsConferencingConfiguration** cmdlet, the new settings will never take effect. Instead, they will disappear as soon as you end your Windows PowerShell session or delete the variable $x.
  

