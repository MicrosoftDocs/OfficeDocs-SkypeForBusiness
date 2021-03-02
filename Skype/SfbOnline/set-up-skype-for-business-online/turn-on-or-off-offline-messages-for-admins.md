---
title: "Turn on or off Offline Messages for admins"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 8967a77f-caa2-4680-aa22-8faa32c716e4
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
description: "Learn how to send Skype for Business instant messages even when your contacts aren't signed in using PowerShell."
---

# Turn on or off Offline Messages for admins

You can send Skype for Business IMs to your contacts even if they aren't signed in. This feature lets your contacts know that you have been trying to reach them. You don't have to wait until someone is online before sending them a message.

For Offline messages, it's important to know:

- Offline messages won't be archived in the user's mailbox.

- Offline messages will be sent to the user's mailbox, and the user will be notified when they log in to Skype for Business.

- If the message recipient's status is set to **Do Not Disturb** or **Presenting**, they will receive a missed message that is sent from the recipient's Skype for Business client.

For more information, see [Use offline messaging in Skype for Business](https://support.office.com/article/ffdc6a43-71a1-40ee-bfcc-640d21324a3d).

## To get you started

 > [!Note]
  > Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector.
1. Install the [Teams PowerShell module](https://docs.microsoft.com/microsoftteams/teams-powershell-install).
    
2. Open a Windows PowerShell command prompt and run the following commands: 

   ```powershell
   # When using Teams PowerShell Module 1.1.6
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   
   # When using Teams PowerShell Module 2.0 or later
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```
If you want more information about starting Windows PowerShell, see [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/library/dn568015.aspx) or [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).

## Turning on or off Offline IM

> [!NOTE]
> Offline Messages are **only** available in the latest version of the Click-to-Run Skype for Business client and aren't available when an older Click-to-Run Skype for Business is used or an *.msi file was used to install the Skype for Business client.

To enable or disable Offline Messages send Offline Messages for users in your organization, set  _EnableIMAutoArchiving_ to `True` or `False`. By default, this is set to `True`.

To turn it off, use the **Set-CsClientPolicy** cmdlet and run:

```PowerShell
Set-CsClientPolicy -Identity Global -EnableIMAutoArchiving $False
```

To enable or disable Offline Messages send Offline Messages for a user, set  _EnableIMAutoArchiving_ to `True` or `False`. By default, this is set to  `True`. You can use an existing policy or create one like the example below.


  ```PowerShell
  New-CsClientPolicy -Identity OfflineIM
  Set-CsClientPolicy -Identity OfflineIM -EnableIMAutoArchiving $False
  Grant -CsClientPolicy -Identity "Tony Smith" - PolicyName OfflineIM
  ```

## Want to know more about Windows PowerShell?

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)

  - [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Microsoft 365 or Office 365](https://go.microsoft.com/fwlink/?LinkId=525041)

- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:

  - [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)

  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)

  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)

## Related topics
[Set up Skype for Business Online](set-up-skype-for-business-online.md)

[Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md)


