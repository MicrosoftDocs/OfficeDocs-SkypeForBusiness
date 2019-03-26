---
title: "Block Point-to-Point file transfers"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 9adf9859-de5b-461e-92ea-b6ce4dd2f7c1
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
- Setup
description: "In Skype for Business Online, you have ability to control Point-to-Point (P2P) file transfers as part of existing conferencing policy settings. However, this allows or blocks file transfers for users whether or not they are transferring files to a user who is within the same organization or to a federated user from another organization. Following the steps below, you can block P2P file transfers with federated organizations or partners."
---

# Block Point-to-Point file transfers

In Skype for Business Online, you have ability to control Point-to-Point (P2P) file transfers as part of existing conferencing policy settings. However, this allows or blocks file transfers for users whether or not they are transferring files to a user who is within the same organization or to a federated user from another organization. Following the steps below, you can block P2P file transfers with federated organizations or partners.
  
 A very common scenario is when you want to allow internal users to use P2P file transfer but block file transfer with federated partners. For this scenario, you would need to do:
  
- Assign a conferencing policy with P2P file transfer enabled (_EnableP2PFileTransfer_ set to _True_) to users in your organization.
    
- Create a global external user communication policy set to block external P2P file transfers (_EnableP2PFileTransfer_ set to _False_) and assign it to a user in your organization. 
    
You can find out more about those settings [here](https://technet.microsoft.com/en-us/library/mt228132.aspx).
  
If a federated user outside your organization tries to send a file to a user where the policy has been applied, they will receive a **Transfer Failed** error. And if a user tries to send a file, they will receive a **File transfer is turned off** error.
  
To make this work, the user must be using a supported version of a 2016 Click-to-Run Skype for Business app that supports it. The following minimum version of Skype for Business 2016 Click-to-Run client is required:
  
|**Type**|**Release date**|**Version**|**Build**|
|:-----|:-----|:-----|:-----|
|First Release for Current Channel  <br/> |11/17/2016  <br/> |16.0.7571.2006  <br/> |Version 1611 (Build 7571.2006)  <br/> |
|Current Channel  <br/> |12/6/2016  <br/> |16.0.7571.2072  <br/> |Version 1611 (Build 7571.2072)  <br/> |
|Deferred Channel  <br/> |2/22/2017  <br/> |16.0.7369.2118  <br/> |Version 1609 (Build 7369.2118)  <br/> |
   
> [!CAUTION]
> Users that are using older versions of Skype for Business Windows apps or Mac clients will still be able to transfer files. 
  
## Verify and start Windows PowerShell

- **Check that you are running Windows PowerShell version 3.0 or higher**
    
1. To verify that you are running version 3.0 or higher: **Start Menu** > **Windows PowerShell**.
    
2. Check the version by typing _Get-Host_ in the **Windows PowerShell** window.
    
3. If you don't have version 3.0 or higher, you need to download and install updates to Windows PowerShell. See [Windows Management Framework 4.0 ](https://go.microsoft.com/fwlink/?LinkId=716845) to download and update Windows PowerShell to version 4.0. Restart your computer when you are prompted.
    
4. You will also need to install the Windows PowerShell module for Skype for Business Online that enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=294688). Restart your computer if you are prompted.
    
    If you need to know more, see [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/EN-US/library/dn568015.aspx).
    
- **Start a Windows PowerShell session**
    
1. From the **Start Menu** > **Windows PowerShell**.
    
2. In the **Windows PowerShell** window, connect to your Office 365 organization by running:
    
    > [!NOTE]
    > You only have to run the **Import-Module** command the first time you use the Skype for Business Online Windows PowerShell module.

   ```      
    Import-Module "C:\Program Files\Common Files\Skype for Business Online\Modules\SkypeOnlineConnector\SkypeOnlineConnector.psd1"
    $credential = Get-Credential
    $session = New-CsOnlineSession -Credential $credential
    Import-PSSession $session
   ```

   If you want more information about starting Windows PowerShell, see [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/EN-US/library/dn568015.aspx) or [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
    
## Disable P2P file transfers for your organization

By default, _EnableP2PFileTransfer_ is enabled on the organization's global policy. When it was created, your users were assigned the _BposSAllModality_ policy.
  
To allow P2P transfers for inside your organization but block external file transfers to another organization, you just need to change it at a global level. To do that, run:
    
  ```
  Set-CsExternalUserCommunicationPolicy -EnableP2PFileTransfer $False
  ```

## Disable P2P file transfers for a user

You can apply this to a user by creating a new policy and granting it to that user. To do that, run: 
> 
>   ```
>   New-CsExternalUserCommunicationPolicy -Identity BlockExternalFT -EnableP2PFileTransfer $False
>   ```
> 
>   ```
>   Grant-CsExternalUserCommunicationPolicy -PolicyName BlockExternalFT -Identity amosm@contoso.com
>   ```

## Want to know more about Windows PowerShell?

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
## Related topics
[Create custom external access policies](create-custom-external-access-policies.md)

[Set up client policies for your organization](set-up-client-policies-for-your-organization.md)

[Set up conferencing policies in your organization](set-up-conferencing-policies-for-your-organization.md)

  
 
