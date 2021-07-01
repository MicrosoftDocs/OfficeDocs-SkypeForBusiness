---
title: "Create custom external access policies"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 89cbd278-5480-473c-8cd9-04e07e5f9e0b
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1.keywords:
- NOCSH
ms.custom:
- Setup
description: "Skype for Business Online allows you to create additional external access policies. Unlike client or conferencing policies, where you can have multiple combinations, there are three predefined external access policies that can cover most of the scenarios."
---

# Create custom external access policies

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Skype for Business Online allows you to create additional external access policies. Unlike client or conferencing policies, where you can have multiple combinations, there are three predefined external access policies that can cover most of the scenarios. These are:
  
- No Federated or Skype Consumer Access (_Tag:NoFederationAndPIC_ )
    
- Federated Access Only (_Tag:FederationOnly_ )
    
- Federated and Consumer Access (_FederationAndPICDefault_)
    
Custom external policies allow you to create additional polices that aren't covered by the settings above. When the policy was created, you would be required to set all required parameters and you couldn't alter them later. Creating new custom policies allow you to control features such as Skype consumer access or a policy to disable public cloud audio/video, which is something that wasn't covered with predefined settings. Custom external access policies follow the same syntax as client, mobility, and conferencing policies. You can find out more about those settings [here](/previous-versions//mt228132(v=technet.10)).
  
To make this work, the user must be using a supported version of 2016 Click-to-Run Skype for Business app that supports it. The following minimum version of Skype for Business 2016 Click-to-Run client is required:
  
|**Type**|**Release date**|**Version**|**Build**|
|:-----|:-----|:-----|:-----|
|First Release for Current Channel  <br/> |11/17/2016  <br/> |16.0.7571.2006  <br/> |Version 1611 (Build 7571.2006)  <br/> |
|Current Channel  <br/> |12/6/2016  <br/> |16.0.7571.2072  <br/> |Version 1611 (Build 7571.2072)  <br/> |
|Deferred Channel  <br/> |2/22/2017  <br/> |16.0.7369.2118  <br/> |Version 1609 (Build 7369.2118)  <br/> |
   
> [!CAUTION]
> Users who are using older versions of Skype for Business Windows apps or Mac clients will still be able to transfer files. 
  
## Start Windows PowerShell

> [!NOTE]
> Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector.
1. Install the [Teams PowerShell module](/microsoftteams/teams-powershell-install).
    
2. Open a Windows PowerShell command prompt and run the following commands: 
 ```powershell
   # When using Teams PowerShell Module

   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```
   
   If you want more information about starting Windows PowerShell, see [Connect to all Microsoft 365 or Office 365 services in a single Windows PowerShell window](/microsoft-365/enterprise/connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window) or [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
   
## Create a custom external access policy for a user

To do this, run:
  
 
```powershell
New-CsExternalAccessPolicy -Identity BlockSkypeVideo -EnablePublicCloudAccess $True -EnablePublicCloudAudioVideoAccess $False -EnableFederationAccess $True -EnableOutsideAccess $True
```


```powershell
Grant-CsExternalAccessPolicy -PolicyName BlockSkypeVideo -Identity amosm@contoso.com
```

## Want to know more about Windows PowerShell?

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
  - [Why you need to use Microsoft 365 or Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  - [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))
    
  - [Using Windows PowerShell to manage Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
## Related topics
[Block point-to-point file transfers](block-point-to-point-file-transfers.md)

[Set up client policies for your organization](set-up-client-policies-for-your-organization.md)

[Set up conferencing policies in your organization](set-up-conferencing-policies-for-your-organization.md)

  
