---
title: First steps before you migrate users from Skype for Business Online
ms.prod: SKYPEFORBUSINESS
ms.assetid: 98245b04-ded4-4186-8da3-ba1c554b5c39
---


# First steps before you migrate users from Skype for Business Online
[] **Summary:** Learn about what you need to do before you migrate users from Skype for Business Online to on-premises Skype for Business.
Before you start moving online users to your on-premises environment, check that all of the following are true:
  
    
    


- Your on-premises environment must be fully deployed and validated. For more information, see  [Deploying Lync Server 2013](http://technet.microsoft.com/library/b76795a4-4e71-4c70-a5c0-d1197fa8028c.aspx) or [Deploy Skype for Business Server 2015](deploy-skype-for-business-server-2015.md), depending on which version you are using on-premises. 
    
  
- Your online tenant must be configured for remote PowerShell Access.
    
    To do this, first install the Skype for Business Online connector module for Windows PowerShell, which you can get here:  [https://go.microsoft.com/fwlink/p/?LinkId=391911](https://go.microsoft.com/fwlink/p/?LinkId=391911).
    
    After you install the module, you can establish a remote session by typing the following cmdlets in the Skype for Business Server Management Shell:
    


  ```
  
Import-Module SkypeOnlineConnector
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


    For more information about how to establish a remote PowerShell session with Skype for Business Online, see  [Connecting to Lync Online By Using Windows PowerShell](http://technet.microsoft.com/library/6167dad9-9628-4fdb-bed1-bdb3f7108e64.aspx).
    
    For more information about using the Skype for Business Online connector PowerShell module, see  [Using Windows PowerShell to Manage Lync Online](http://technet.microsoft.com/library/9ef2d853-10fb-4e02-a552-dcf6818d7153.aspx).
    
  
- Your online tenant must be configured for Shared SIP Address Space. To do this, first start a remote Powershell session with Skype for Business Online. Then run the following cmdlet:
    
  ```
  Set-CsTenantFederationConfiguration -SharedSipAddressSpace $True
  ```


    > [!NOTE]
      > The SharedSipAddressSpace attribute needs to remain "True" until moving to online is final, and no users remain on-premises. 

After you've finished these steps, you can move on to  [Migrate online users to on-premises in Skype for Business Server](migrate-online-users-to-on-premises-in-skype-for-business-server.md).
  
    
    


