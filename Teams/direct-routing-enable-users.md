---
title: "Enable users for Direct Routing"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to enable users Microsoft Phone System Direct Routing."
---

# Enable users for Direct Routing, voice, and voicemail

This article describes how to enable users for Phone System Direct Routing.  This is step 2 of the following steps for configuring Direct Routing:

- Step 1. [Connect the SBC with Microsoft Phone System and validate the connection](direct-routing-connect-the-sbc.md) 
- **Step 2. Enable users for Direct Routing, voice, and voicemail**   (this article)
- Step 3. [Configure voice routing](direct-routing-voice-routing.md)
- Step 4. [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 


For information on all the steps required for setting up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

When you are ready to enable users for Direct Routing, follow these steps: 

1. Create a user in Microsoft 365 or Office 365 and assign a Phone System license. 
2. Ensure that the user is homed in Skype for Business Online. 
3. Configure the phone number and enable enterprise voice and voicemail. 
4. Assign Teams Only mode to users.

## Create a user and assign the license 

There are two options for creating a new user in Microsoft 365 or Office 365. However, Microsoft recommends that your organization choose one option to avoid routing issues: 

- Create the user in on-premises Active Directory and sync the user to the cloud. See [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).
- Create the user directly in the Microsoft 365 admin center. See [Add users individually or in bulk to Microsoft 365 or Office 365 - Admin Help](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec). 

If your Skype for Business Online deployment coexists with Skype for Business 2015 or Lync 2010 or 2013 on-premises, the only supported option is to create the user in the on-premises Active Directory and sync the user to the cloud (Option 1). 

For information about license requirements, see [licensing and other requirements](direct-routing-plan.md#licensing-and-other-requirements) in [Plan Direct Routing](direct-routing-plan.md).

## Ensure that the user is homed online and phone number is not being synced from on-premises (applicable for Skype for Business Server Enterprise Voice enabled users being migrated to Teams Direct Routing)

Direct Routing requires the user to be homed online. You can check by looking at the RegistrarPool parameter, which needs to have a value in the infra.lync.com domain. 
OnPremLineUriManuallySet parameter should also to be set to True. This is achieved by configuring the phone number and enable enterprise voice and voicemail using Skype for Business Online PowerShell.

1. Connect a Skype for Business Online PowerShell session.

2. Issue the command: 

    ```PowerShell
    Get-CsOnlineUser -Identity "<User name>" | fl RegistrarPool,OnPremLineUriManuallySet,OnPremLineUri,LineUri
    ``` 
    In case OnPremLineUriManuallySet is set to False and LineUri is populated with a <E.164 phone number>, please clean the parameters using on-premises Skype for Business Management Shell, before configuring the phone number using Skype for Business Online PowerShell. 

1. From Skype for Business Management Shell issue the command: 

   ```PowerShell
   Set-CsUser -Identity "<User name>" -LineUri $null -EnterpriseVoiceEnabled $False -HostedVoiceMail $False
    ``` 
   After the changes have synced to Office 365 the expected output of `Get-CsOnlineUser -Identity "<User name>" | fl RegistrarPool,OnPremLineUriManuallySet,OnPremLineUri,LineUri` would be:

   ```console
   RegistrarPool                        : pool.infra.lync.com
   OnPremLineURIManuallySet             : True
   OnPremLineURI                        : 
   LineURI                              : 
   ```

## Configure the phone number and enable enterprise voice and voicemail 

After you have created the user and assigned a license, the next step is to configure the user's phone number and voicemail. 

To add the phone number and enable for voicemail:
 
1. Connect a Skype for Business Online PowerShell session. 

2. Issue the command: 
 
    ```PowerShell
    Set-CsUser -Identity "<User name>" -EnterpriseVoiceEnabled $true -HostedVoiceMail $true -OnPremLineURI tel:<phone number>
    ```
    
    For example, to add a phone number for user "Spencer Low," enter the following: 

    ```PowerShell
    Set-CsUser -Identity "spencer.low@contoso.com" -OnPremLineURI tel:+14255388797 -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
    ```
    If the users "Spencer Low" and "Stacy Quinn" share the same base number with unique extensions, enter the following
    
    ```PowerShell
    Set-CsUser -Identity "spencer.low@contoso.com" -OnPremLineURI tel:+14255388701;ext=1001 -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
    Set-CsUser -Identity "stacy.quinn@contoso.com" -OnPremLineURI tel:+14255388701;ext=1002 -EnterpriseVoiceEnabled $true -HostedVoiceMail $true
    ```

    It's recommended, but not required, that the phone number used is configured as a full E.164 phone number with country code. It is supported to configure phone numbers with extensions which will be used to lookup users when the lookup against the base number returns more than one result. This allows companies to configure phone numbers with the same base number and unique extensions. For lookup to be successful, the invite must include the full number with extension as follows:
    ```PowerShell
    To: <sip:+14255388701;ext=1001@sbc1.adatum.biz
    ```
    
    > [!NOTE]
    > If the user’s phone number is managed on premises, use on-premises Skype for Business Management Shell or Control Panel to configure the user's phone number. 


## Configuring sending calls directly to voicemail

Direct Routing allows you to end the call to a user and send it directly to the user's voicemail. If you want to send the call directly to voicemail, attach opaque=app:voicemail to the Request URI header. For example, "sip:user@yourdomain.com;opaque=app:voicemail". In this case, the Teams user will not receive the calling notification, the call will be connected to the voicemail of the user directly.

## Assign Teams Only mode to users to ensure calls land in Microsoft Teams

Direct Routing requires that users be in Teams Only mode to ensure incoming calls land in the Teams client. To put users in Teams Only mode, assign them the "UpgradeToTeams" instance of TeamsUpgradePolicy. For more information, see [Upgrade strategies for IT administrators](upgrade-to-teams-on-prem-implement.md). If your organization uses Skype for Business Server or Skype for Business Online, see the following article for information about interoperability between Skype and Teams: [Migration and interoperability with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)
