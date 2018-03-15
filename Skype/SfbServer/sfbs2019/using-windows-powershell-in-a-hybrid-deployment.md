---
title: "Using Windows PowerShell in a hybrid deployment with Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: b19625d4-4b68-403c-a072-5296aa590556
description: "In a hybrid deployment, an organization has some users homed on the on-premises version of Lync Server 2013 and other users homed on Skype for Business Online. You can use a single session of Windows PowerShell to simultaneously manage both your on-premises version of Lync Server and your Skype for Business Online tenant. To do this, you'll need to understand two key things:"
---

# Using Windows PowerShell in a hybrid deployment with Skype for Business Online
[]
In a hybrid deployment, an organization has some users homed on the on-premises version of Lync Server 2013 and other users homed on Skype for Business Online. You can use a single session of Windows PowerShell to simultaneously manage both your on-premises version of Lync Server and your Skype for Business Online tenant. To do this, you'll need to understand two key things:
  
1. How to make a simultaneous connection to Lync Server and Skype for Business Online.
    
2. How to reference Skype for Business Online settings from this simultaneous connection.
    
Making a simultaneous connection to Lync Server and Skype for Business Online is surprisingly easy. To do this, start by connecting Lync Server the same way you always do, either by starting the Lync Server Management Shell or by creating a remote connection to a Front End pool. After you have successfully connected to the on-premises version of Lync Server, you can then connect to Skype for Business Online by using the same procedure that you would use if you were connecting only to Skype for Business Online. To make this connection, you must first create a Windows PowerShell credentials object by using your Office 365 logon information. To do that, type the following at the Windows PowerShell prompt and then press ENTER:
  
```
$credential = Get-Credential
```

After you press ENTER, you'll see the **Windows PowerShell Credential** dialog box: 
  
![Windows PowerShell log in credentials](media/LyncOnlinePowerShell_Empty_Credentials_Box.png)
  
In the **User name** box, type your Skype for Business Online name. In the **Password** box, type your Skype for Business Online password (the password will be masked and will not be visible onscreen). For example, if your user name is kenmyer@litwareinc.com and your password is p@ssw0rd!, the dialog box will look like this: 
  
![Windows PowerShell credentials log in](media/LyncOnlinePowerShell_Filled_CredentialsBox.png)
  
To create the credentials object, click **OK**. After you have created the credentials object, you can connect to Skype for Business Online by running the following command:
  
```
$session = New-CsOnlineSession -Credential $credential
```

Make sure that you type the command exactly as shown. Note that it does not matter what the name of your Skype for Business Online domain is. The **New-CsOnlineSession** cmdlet will connect you to Office 365 and log you on by using the supplied credentials. After you make the connection and have been authenticated, you will then be automatically redirected to the appropriate URI. 
  
If your connection succeeds, you'll see a message similar to this in the Windows PowerShell console:
  
```
VERBOSE: Determining domain to admin
VERBOSE: AdminDomain = litwareinc.com
VERBOSE: Discovering PowerShell endpoint URI
VERBOSE: TargetUri = https://webdir0d.litwareinc.com/OcsPowerShellLiveId
VERBOSE: Requesting authentication token
VERBOSE: Success
VERBOSE: Initializing remote session
VERBOSE: Success
Id Name       ComputerName    State        ConfigurationName     Availability -- ----       ------------    -----        -----------------     ------------
2 Session2    litwarein...    Opened       Microsoft.PowerShell  Available
```

After you have successfully established a connection to Skype for Business Online, import that session by running a command similar to the following:
  
```
Import-PSSession $session -AllowClobber
```

> [!NOTE]
> The AllowClobber parameter ensures that all the Skype for Business Online cmdlets are imported, including cmdlets that have the same name as the regular Lync Server cmdlets. There will be a large number of these cmdlets because most of the Skype for Business Online cmdlets, including [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md), [New-CsExUmContact](new-csexumcontact.md), [Remove-CsVoicePolicy](remove-csvoicepolicy.md), and so on, have an on-premises equivalent. The paired cmdlets (for example, the Lync Server **Get-CsMeetingConfiguration** cmdlet and the Skype for Business Online **Get-CsMeetingConfiguration** cmdlet) are identical: it does not matter which cmdlet you use. The only reason to use the AllowClobber parameter is to prevent warning messages from appearing on your screen. 
  
At this point, you are ready to begin managing both the on-premises version of Lync Server and Skype for Business Online. At this point, you might also have an important question: how do you differentiate between Lync Server policies and settings and Skype for Business Online policies and settings? For example, you might want to change the global meeting configuration settings. To do so, you run this command:
  
```
Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False
```

This command modifies the global settings. But which global settings? Lync Server on-premises? Skype for Business Online? Both? Neither?
  
In this particular case, the on-premises settings will be modified. How do we know that? Because the Tenant parameter was not included in the command. If you are simultaneously connected to Lync Server on-premises and to Skype for Business Online, cmdlets that can work against either platform will run against Lync Server unless you tell them otherwise. And the only way to tell them otherwise is to include the Tenant parameter when running the command. For example, this command updates the global settings for the Skype for Business Online tenant with the Tenant ID bf19b7db-6960-41e5-a139-2aa373474354:
  
```
Set-CsMeetingConfiguration -Identity "global" -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AdmitAnonymousUsersByDefault $False
```

The Tenant parameter is the key. This command returns the global external access policy for Lync Server on-premises:
  
```
Get-CsExternalAccessPolicy -Identity "global"
```

And this command returns the global external access policy for your Skype for Business Online tenant:
  
```
Get-CsExternalAccessPolicy -Identity "global" -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"
```

Keep in mind that there are well over 700 on-premises cmdlets. However, the vast majority of those cmdlets do not have a Tenant parameter, meaning that they cannot be used with Skype for Business Online. Note, too that there are a handful of cmdlets that have a Tenant parameter, but are not yet available for use with Skype for Business Online. To retrieve the exact set of cmdlets that can be used with Skype for Business Online, run this command from the Windows PowerShell prompt:
  
```
Get-Module
```

Information similar to the following will appear onscreen:
  
```
ModuleType Name                 ExportedCommands
---------- ----                 ----------------
Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A…}
Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl…}
```

The module with the ModuleType Script is the module containing the Skype for Business Online cmdlets. To return a list of those cmdlets, run the **Get-Command** cmdlet, using the name of the Script module as the module name: 
  
```
Get-Command -Module tmp_5astd3uh.m5v
```

Windows PowerShell will then display a list of all of the Skype for Business Online cmdlets.
  
 **Troubleshooting Connection Problems in a Hybrid Deployment**
  
In some cases, administrators might experience problems logging on to Office 365 when using an on-premises account (for example, administrator@litwareinc.net) rather than an Office 365 account (such as administrator@litwareinc.onmicrosoft.com). If directory synchronization is working properly then you should be able to log on using either account; that's one of the advantages of a hybrid deployment. However, there have been instances where an administrator has been unable to log on using his or her on-premises account. This is typically due to autodiscovery pointing the log-on effort to the on-premises installation of Lync Server instead of Office 365.
  
Fortunately, there is an easy way to workaround this problem. When using the **New-CsOnlineSession** cmdlet to log on to Office 365, simply include the OverrideAdminDomain parameter followed by the Office 365 domain name. For example, to log on to Office 365 using the account administrator@litwareinc.net, include the OverrideAdminDomain parameter followed by the domainname litwareinc.onmicrosoft.com: 
  
```
$session = New-CsOnlineSession -Credential $credential -OverrideAdminDomain "litwareinc.onmicrosoft.com"
```

That command will explicitly direct the logon attempt to the Office 365 servers and the litwareinc.onmicrosoft.com domain.
  

