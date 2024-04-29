---
ms.date: 11/28/2017
title: "Download and install Windows PowerShell 5.1"
ms.reviewer: 
ms.author: serdars
author: pamgreen
manager: serdars
ms.topic: article
ms.assetid: d739cd71-3c18-42ea-879f-b408bf53b1f4
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
- PowerShell
- LIL_Placement
description: "Download, install, and then use Windows PowerShell 5.1 to create a remote PowerShell session that connects to Skype for Business Online."
---

# Download and install Windows PowerShell 5.1

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

If you're using Windows 10 Anniversary Update, or Windows Server 2016, you should already have Windows PowerShell 5.1. That's because this application comes preinstalled with those operating systems.
  
To determine which version of Microsoft PowerShell you're using, do the following on your Windows 7 or Windows Server 2008 R2 or Windows Server 2012 computer:
  
1. Click **Start**, select **All Programs**, select **Accessories**, select **Windows PowerShell**, and then select **Windows PowerShell**.
    
2. In the PowerShell console, type the following command and then press ENTER:
    
   ```PowerShell
   Get-Host | Select-Object Version
   ```

3. Information similar to the following should then be displayed in the console window:
    
    <pre>
    Version <BR>
    ------- <BR>
    4.0
    </pre>

    If the returned Version number is 5.1, then you're running Windows PowerShell 5.1. If the returned Version number isn't 5.1, then you'll need to install Windows PowerShell 5.1. You can download Windows Management Framework 5.1, which includes Windows PowerShell 5.1, from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=54616).
  
After you've verified that Windows PowerShell 5.1 is installed, you must make sure that PowerShell has been configured for running remote scripts. To do that, start PowerShell as an administrator. On Windows 7, Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012 R2 do the following:
  
1. Click **Start**, select **All Programs**, select **Accessories**, select **Windows PowerShell**, right-click **Windows PowerShell**, and then select **Run as administrator**.
    
2. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run PowerShell under administrator credentials.
    
If you're running Windows 8, complete this procedure instead:
  
1. Access the Charms bar and select **Search**, and then right-click **Windows PowerShell**. You can quickly access the Charms bar on any Windows 8 computer (touch screen or nontouch screen) by holding down the Windows key and pressing C.
    
2. In the toolbar at the bottom of the screen, select **Run as administrator**.
    
3. If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run PowerShell under administrator credentials.
    
After PowerShell is running, you must change the execution policy to allow the running of remote scripts. In the PowerShell console, type the following command and then press ENTER:
```PowerShell
Set-ExecutionPolicy RemoteSigned -Force
```
   
 
> [!NOTE]
> When you run the preceding command, you might receive the following error message:> *Set-ExecutionPolicy : Access to the registry key'HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\PowerShell\\1\\ShellIds\\Micrsoft.PowerShell' is denied.* This error message typically occurs if you are not running PowerShell under administrator credentials. Close your session of PowerShell, and start a new session as an administrator.
 
To verify that the execution policy has been configured correctly, type the following at the PowerShell prompt and then press ENTER:
  
```PowerShell
Get-ExecutionPolicy
```

If you get back the following value, then everything has been configured correctly:
  
`RemoteSigned`

If you aren't currently running Windows PowerShell 5.1, you'll also need to download and install Windows Management Framework 5.1 from the Microsoft Download Center. This is an installation package that includes Windows PowerShell 5.1 and Windows Remote Management (WinRM) 3.0. This installation package might be required if you, for example, are running Windows 7 SP1 and have not yet updated to Windows PowerShell 5.1. If you're running Windows Server 2016, or Windows 10 Anniversary Update, there should be no need to install Windows PowerShell 5.1. Windows PowerShell 5.1 comes preinstalled on those operating systems.
  
Before installing Windows Management Framework 5.1:
  
- Make sure you have downloaded the correct version of the installation package. If you're running the 64-bit version of Windows 7 SP1, download the file Win7AndW2K8R2-KB3191566-x64.ZIP. If you're running the 32-bit version of Windows 7, download the file Win7-KB3191566-x86.ZIP.
    
- If you're running Windows 7 on your computer, make sure that you have installed Windows 7 Service Pack 1.

If you aren't sure which version of Windows you're running, or you aren't sure if you've installed Windows 7 Service Pack 1, select **Start**, right-click **Computer**, and then select **Properties**. This information will be reported in the System dialog box.
  
To install Windows Management Framework 5.1, complete the procedure in [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).
  
After the computer has rebooted, verify that Windows PowerShell can start and that the application can be run under administrative credentials. To do this:
  
1. Click **Start**, select **All Programs**, select **Accessories**, select **Windows PowerShell**, right-click **Windows PowerShell** and then select **Run as administrator**.
    
2. If the User Account Control dialog box appears, select **Yes** to verify that you want to run PowerShell under administrator credentials.
    
When the PowerShell console appears, you should then verify that the WinRM service is running and has been configured correctly. To verify that the service is running, type the following command at the PowerShell prompt and then press ENTER:
  
```PowerShell
Get-Service winrm
```

Information about the WinRM service will then be displayed on screen:
  
<pre>
Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...
</pre>

If the service Status doesn't equal "Running," start the WinRM service by typing the following command and then pressing ENTER:
  
```PowerShell
Start-Service winrm
```

After the service has started, run the following command to make sure that WinRM is using Basic authentication:
  
```PowerShell
winrm set winrm/config/client/auth '@{Basic="True"}'
```

Information similar to the following will be displayed onscreen:
  
<pre>
Auth
    Basic = true
    Digest = true
    Kerberos = true
    Negotiate = true
    Certificate = true
    CredSSP = false
</pre>

If basic authentication has been set to true, then you're ready to use PowerShell to connect to Skype for Business Online.
  
[!INCLUDE [LinkedIn Learning Info](../../common/office/linkedin-learning-info.md)]
   
## Related articles
[Set up your computer for Windows PowerShell](set-up-your-computer-for-windows-powershell.md) 

  

