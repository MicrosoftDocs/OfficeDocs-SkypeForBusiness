---
title: Using PowerShell to manage Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
description: Learn to use Windows PowerShell to manage all of features found in Microsoft Teams.
appliesto: 
- Microsoft Teams
---

# Using PowerShell to manage Teams

Features in Teams can be managed using PowerShell or the Microsoft Teams and Skype for Business Admin Center. 

> ![Note]
> Not all of the features in Teams can be managed using the Teams connector module. You may need to use the Skype for Business connector. See [Download and install the Skype for Business Online connector](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-the-skype-for-business-online-connector)

### Step 1: Prerequisites

Remote management of Microsoft Teams by using PowerShell is supported only on 64-bit computers running one of the following operating systems:
  
- Windows 10
- Windows 8.1
- Windows 8 
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008
- Windows 7
    
In addition to a supported operating system, the computer must also be running the following:
  
- PowerShell 3.0 or higher
    
- Teams PowerShell connector module


### Step 2: Install PowerShell 3.0 or higher
[Use this topic for help](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-3-0) 

### Step 3: Download and install the Teams connector module
[Use this topic for help](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-the-skype-for-business-online-connector) 

Install the latest module from the PowerShell Gallery using: 
  
  Install-Module MicrosoftTeams

Or, for more information, the package can be found here: https://www.powershellgallery.com/packages/MicrosoftTeams/

### Step 4: Connect using the Teams connector module
[Use this topic for help](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-the-skype-for-business-online-connector) 

### Related topics
- [Manage Teams features with PowerShell](manage-features-with-powershell.md)
