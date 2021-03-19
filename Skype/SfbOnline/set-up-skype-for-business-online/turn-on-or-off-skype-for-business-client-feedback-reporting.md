---
title: "Turn on or off Skype for Business client feedback reporting"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 35562b48-1da1-4081-8a3a-033d0f1986b2
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
description: "You can enable your Skype for Business users to use the built-in Skype for Business app feedback tool to let users report issues and provide feedback directly to Microsoft about their experience."
---
# Turn on or off Skype for Business client feedback reporting

You can enable your Skype for Business Online users to use the built-in Skype for Business app feedback tool to let users report issues and provide feedback directly to Microsoft about their experience. 
  
![Provide Feedback icon](../images/eac13837-04d9-4da1-8e80-54612cf6650d.png)
  
Using this tool, a user can copy the logs from the app on their device to help Microsoft better investigate and troubleshoot problems that they might have. 
  
![Report a problem using Settings icon](../images/2dfb5603-1d69-41fc-a43e-91a3379acbe0.png)
  
You can also use the  _EnableOnlineFeedbackScreenshot_ setting so users can include a screenshot of their device as a part of their feedback.
  
![Skype for Business client reporting form.](../images/d859578d-8116-4d4b-a08f-c0cae28b8b76.png)
  
> [!IMPORTANT]
> The logs collected by the app's feedback tool will be stored for up to a maximum of 90 days in the United States while the issue is being investigated. Because of this, please don't enable this feedback tool if this violates your organization's data protection policy. 
  
## Start Windows PowerShell

> [!NOTE]
> Skype for Business Online Connector is currently part of the latest Teams PowerShell module. If you're using the latest Teams PowerShell public release, you don't need to install the Skype for Business Online Connector.
1. Install the [Teams PowerShell module](https://docs.microsoft.com/microsoftteams/teams-powershell-install).
    
2. Open a Windows PowerShell command prompt and run the following commands: 

   ```powershell
   # When using Teams PowerShell Module

   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```
   If you want more information about starting Windows PowerShell, see [Connect to all Microsoft 365 or Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/library/dn568015.aspx) or [Set up your computer for Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
   
## Turn on client app feedback reporting for all the users in your organization

To enable feedback reporting for users in your organization and allow them to submit device screenshots, run:
 
  ```PowerShell
  Set-CsClientPolicy -Identity EnableOnlineFeedback -EnableOnlineFeedback $true -EnableOnlineFeedbackScreenshots $true
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

  
 
