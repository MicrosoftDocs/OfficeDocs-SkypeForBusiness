---
title: "Enable users for Enterprise Voice online and Phone System in Office 365 Voicemail"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 9/25/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 28daebcb-c2dc-4338-b2d1-04345ece9c19
description: "Learn how to enable Phone System in Office 365 voice services for your Skype for Business users."
---

# Enable users for Enterprise Voice online and Phone System in Office 365 Voicemail
 
Learn how to enable Phone System in Office 365 voice services for your Skype for Business users.
  
The final step in deploying Phone System in Office 365 with on-premises PSTN connectivity is to enable your users for Phone System in Office 365 and voicemail. To enable these capabilities, you must be a user with the Office 365 Global Administrator role, and be able to run remote PowerShell. You need to follow the steps in this topic for all user accounts that do not already have Enterprise Voice enabled for Skype for Business Online.
  
## Enable Phone System in Office 365 voice services

To enable a user for Phone System in Office 365 Voice and voicemail, you'll need to perform some initial steps, like checking to see if the Skype for Business Online Connector is deployed on your servers and enable your users for hosted voicemail.
  
### To enable your users for Phone System in Office 365 voice and voicemail

1. Before you begin, check that the Skype for Business Online Connector (Windows PowerShell module) is deployed on your Front End Servers. If it's not, you can download it from [the download center](https://www.microsoft.com/en-us/download/details.aspx?id=39366). You can find more information about using this module at [Configuring your computer for Skype for Business Online management](https://technet.microsoft.com/en-us/library/dn362839%28v=ocs.15%29.aspx).
    
2. Start Windows PowerShell as an administrator.
    
3. Type the following and press Enter:
    
   ```
   Import-Module skypeonlineconnector
   ```

4. Type the following and press Enter:
    
   ```
   $cred = Get-Credential
   ```

    After you press Enter, you should see the Windows PowerShell Credential dialog box.
    
5. Type your tenant admin username and password, and click **OK**.
    
6. In the PowerShell window, type the following and press Enter:
    
   ```
   $Session = New-CsOnlineSession -Credential $cred -Verbose
   ```

7. Import the session by typing the following cmdlet:
    
   ```
   Import-PSSession $Session -AllowClobber
   ```

    When running PowerShell on a Skype for Business Server, the local Skype for Business cmdlets are already loaded when you open PowerShell. You must specify the -AllowClobber parameter to allow the online cmdlets to overwrite the on-premises cmdlets with the same name.
    
8. Use the Set-CsUser cmdlet to assign the $EnterpriseVoiceEnabled and $HostedVoiceMail properties to your user as follows:
    
   ```
   Set-CsUser -Identity "<User name>" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
   ```

    For example:
    
   ```
   Set-CsUser -Identity "Bob Kelly" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
   ```

    > [!NOTE]
    > You can also specify a user by their SIP address, User Principal name (UPN), domain name and username (domain\username), and display name in Active Directory ("Bob Kelly"). 
  
## Update the Line URI and dial plan for users enabled for Phone System in Office 365

This section describes how to update the Line URI and dial plan for users enabled for Phone System in Office 365. 
  
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

You can assign per-user dial plans with Windows PowerShell and the [Grant-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/grant-csdialplan?view=skype-ps) cmdlet. You can run this cmdlet either from the Skype for Business Server 2015 or from a remote session of Windows PowerShell.
  
### To assign a per-user dial plan to a single user

- Use the [Grant-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/grant-csdialplan?view=skype-ps) cmdlet to assign the per-user dial plan RedmondDialPlan to the user Ken Myer:
    
  ```
  Grant-CsDialPlan -Identity "Ken Myer" -PolicyName "RedmondDialPlan"
  ```

### To assign a per-user dial plan to multiple users

- The following command assigns the per-user dial plan RedmondDialPlan to all the users who work in the city of Redmond. For more information on the LdapFilter parameter used in this command, see the documentation for the [Get-CsUser](https://docs.microsoft.com/powershell/module/skype/get-csuser?view=skype-ps) cmdlet:
    
  ```
  Get-CsUser -LdapFilter "l=Redmond" | Grant-CsDialPlan -PolicyName "RedmondDialPlan"
  ```

> [!NOTE]
> You may use either Global or User dial plans for online users. Site dial plans cannot be used as these only apply to users who are hosted on premises and are assigned to an on-premises site. 
  
### To unassign a per-user dial plan

- Use the [Grant-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/grant-csdialplan?view=skype-ps) cmdlet to unassign any per-user dial plan previously assigned to Ken Myer. After the per-user dial plan is unassigned, Ken Myer will automatically be managed by using the global dial plan or the service-scope dial plan assigned to his Registrar or PSTN gateway. A service scope dial plan takes precedence over the global dial plan:
    
  ```
  Grant-CsDialPlan -Identity "Ken Myer" -PolicyName $Null
  ```

## Update the voice routing policies using on-premises Windows PowerShell cmdlets

This section describes how to update the voice routing policies for users enabled for Phone System in Office 365.
  
Phone System in Office 365 users must have a Voice Routing Policy assigned to them for calls to route successfully. This differs from on-premises business voice users who require a Voice Policy to be assigned to them to allow calls to route successfully. The Voice Routing Policy should contain PSTN usages that define authorized calls and routes for Phone System in Office 365 users. You can copy these PSTN usages from existing Voice Policies to new Voice Routing Policies. For more information, see [New-CsVoiceRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csvoiceroutingpolicy?view=skype-ps).
  
> [!NOTE]
> All Phone System in Office 365 users are assigned the same online Voice Policy named BusinessVoice which defines the calling features allowed; for example, Allow Simultaneous Ring. 
  
### To assign a per-user voice routing policy to a single user

- Use the [Grant-CsVoiceRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csvoiceroutingpolicy?view=skype-ps) cmdlet to assign the per-user voice routing policy RedmondVoiceRoutingPolicy to the user Ken Myer:
    
  ```
  Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName "RedmondVoiceRoutingPolicy"
  ```

### To assign a per-user voice routing policy to multiple users

- The next command assigns the per-user voice routing policy RedmondVoiceRoutingPolicy to all the users who work in the city of Redmond. For more information on the LdapFilter parameter used in this command, see [Get-CsUser](https://docs.microsoft.com/powershell/module/skype/get-csuser?view=skype-ps).
    
  ```
  Get-CsUser -LdapFilter "l=Redmond" | Grant-CsVoiceRoutingPolicy -PolicyName "RedmondVoiceRoutingPolicy"
  ```

    > [!NOTE]
    > You may use either Global or User voice routing policies for online users. Site voice routing policies cannot be used as these only apply to users who are hosted on premises and are assigned to an on-premises site. 
  
### To unassign a per-user voice routing policy

- Use the Grant-CsVoiceRoutingPolicy to unassign any per-user voice routing policy previously assigned to Ken Myer. After the per-user voice routing policy is unassigned, Ken Myer will automatically be managed by using the global voice routing policy.
    
  ```
  Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName $Null
  ```

    For more information, see [Grant-CsVoiceRoutingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csvoiceroutingpolicy?view=skype-ps).
    

