---
title: "Managing Skype for Business Online and Microsoft Exchange from the same remote Windows PowerShell session"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 4eb4b5f0-f407-46bd-a2ac-a7ccbc387d51
description: "When you subscribe to Office 365, you not only get access to Skype for Business Online; you also get access to Exchange Online. You can use a remote session of Windows PowerShell to manage Skype for Business Online. You can also use a remote session of Windows PowerShell to manage Exchange. However, Skype for Business Online and Exchange Online do not share the same URI, nor do they use the same connection method. This implies that you need to use separate sessions to manage Skype for Business Online and Exchange. Or is there some way to manage both products by using a single remote session of Windows PowerShell?"
---

# Managing Skype for Business Online and Microsoft Exchange from the same remote Windows PowerShell session
[]
When you subscribe to Office 365, you not only get access to Skype for Business Online; you also get access to Exchange Online. You can use a remote session of Windows PowerShell to manage Skype for Business Online. You can also use a remote session of Windows PowerShell to manage Exchange. However, Skype for Business Online and Exchange Online do not share the same URI, nor do they use the same connection method. This implies that you need to use separate sessions to manage Skype for Business Online and Exchange. Or is there some way to manage both products by using a single remote session of Windows PowerShell?
  
As it turns out, you can not only manage both products from the same instance of Windows PowerShell, but setting up this dual management session is remarkably easy. To begin with, start Windows PowerShell and connect to Skype for Business Online the same way you always do: create a Credentials object, then create a new session that connects to Skype for Business Online:
  
```
$credential = Get-Credential "kenmyer@litwareinc.com"
$lyncSession = New-CsOnlineSession -Credential $credential
```

Next, use a similar process to connect to Exchange Online. Note that you do not need to create a new Credentials object. You can continue to use the same object ($credential) that you used when logging on to Skype for Business Online:
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

You should always use the URI https://outlook.office365.com/powershell-liveid/ when connecting to Exchange Online, and you should do so regardless of your Office 365 URI. After you are authenticated, you will automatically be redirected to the appropriate URI. This makes it especially important that you include the AllowRedirection parameter. If this parameter is omitted, you'll be authenticated, but redirection will fail, and you will not be connected to Exchange Online:
  
```
New-PSSession : [ps.outlook.com] The WinRM service cannot process the request because the request needs to be sent to a different machine. Use the redirect information to send the request to a new machine.  Redirect location reported: https://pod51043psh.outlook.com/powershell-liveid?PSVersion=3.0 . To automatically connect to the redirected URI, verify  MaximumConnectionRedirectionCount" property of session preference variable "PSSessionOption" and use "AllowRedirection" parameter on the cmdlet.
```

At this point, you should have two separate remote sessions running on your computer. To verify this, type the following command at the Windows PowerShell prompt:
  
```
Get-PSSession
```

You should see information similar to this displayed onscreen:
  
```
Id Name      ComputerName  State   ConfigurationName     Availability
-- ----      ------------  -----   -----------------     ------------
 1 Session1  pod510w43...  Opened  Microsoft.PowerShell     Available
 2 Session2  up02921vd...  Opened  Microsoft.Exchange       Available
```

You now have a pair of remote sessions that can be imported into your local session of Windows PowerShell. To do that, run these two commands:
  
```
Import-PSSession $lyncSession
Import-PSSession $exchangeSession
```

At this point, you will have both the Skype for Business Online and the Exchange Online cmdlets available for use. To verify this, run the following command, and make sure that you get back user information:
  
```
Get-CsOnlineUser -ResultSize 1
```

Then run the following Exchange command and verify that you get back mailbox information:
  
```
Get-Mailbox -ResultSize 1
```

When you want to end your management session, make sure that you close both remote sessions:
  
```
Remove-PSSession $lyncSession
Remove-PSSession $exchangeSession
```

## See also

#### 

[Configuring your computer for Skype for Business Online management](configuring-your-computer-for-skype-for-business-online-management.md)

