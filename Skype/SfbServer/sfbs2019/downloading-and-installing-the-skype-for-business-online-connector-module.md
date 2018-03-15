---
title: "Downloading and installing the Skype for Business Online Connector module"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.assetid: a0c87219-b642-4201-85d4-a85c2163d1eb
description: "The Skype for Business Online Connector module includes the New-CsOnlineSession cmdlet, which enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers (see Configuring your computer for Skype for Business Online management for more information), can be downloaded from the Microsoft Download Center at https://go.microsoft.com/fwlink/?LinkId=294688. Download the LyncOnlinePowershell.exe file, and then complete the following procedure:"
---

# Downloading and installing the Skype for Business Online Connector module
[]
The Skype for Business Online Connector module includes the **New-CsOnlineSession** cmdlet, which enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers (see [Configuring your computer for Skype for Business Online management](configuring-your-computer-for-skype-for-business-online-management.md) for more information), can be downloaded from the Microsoft Download Center at [https://go.microsoft.com/fwlink/?LinkId=294688](https://go.microsoft.com/fwlink/?LinkId=294688). Download the LyncOnlinePowershell.exe file, and then complete the following procedure:
  
1. Double-click the **LyncOnlinePowershell.exe** file. 
    
2. In the Skype for Business Online Tenant PowerShell Setup wizard, on the **Microsoft Software License Terms** page, select **I accept the terms in the License Agreement**, and then click **Install**. If the **User Account Control** dialog box appears, click **Yes** to continue the installation. 
    
3. On the **Completed the Microsoft Lync Online, Tenant PowerShell Setup** page, click **Finish**.
    
The setup program copies the Skype for Business Online Connector module (and the **New-CsOnlineSession** cmdlet) to your local computer. To access the module, start a Windows PowerShell session under administrator credentials, and then run the following command: 
  
```
Import-Module LyncOnlineConnector
```

If you do not want to type this command every time you start Windows PowerShell, you can add the command to your Windows PowerShell profile. To do that, type the following command at the Windows PowerShell prompt and then press ENTER:
  
```
notepad.exe $profile
```

 When Notepad appears, add the following line to the bottom of the commands that are already in the profile (if any): 
  
```
Import-Module LyncOnlineConnector
```

Save the file. The next time you start Windows PowerShell, the Skype for Business Online Connector module will automatically be imported. Be aware that you will get an error message, and the module will not be loaded, if you are not running Windows PowerShell under administrator credentials.
  
In addition to installing the Skype for Business Online Connector module, LyncOnlinePowershell.exe also installs three additional components: 1) the Identity Service Client Runtime Library (IDCRL), used to handle client authentication to Skype for Business Online; 2) .NET Framework 4.5; and, 3) the Microsoft Visual C++ 2012 Redistributable (x64) package (version 11.0.50727). .NET Framework 4.5 provides the infrastructure used for building and running .NET applications, including Windows PowerShell. The Visual C++ Redistributable package installs Visual C++ runtime components for computers that do not have Microsoft Visual Studio 2012 installed.
  
Note that in March, 2014 a new version of the Skype for Business Online Connector module was posted to the Download center. Most users will be still able to connect to Skype for Business Online by using the previous version of the module (version number 5.0.8643.0). However, to ensure that you continue to get the latest updates it is recommended that everyone install the March, 2014 version of the Connector module anyway. Running the installation program will uninstall the previous version of the Connector module and then install the March, 2014 update.
  
To verify the version number of the Connector module that is currently installed on your computer, open Control Panel, open **Programs and Features**, and then check the version number for the **Microsoft Lync Online, Windows PowerShell Module**. 
  
## See also

#### 

[Configuring your computer for Skype for Business Online management](configuring-your-computer-for-skype-for-business-online-management.md)

