---
title: "First steps before you start migrating users from Lync Online to Lync on-premises in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 98245b04-ded4-4186-8da3-ba1c554b5c39
description: "Before you start moving Lync Online users to your on-premises environment, check that all of the following are true:"
---

# First steps before you start migrating users from Lync Online to Lync on-premises in Lync Server 2013
[]
Before you start moving Lync Online users to your on-premises environment, check that all of the following are true:
  
- Your Lync Server on-premises environment must be fully deployed and validated. For more information, see [Deploying Lync Server 2013](deploying-lync-server-2013.md). 
    
- Your Lync Online tenant must be configured for remote PowerShell Access.
    
    To do this, first install the Skype for Business Online module for Windows PowerShell, which you can get here: [https://go.microsoft.com/fwlink/p/?LinkId=391911](https://go.microsoft.com/fwlink/p/?LinkId=391911).
    
    After you install the module, you can establish a remote session by typing the following cmdlets in the Lync Server Management Shell:
    
  ```
  Import-Module LyncOnlineConnector
  ```

  ```
  $cred = Get-Credential
  ```

  ```
  $CSSession = New-CsOnlineSession -Credential $cred
  ```

  ```
  Import-PSSession $CSSession -AllowClobber
  ```

    For more information about how to establish a remote PowerShell session with Skype for Business Online, see [Connecting to Skype for Business Online by using Windows PowerShell](connecting-to-skype-for-business-online-by-using-windows-powershell.md).
    
    For more information about using the Skype for Business Online PowerShell module, see [Using Windows PowerShell to manage Skype for Business Online](using-windows-powershell-to-manage-skype-for-business-online.md).
    
- Your Lync Online must be configured for Shared SIP Address Space. To do this, first start a remote Powershell session with Lync Online. Then run the following cmdlet:
    
  ```
  Set-CsTenantFederationConfiguration -SharedSipAddressSpace $True
  ```

After you've finished these steps, you can move on to [Migrating Lync Online users to Lync on-premises in Lync Server 2013](migrating-lync-online-users-to-lync-on-premises.md).
  

