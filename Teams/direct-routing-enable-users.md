---
title: "Enable users for Direct Routing"
ms.reviewer: filippse
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to enable users for Microsoft Teams Phone Direct Routing."
---

# Enable users for Direct Routing

This article describes how to enable users for Direct Routing. This is step 2 of the following steps for configuring Direct Routing:

- Step 1. [Connect the SBC with Phone System and validate the connection](direct-routing-connect-the-sbc.md) 
- **Step 2. Enable users for Direct Routing**   (this article)
- Step 3. [Configure voice routing](direct-routing-voice-routing.md)
- Step 4. [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 


For information on all the steps required for setting up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

When you're ready to enable users for Direct Routing, follow these steps: 

1. Create a user in Microsoft 365 and assign a Phone System license.  
2. Ensure that the user is homed online.
3. Configure the phone number and enable enterprise voice. 
4. Assign Teams Only mode to users.

## Create a user and assign the license

There are two options for creating a new user in Microsoft 365. However, Microsoft recommends that your organization choose one option to avoid routing issues: 

- Create the user in on-premises Active Directory and sync the user to the cloud. See [Integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).
- Create the user directly in the Microsoft 365 admin center. See [Add users individually or in bulk to Microsoft 365 or Office 365 - Admin Help](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec). 

If your Skype for Business Online deployment coexists with Skype for Business 2015 or Lync 2010 or 2013 on-premises, the only supported option is to create the user in the on-premises Active Directory and sync the user to the cloud (Option 1). 

For information about license requirements, see [licensing and other requirements](direct-routing-plan.md#licensing-and-other-requirements) in [Plan Direct Routing](direct-routing-plan.md).

## Ensure that the user is homed online 

This step applies to Skype for Business Server Enterprise Voice enabled users being migrated to Teams Direct Routing.

Direct Routing requires the user to be homed online. You can check by looking at the RegistrarPool parameter, which needs to have a value in the infra.lync.com domain. Microsoft recommends, but doesn't require, that you change the LineURI from on-premises to online when migrating users to Teams Direct Routing. 

1. Connect a Microsoft Teams PowerShell session.

2. Issue the command: 

    ```PowerShell
    Get-CsOnlineUser -Identity "<User name>" | fl RegistrarPool,OnPremLineUri,LineUri
    ``` 
    If OnPremLineUri is populated with a <E.164 phone number>, the phone number was assigned on-premises and synchronized to Microsoft 365. If you want to manage the phone number online, clear the parameter using on-premises Skype for Business Management Shell and synchronize to Microsoft 365 before configuring the phone number using Teams PowerShell. 

1. From Skype for Business Management Shell, issue the command: 

   ```PowerShell
   Set-CsUser -Identity "<User name>" -LineUri $null
    ``` 
 > [!NOTE]
 > Do not set EnterpriseVoiceEnabled to False as there is no requirement to do so and this can lead to dial plan normalization issues if legacy Skype for Business phones are in use and the Tenant hybrid configuration is set with UseOnPremDialPlan $True. 
    
   After the changes have synced to Microsoft 365, the expected output of `Get-CsOnlineUser -Identity "<User name>" | fl RegistrarPool,OnPremLineUri,LineUri` is:

   ```console
   RegistrarPool                        : pool.infra.lync.com
   OnPremLineURI                        : 
   LineURI                              : 
   ```
 > [!NOTE]
 > All user's phone attributes must be managed online before you [decomission your on-premises Skype for Business environment](/skypeforbusiness/hybrid/decommission-on-prem-overview). 

## Configure the phone number and enable enterprise voice 

After you've created the user and assigned a license, you must configure the user's online phone settings. The configuration of Cloud Voicemail for the user is automatic; no other configuration needs to be done.

You can configure the phone number by using the Teams admin center or by using Teams PowerShell.

### Use Teams admin center

1. Go to **Users** -> **Manage users**.

2. Select a user.

2. Under **Account** **General information**, select **Edit**.

3. Under **Assign phone number**, from the **Phone number type** drop-down menu, select **Direct Routing**.

4. Enter an assigned phone number and a phone number extension if applicable.

5. Select **Apply.**

The account general information will now show the assigned phone number and Direct Routing as the phone number type.


### Use PowerShell

1. Connect to a Microsoft Teams PowerShell session. 

2. The next steps depend on whether you're managing the user's phone number on-premises or online. If you're managing the phone number on-premises, you must use the on-premises Skype for Business Management Shell, Control Panel, or one of the methods explained in [Decide how to manage attributes after decommissioning](/skypeforbusiness/hybrid/cloud-consolidation-managing-attributes).

   - If you're managing the user's phone number on-premises, you need to ensure that the user is Enterprise Voice enabled online by using the following command:

       ```PowerShell
       Set-CsPhoneNumberAssignment -Identity "<User name>" -EnterpriseVoiceEnabled $true
       ```
       
   - If you're managing the user's phone number online, you need to assign the phone number to the user by using the following command in Teams PowerShell. The user is automatically Enterprise Voice enabled by the command: 
 
       ```PowerShell
       Set-CsPhoneNumberAssignment -Identity "<User name>" -PhoneNumber <phone number> -PhoneNumberType DirectRouting
       ```
    
       For example, to add a phone number for user "Spencer Low," enter the following: 

       ```PowerShell
       Set-CsPhoneNumberAssignment -Identity "spencer.low@contoso.com" -PhoneNumber "+14255388797" -PhoneNumberType DirectRouting
       ```
       If the users "Spencer Low" and "Stacy Quinn" share the same base number with unique extensions, enter the following
    
       ```PowerShell
       Set-CsPhoneNumberAssignment -Identity "spencer.low@contoso.com" -PhoneNumber "+14255388701;ext=1001" -PhoneNumberType DirectRouting
       Set-CsPhoneNumberAssignment -Identity "stacy.quinn@contoso.com" -PhoneNumber "+14255388701;ext=1002" -PhoneNumberType DirectRouting
       ```

    Microsoft recommends, but doesn't require, that the phone number is configured as a full E.164 phone number with country code. You can configure phone numbers with extensions. These extensions will be used to look up users when the lookup against the base number returns more than one result. This functionality allows companies to configure phone numbers with the same base number and unique extensions. For lookup to be successful, the invite must include the full number with extension as follows:
    
    ```PowerShell
    To: <sip:+14255388701;ext=1001@sbc1.adatum.biz
    ```


## Configure sending calls directly to voicemail

Direct Routing allows you to end the call to a user and send it directly to the user's voicemail. If you want to send the call directly to voicemail, attach opaque=app:voicemail to the Request URI header. For example, "sip:user@yourdomain.com;opaque=app:voicemail". The Teams user won't receive the calling notification. Instead, The call will be connected to the voicemail of the user directly.

## Assign Teams Only mode to users to ensure calls land in Microsoft Teams

Direct Routing requires that users be in Teams Only mode to ensure incoming calls land in the Teams client. To put users in Teams Only mode, assign them the "UpgradeToTeams" instance of TeamsUpgradePolicy. For more information, see [Upgrade strategies for IT administrators](upgrade-to-teams-on-prem-implement.md). If your organization uses Skype for Business Server, see the following article for information about interoperability between Skype and Teams: [Migration and interoperability with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)
