---
title: "Enable users for Enterprise Voice online and Phone System Voicemail"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 9/25/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- Ent_O365_Hybrid
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 28daebcb-c2dc-4338-b2d1-04345ece9c19
description: "Learn how to enable Phone System voice services for your Skype for Business users."
---

# Enable users for Enterprise Voice online and Phone System Voicemail
 
> [!Important]
> Skype for Business Online was retired on July 31, 2021 and PSTN connectivity between your on-premises environment, whether through Skype for Business Server or Cloud Connector Edition and Skype for Business Online, is no longer supported.  Learn how to connect your on-premises telephony network to Teams using [Direct Routing](/MicrosoftTeams/direct-routing-landing-page).

Learn how to enable Phone System voice services for your Skype for Business users.
  
The final step in deploying Phone System with on-premises PSTN connectivity is to enable your users for Phone System and voicemail. To enable these capabilities, you must be a user with the Global Administrator role, and be able to run remote PowerShell. You need to follow the steps in this topic for all user accounts that do not already have Enterprise Voice enabled for Skype for Business Online.
  
## Enable Phone System voice services

To enable a user for Phone System Voice and voicemail, you'll need to perform some initial steps, like checking to see if the Skype for Business Online Connector is deployed on your servers and enable your users for hosted voicemail.
  
### To enable your users for Phone System voice and voicemail

> [!NOTE]
> Skype for Business Online Connector is currently part of latest Teams PowerShell Module.
> If you're using the latest [Teams PowerShell public release](https://www.powershellgallery.com/packages/MicrosoftTeams/), you don't need to install the Skype for Business Online Connector.

1. Before you begin, check that the Teams PowerShell module is installed on your Front End Servers. If it's not, please  install using the instructions in [Teams PowerShell Module Installation](/microsoftteams/teams-powershell-install).
    
2. Start Windows PowerShell as an administrator.
    
3. Type the following and press Enter:
    
 ```powershell
  # When using Teams PowerShell Module

   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
```

  
4. Use the Set-CsUser cmdlet to assign the $EnterpriseVoiceEnabled and $HostedVoiceMail properties to your user as follows:
    
   ```powershell
   Set-CsUser -Identity "<User name>" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
   ```

    For example:
    
   ```powershell
   Set-CsUser -Identity "Bob Kelly" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
   ```

    > [!NOTE]
    > You can also specify a user by their SIP address, User Principal name (UPN), domain name and username (domain\username), and display name in Active Directory ("Bob Kelly"). 
  
## Update the Line URI and dial plan for users enabled for Phone System

This section describes how to update the Line URI and dial plan for users enabled for Phone System. 
  
### To update the Line URI

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Use the Start menu or desktop shortcut to open the Skype for Business Server Control Panel.
    
    > [!NOTE]
    > You can also open a browser window, and then enter the Administrator URL to open the Skype for Business Server Control Panel. 
  
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.
    
5. In the table, click the Skype for Business user account that you want to change line URI.
    
6. Click **Line URI**, and type a unique, normalized phone number (for example, tel:+14255550200). Then click **Commit**.
    
## Update the dial plan using on-premises Windows PowerShell cmdlets

You can assign per-user dial plans with Windows PowerShell and the [Grant-CsDialPlan](/powershell/module/skype/grant-csdialplan?view=skype-ps) cmdlet. You can run this cmdlet either from the Skype for Business Server 2015 or from a remote session of Windows PowerShell.
  
### To assign a per-user dial plan to a single user

- Use the [Grant-CsDialPlan](/powershell/module/skype/grant-csdialplan?view=skype-ps) cmdlet to assign the per-user dial plan RedmondDialPlan to the user Ken Myer:
    
  ```powershell
  Grant-CsDialPlan -Identity "Ken Myer" -PolicyName "RedmondDialPlan"
  ```

### To assign a per-user dial plan to multiple users

- The following command assigns the per-user dial plan RedmondDialPlan to all the users who work in the city of Redmond. For more information on the LdapFilter parameter used in this command, see the documentation for the [Get-CsUser](/powershell/module/skype/get-csuser?view=skype-ps) cmdlet:
    
  ```powershell
  Get-CsUser -LdapFilter "l=Redmond" | Grant-CsDialPlan -PolicyName "RedmondDialPlan"
  ```

> [!NOTE]
> You may use either Global or User dial plans for online users. Site dial plans cannot be used as these only apply to users who are hosted on premises and are assigned to an on-premises site. 
  
### To unassign a per-user dial plan

- Use the [Grant-CsDialPlan](/powershell/module/skype/grant-csdialplan?view=skype-ps) cmdlet to unassign any per-user dial plan previously assigned to Ken Myer. After the per-user dial plan is unassigned, Ken Myer will automatically be managed by using the global dial plan or the service-scope dial plan assigned to his Registrar or PSTN gateway. A service scope dial plan takes precedence over the global dial plan:
    
  ```powershell
  Grant-CsDialPlan -Identity "Ken Myer" -PolicyName $Null
  ```

## Update the voice routing policies using on-premises Windows PowerShell cmdlets

This section describes how to update the voice routing policies for users enabled for Phone System.
  
Phone System users must have a Voice Routing Policy assigned to them for calls to route successfully. This differs from on-premises business voice users who require a Voice Policy to be assigned to them to allow calls to route successfully. The Voice Routing Policy should contain PSTN usages that define authorized calls and routes for Phone System users. You can copy these PSTN usages from existing Voice Policies to new Voice Routing Policies. For more information, see [New-CsVoiceRoutingPolicy](/powershell/module/skype/new-csvoiceroutingpolicy?view=skype-ps).
  
> [!NOTE]
> All Phone System users are assigned the same online Voice Policy named BusinessVoice which defines the calling features allowed; for example, Allow Simultaneous Ring. 
  
### To assign a per-user voice routing policy to a single user

- Use the [Grant-CsVoiceRoutingPolicy](/powershell/module/skype/grant-csvoiceroutingpolicy?view=skype-ps) cmdlet to assign the per-user voice routing policy RedmondVoiceRoutingPolicy to the user Ken Myer:
    
  ```powershell
  Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName "RedmondVoiceRoutingPolicy"
  ```

### To assign a per-user voice routing policy to multiple users

- The next command assigns the per-user voice routing policy RedmondVoiceRoutingPolicy to all the users who work in the city of Redmond. For more information on the LdapFilter parameter used in this command, see [Get-CsUser](/powershell/module/skype/get-csuser?view=skype-ps).
    
  ```powershell
  Get-CsUser -LdapFilter "l=Redmond" | Grant-CsVoiceRoutingPolicy -PolicyName "RedmondVoiceRoutingPolicy"
  ```

    > [!NOTE]
    > You may use either Global or User voice routing policies for online users. Site voice routing policies cannot be used as these only apply to users who are hosted on premises and are assigned to an on-premises site. 
  
### To unassign a per-user voice routing policy

- Use the Grant-CsVoiceRoutingPolicy to unassign any per-user voice routing policy previously assigned to Ken Myer. After the per-user voice routing policy is unassigned, Ken Myer will automatically be managed by using the global voice routing policy.
    
  ```powershell
  Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName $Null
  ```

    For more information, see [Grant-CsVoiceRoutingPolicy](/powershell/module/skype/grant-csvoiceroutingpolicy?view=skype-ps).
