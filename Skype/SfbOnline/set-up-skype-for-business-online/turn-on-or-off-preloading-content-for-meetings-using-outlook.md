---
title: "Turn on or off allowing content to be preloaded for meetings using Outlook"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: d217d422-f7e9-433d-ad24-bf41751f65ca
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
description: "See how to turn preloaded content on or off for Skype for Business meetings using files or attachments on an Outlook meeting invitation. "
---

# Turn on or off allowing content to be preloaded for meetings using Outlook

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Users can preload content, files, or attachments that are attached to an Outlook meeting invitation to a Skype for Business Online meeting, but you can it turn on or off. It's turned on by default for all organizations that are using Skype for Business Online. See how to [Preload attachments for a Skype for Business meeting](https://support.office.com/article/fd3d9f9d-b448-4754-b813-02e49393f251).
  
> [!NOTE]
> Currently, there are no cmdlets available in Skype for Business Online for setting or viewing online values for  _MaxContentStorageMB_ and _MaxUploadFileMB_. They are only available for on-premises deployments. It's important to know that content won't be uploaded to a meeting if the attached content exceeds the  _MaxUploadFileSizeMB_ or if the _MaxContentStorageMB_ limit is reached.
  
## To get you started

## Start Windows PowerShell

> [!NOTE]
> Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector.
1. Install the [Teams PowerShell module](/microsoftteams/teams-powershell-install).
    
2. Open a Windows PowerShell command prompt and run the following commands: 

   ```powershell
   # When using Teams PowerShell Module

   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

If you want more information about starting Windows PowerShell, see [Connect to all Microsoft 365 or Office 365 services in a single Windows PowerShell window](/microsoft-365/enterprise/connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window) or [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
  
## Turning it on or off

Being able to preload content attached to an Outlook meeting invitation to Skype for Business Online meetings is turned on by default, but you may need to prevent users in your organization from preloading content in their meetings.
  
> [!IMPORTANT]
> This setting can only be turned on or off for your entire organization; you can't turn it on or off for a single user. 
  
 **To turn it off, open Windows PowerShell and do the following:**
  
```PowerShell
Grant-CsGraphPolicy -PolicyName GraphDisabled 
```

 **If you want to turn it back on, open Windows PowerShell and do the following:**
  
```PowerShell
Grant-CsGraphPolicy -PolicyName GraphEnabled 
```

## Want to know more about Windows PowerShell?

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
  - [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Microsoft 365 or Office 365](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  - [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))
    
  - [Using Windows PowerShell to manage Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
## Related topics
[Set up Skype for Business Online](set-up-skype-for-business-online.md)

[Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md)

  
