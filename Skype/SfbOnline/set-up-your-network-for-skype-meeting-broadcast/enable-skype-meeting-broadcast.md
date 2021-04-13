---
title: "Enable Skype Meeting Broadcast"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: micchan
ms.topic: article
ms.assetid: 5299cce0-850e-42dc-b6ae-2d0ee775c4a9
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
- SMB
description: "Before the people in your organization can use Skype Meeting Broadcast, you need to enable it. To do this, you need to know how to use Windows PowerShell. If you don't know Windows PowerShell, consider hiring a Microsoft partner to do this step for you."
---

# Enable Skype Meeting Broadcast

> [!IMPORTANT]
> Skype for Business Online is retiring on July 31, 2021, at which time access to the service will end. We encourage customers to begin the upgrade to Microsoft Teams, the core client for communications and teamwork in Microsoft 365.

Before the people in your organization can use Skype Meeting Broadcast, you need to enable it. To do this, you need to know how to use Windows PowerShell. If you don't know Windows PowerShell, consider hiring a [Microsoft partner](https://go.microsoft.com/fwlink/?linkid=391089) to do this step for you.



> [!NOTE]
> The Microsoft Teams admin center has replaced the Skype for Business admin center (Legacy portal). All settings for managing Skype for Business are now in the Teams admin center. You must be assigned the [Azure AD admin role](/azure/active-directory/roles/permissions-reference) of Global admin or Skype for Business admin to manage Skype for Business features in the Teams admin center. To learn more, see [Manage Skype for Business settings in the Microsoft Teams admin center](/MicrosoftTeams/skype-for-business-settings?bc=%2fskypeforbusiness%2fbreadcrumb%2ftoc.json&toc=%2fskypeforbusiness%2fsfbotoc%2ftoc.json).

  
## Enable Skype Meeting Broadcast using the Skype for Business admin center

![An icon showing the Skype for Business logo](../images/sfb-logo-30x30.png) **Using the Skype for Business admin center**

1. Sign in with your global admin account or Skype for Business admin account at [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).
    
2. In the admin center, go to **Admin centers** > **Teams**.
    
3. In the **Teams admin center**, go to **Legacy portal** > **Online meetings** > **Broadcast meetings**, and then select **Enable Skype Meeting Broadcast**.
    
## Enable Skype Meeting Broadcast using PowerShell

1. Install the [Teams PowerShell module](/microsoftteams/teams-powershell-install).
    
2. Open a Windows PowerShell command prompt and run the following commands: 

   ```powershell
   # When using Teams PowerShell Module
   
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```
3. Confirm your current Skype Meeting Broadcast configuration by running:
    
   ```PowerShell
   Get-CsBroadcastMeetingConfiguration
   ```

    Verify that the parameter  _EnableBroadcastMeeting_ is set to `False`.
    
     ![Skype Meeting Broadcast Enable Organization cmdlet.](../images/44abe30d-d3df-4ca9-9761-603a7ff78723.png)
  
9. Enable Skype Meeting Broadcast for your organization by running:
    
   ```PowerShell
   Set-CsBroadcastMeetingConfiguration -EnableBroadcastMeeting $True
   ```

    You can confirm that the setting is enabled by running  `Get-CsBroadcastMeetingConfiguration` again.
    
     ![Skype Meeting Broadcast Enable Organization Cmdlet.](../images/788515f0-32c9-415a-9235-6bfbe095e6f3.png)
  
    > [!TIP]
    > After you make the change, it may take up to an hour to take effect in the Skype Meeting Broadcast portal. 
  
10. Your users can now hold broadcast meetings with other users in your business. To get them started, point them to [What is a Skype Meeting Broadcast?](https://support.office.com/article/c472c76b-21f1-4e4b-ab58-329a6c33757d)
    
## Configure your network to broadcast meetings with external attendees

If you have a firewall, and you want to hold broadcasts with people outside of your business (who are not a federated business), you need to configure your network using these instructions: [Set up your network for Skype Meeting Broadcast](set-up-your-network-for-skype-meeting-broadcast.md). 
  
If you aren't experienced with configuring your firewall, consider hiring a [Microsoft partner](https://go.microsoft.com/fwlink/?linkid=391089) to do this step for you.
  
To skip this step and instead add another business to your federation, see [Allow users to contact external Skype for Business users](../set-up-skype-for-business-online/allow-users-to-contact-external-skype-for-business-users.md). 
  
## Related topics

[An introduction to Windows PowerShell and Skype for Business Online](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
  
[Set up Skype for Business Online](../set-up-skype-for-business-online/set-up-skype-for-business-online.md)

  
