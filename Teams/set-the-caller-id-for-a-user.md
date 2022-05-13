---
title: "Set the Caller ID for a user"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: jens, roykuntz
ms.topic: article
ms.assetid: c7323490-d9b7-421a-aa76-5bd485f80583
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business Online  
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
  - seo-marvel-mar2020
description: Learn about the Microsoft 365 and Office 365 default caller ID (a user's assigned telephone number), also known as Calling Line ID. You can change or block a user's caller ID.
---
# Set the Caller ID for a user

Phone System in Microsoft 365 provides a default caller ID that is the user's assigned telephone number. You can either change or block the caller ID (also called a Calling Line ID) for a user. You can learn more about how to use caller ID in your organization by going [How can caller ID be used in your organization](how-can-caller-id-be-used-in-your-organization.md).
  
By default, the following caller ID settings are **turned off**. This means that the Teams user's phone number can be seen when that user makes a call to a PSTN phone. You can change these settings as follows:
  
- **Outgoing caller ID** You can replace a user's Caller ID, which by default is their telephone number, with another phone number. For example, you could change the user's Caller ID from their phone number to a main phone number for your business or to a main phone number for the legal department. Additionally, you can set the Calling ID number to any online service number (toll or toll-free) or to an on-premises phone number through Direct Routing that is assigned to a resource account used by an Auto Attendant or a Call Queue.
    
  > [!NOTE]
  > If you want to use the *Service* parameter, you must specify a valid service number.
  > You need to use the PowerShell cmdlets New-CsCallingLineIdentity or Set-CsCallingLineIdentity in the Teams PowerShell module 2.3.1 or later for the Resource account number if it is not visible in the dropdown.
  
- **Block outbound caller ID.** You can block the outgoing Caller ID from being sent on a user's outgoing PSTN calls. Doing this will block their phone number from being displayed on the phone of a person being called.
    
- **Block incoming caller ID.** You can block a user from receiving Caller ID on any incoming PSTN calls.

- **Set Calling Party Name (CNAM).** For your Microsoft Teams users you can send a CNAM on outbound PSTN calls.
    
> [!IMPORTANT]
> Emergency calls will always send the user's telephone number (caller ID). 
  

  
To learn more about these settings and how you can use them, see [How can caller ID be used in your organization](how-can-caller-id-be-used-in-your-organization.md).
  
## Set your caller ID policy settings

> [!NOTE]
> To set the caller ID to a resource account phone number and to set the calling party name, use the PowerShell cmdlets New-CsCallingLineIdentity or Set-CsCallingLineIdentity in the Teams PowerShell module 2.3.1 or later. (These options are not currently available in the Microsoft Teams admin center.) 

Open 
a Windows PowerShell command prompt and run the following commands:

```PowerShell
# When using Teams PowerShell Module

Import-Module MicrosoftTeams
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
``` 

### View, create, and apply policy settings

1. To view all of the caller ID policy settings in your organization, run:

     ```PowerShell
     Get-CsCallingLineIdentity |fl
     ```
   For more information, see [Get-CsCallingLineIdentity](/powershell/module/skype/Get-CsCallingLineIdentity).
    
2. To create a new caller ID policy for your organization, use the New-CsCallingIdentity cmdlet:
    
     ```PowerShell
     New-CsCallingLineIdentity  -Identity Anonymous -Description "Anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
     ```
    In all cases, the "Service Number" field should not include an initial "+".

   For more information, see [New-CsCallingLineIdentity](/powershell/module/skype/New-CsCallingLineIdentity).
    
3. Apply the new policy you created by using the Grant-CsCallingIdentity cmdlet. For example, the following example applies the new policy to user Amos Marble.
    
     ```PowerShell
     Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName Anonymous
     ```
   For more information, see [Grant-CsCallingLineIdentity](/powershell/module/skype/Grant-CsCallingLineIdentity) cmdlet.
    

4. If you want to block the incoming caller ID, run:
    
   ```PowerShell
   Set-CsCallingLineIdentity  -Identity "Block Incoming" -BlockIncomingPstnCallerID $true
   ``` 

   For more information, see [Set-CsCallingLineIdentity](/powershell/module/skype/Set-CsCallingLineIdentity).
    
5. To apply the policy setting you created to a user in your organization, run:
    
   ```PowerShell
   Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Block Incoming"
   ```
   For more information, see [Grant-CsCallingLineIdentity](/powershell/module/skype/Grant-CsCallingLineIdentity).

6. To create a new Caller ID policy that sets the Caller ID to the phone number of the specified resource account and sets the Calling party name to Contoso:

   ```PowerShell
   $ObjId = (Get-CsOnlineApplicationInstance -Identity dkcq@contoso.com).ObjectId
   New-CsCallingLineIdentity  -Identity DKCQ -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $ObjId -CompanyName "Contoso"
   ```
**Note**: Configuring the -CompanyName attribute here does not guarantee all PSTN recipients will see it. For more information read: [More about Calling Line ID and Calling Party Name](https://docs.microsoft.com/en-us/microsoftteams/more-about-calling-line-id-and-calling-party-name)

If you have already created a policy, you can use the [Set-CsCallingLineIdentity](/powershell/module/skype/Set-CsCallingLineIdentity) cmdlet to make changes to the existing policy, and then use the [Grant-CsCallingLineIdentity](/powershell/module/skype/Grant-CsCallingLineIdentity) cmdlet to apply the settings to your users.
    
### Remove a policy setting

To remove a policy from your organization, run:
  
```PowerShell
Remove-CsCallingLineIdentity -Identity "My Caller ID Policy"
```
To remove a policy from a user, run:
  
```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName $null
```
## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 using a single point of administration that can simplify your daily work. To get started with Windows PowerShell, see these topics:
    
- [An introduction to Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)
    
- [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Microsoft 365](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
- [Best ways to manage Microsoft 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))
    
- [Using Windows PowerShell to manage Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)
    
- [Using Windows PowerShell to do common Skype for Business Online management tasks](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)
    
  
 ## Related topics
[Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)

[Different kinds of phone numbers used for Calling Plans](./different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[More about Calling Line ID and Calling Party Name](/skypeforbusiness/what-are-calling-plans-in-office-365/more-about-calling-line-ID-and-calling-party-name)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
