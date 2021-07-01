---
title: "Set up mobile policies for your organization"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: beea47b2-7b9a-4b28-92d0-af65d80cd00f
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
description: "You can set up how your users connect to Skype for Business Online using the Skype for Business app on mobile devices, such as a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls."
---

# Set up mobile policies for your organization

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

You can set up how your users connect to Skype for Business Online using the Skype for Business app on mobile devices, such as a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls.
  
Mobile policy settings can be configured at the time a policy is created, or you can use the **Set-CsMobilityPolicy** cmdlet to modify the settings of an existing policy.
  
## Set your mobile policies

> [!NOTE]
> For all of the mobile policy settings in Skype for Business Online, you must use Windows PowerShell and you **can't use** the **Skype for Business admin center**. 
  
### Start Windows PowerShell

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
   
### Require a WiFi connection for video for a user

- To create a new policy for these settings, run:
   
   ```powershell
   New-CsMobilityPolicy -Identity MobilityPolicy -RequireWIFIForIPVideo $true
   ```
   See more on the [New-CsMobilityPolicy](/powershell/module/skype/New-CsMobilityPolicy) cmdlet.
    
- To grant the new policy you created to all of the users in your organization, run:
   
   ```powershell
   Grant-CsMobilityPolicy -Identity"amos.marble@contoso.com" -PolicyName MobilityPolicy
   ```
   See more on the [Grant-CsMobilityPolicy](/powershell/module/skype/Grant-CsMobilityPolicy) cmdlet.
    
  If you have already created a policy, you can use the [Set-CsMobilityPolicy](/powershell/module/skype/Set-CsMobilityPolicy) cmdlet to make changes to the existing policy, and then use the[Grant-CsMobilityPolicy](/powershell/module/skype/Grant-CsMobilityPolicy) cmdlet to apply the setting to your users.
  
### Prevent a user from using the Skype for Business app

- To create a new policy for these settings, run:
  ```PowerShell
  New-CsMobilityPolicy -Identity NoAppClientPolicy -EnableMobility $false 
  ```
  See more on the [New-CsMobilityPolicy](/powershell/module/skype/New-CsMobilityPolicy) cmdlet.
    
- To grant the new policy you created to Amos Marble, run:  
   
   ```powershell
   Grant-CsMobilityPolicy -Identity "amos.marble@contoso.com"-PolicyName NoAppClientPolicy
   ```
   See more on the [Grant-CsMobilityPolicy](/powershell/module/skype/Grant-CsMobilityPolicy) cmdlet.
    
  If you have already created a policy, you can use the [Set-CsMobilityPolicy](/powershell/module/skype/Set-CsMobilityPolicy) cmdlet to make changes to the existing policy, and then use the [Grant-CsMobilityPolicy](/powershell/module/skype/Grant-CsMobilityPolicy) cmdlet to apply the setting to your users.
  
### Prevent a user from making voice over IP calls using a mobile device

- To create a new policy for these settings, run:
   
   ```powershell
   New-CsMobilityPolicy -Identity VoIPClientPolicy -EnableIPAudioVideo  $false
   ```
   See more on the [New-CsMobilityPolicy](/powershell/module/skype/New-CsMobilityPolicy) cmdlet.
    
- To grant the new policy you created to all of the users in your organization, run:
   
   ```powershell
   Grant-CsMobilityPolicy -Identity "amos.marble@contoso.com" -PolicyName VoIPClientPolicy
   ```

  See more on the [Grant-CsMobilityPolicy](/powershell/module/skype/Grant-CsMobilityPolicy) cmdlet.
    
If you have already created a policy, you can use the [Set-CsMobilityPolicy](/powershell/module/skype/Set-CsMobilityPolicy) cmdlet to make changes to the existing policy, and then use the[Grant-CsMobilityPolicy](/powershell/module/skype/Grant-CsMobilityPolicy) cmdlet to apply the setting to your users.
  
## Want to know more about Windows PowerShell?

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
  - [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Microsoft 365 or Office 365](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  - [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))
    
  - [Using Windows PowerShell to manage Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
    
## Related topics
[Create custom external access policies](create-custom-external-access-policies.md)

[Block point-to-point file transfers](block-point-to-point-file-transfers.md)

[Set up client policies for your organization](set-up-client-policies-for-your-organization.md)

[Set up conferencing policies in your organization](set-up-conferencing-policies-for-your-organization.md)

  
