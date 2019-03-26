---
title: "Download and install the Skype for Business Online Connector module"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 9c1cc3dc-7d6d-43ca-8e4a-7763a3f78cb3
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- PowerShell
description: "Download, install, and then use the Skype for Business Online Connector to create a remote Windows PowerShell session that connects to Skype for Business Online.
"
---

# Download and install the Skype for Business Online Connector module

The Skype for Business Online Connector module includes the **New-CsOnlineSession** cmdlet, which enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers (see [Set up your computer for Skype for Business Online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md) for more information), can be downloaded from the Microsoft Download Center at [https://www.microsoft.com/en-us/download/details.aspx?id=39366](https://www.microsoft.com/en-us/download/details.aspx?id=39366). Download the SkypeOnlinePowershell.exe file, and then complete the following procedure:
  
1. Double-click the **SkypeOnlinePowershell.exe** file.
    
2. In the Skype for Business Online, Windows PowerShell setup wizard, on the **Microsoft Software License Terms** page, select **I accept the terms in the License Agreement**, and then click **Install**. If the **User Account Control** dialog box appears, click **Yes** to continue the installation.
    
3. On the **Completed the Skype for Business Online, Windows PowerShell Module** page, click **Finish**.
    
The setup program copies the Skype for Business Online Connector module (and the **New-CsOnlineSession** cmdlet) to your computer. To access the module, start a Windows PowerShell session under administrator credentials, and then run the following command:
  
```
Import-Module "C:\\Program Files\\Common Files\\Skype for Business Online\\Modules\\SkypeOnlineConnector\\SkypeOnlineConnector.psd1"
```

If you don't want to type this command every time you start Windows PowerShell, you can add the command to your Windows PowerShell profile. To do that, type the following command at the Windows PowerShell prompt and then press ENTER:
  
```
notepad.exe $profile
```

 When Notepad appears, add the following line to the bottom of the commands that are already in the profile (if any):
  
```
Import-Module SkypeOnlineConnector
```

Save the file. The next time you start Windows PowerShell, the Skype for Business Online Connector module will automatically be imported. Be aware that you will get an error message, and the module will not be loaded, if you are not running Windows PowerShell under administrator credentials.
  
In addition to installing the Skype for Business Online Connector module, SkypeOnlinePowershell.exe also installs three additional components: 1) the Identity Service Client Runtime Library (IDCRL), used to handle client authentication to Skype for Business Online; 2) .NET Framework 4.5; and, 3) the Microsoft Visual C++ 2012 Redistributable (x64) package (version 11.0.50727). .NET Framework 4.5 provides the infrastructure used for building and running .NET applications, including Windows PowerShell. The Visual C++ Redistributable package installs Visual C++ runtime components for computers that do not have Microsoft Visual Studio 2012 installed.
  
To verify the version number of the Connector module that is currently installed on your computer, open Control Panel, open **Programs and Features**, and then check the version number for the **Skype for Business Online, Windows PowerShell Module**.
  
## Related topics
[Set up your computer for skype for business online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md)

  
 
