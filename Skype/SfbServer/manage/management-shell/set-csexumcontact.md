---
title: "Set-CsExUmContact"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 5/22/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c0fe0fdc-6fea-4334-8645-24ffd494db07
description: "Modifies an existing Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010."
---

# Set-CsExUmContact
 
Modifies an existing Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010.
  
> [!NOTE]
> This cmdlet can be used only with Skype for Business on-premises. 
  
```
Set-CsExUmContact -Identity <UserIdParameter> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example sets the AutoAttendant property of the Exchange UM contact with the SIP address exumsa4@fabrikam.com to True. We first call the **Get-CsExUmContact** cmdlet to retrieve the contact object. (We could also have used the contact's Active Directory display name, the contact's user principal name, or the contact's logon name.) This command retrieves the one contact with the provided Identity. That contact is then passed to the **Set-CsExUmContact** cmdlet, where we set its AutoAttendant parameter to True.
  
```
Get-CsExUmContact -Identity sip:exumsa4@fabrikam.com | Set-CsExUmContact -AutoAttendant $True
```

### EXAMPLE 2

This example is identical to Example 1, but instead of retrieving the contact by calling the **Get-CsExUmContact** cmdlet and piping that object to the **Set-CsExUmContact** cmdlet, we provide the **Set-CsExUmContact** cmdlet with the Identity of the contact we want to modify. Notice the format of the Identity: in this case we've used the full distinguished name of the contact object, which includes an auto-generated GUID (generated at the time the contact was created). We then set the AutoAttendant parameter of the contact to True.
  
```
Set-CsExUmContact -Identity "CN={1bf6208d-2847-45d0-828f-636f14da858b},OU=ExUmContacts,DC=litwareinc,DC=com" -AutoAttendant $True
```

## Detailed Description

Skype for Business Server 2015 works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on premises), contact objects must be created by using Windows PowerShell to apply the Auto Attendant and Subscriber Access functionality. These objects are created by calling the **New-CsExUmContact** cmdlet and can later be modified by using the **Set-CsExUmContact** cmdlet.
  
The easiest way to use this cmdlet is often to first call the **Get-CsExUmContact** cmdlet to retrieve an instance of the contact object you want to modify. Simply pipe the output of the **Get-CsExUmContact** cmdlet command to the **Set-CsExUmContact** cmdlet and assign values to the parameters for the properties you want to change. (For details, see the Examples section in this topic.) Alternatively, you can call the **Set-CsExUmContact** cmdlet, passing it the Identity of the contact object you want to modify.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |UserIdParameter  <br/> |The unique identifier of the contact object you want to modify. Contact identities can be specified using one of four formats: 1) The contact's SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).  <br/> Full data type: Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |
| _AutoAttendant_ <br/> |Optional  <br/> |Boolean  <br/> |Set the parameter to True if the contact object is an Auto Attendant. This parameter is False by default.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |String  <br/> |A description of this contact. The description is for use by administrators to identify the type of contact (Auto Attendant or Subscriber Access), the location, provider, or any other information that will identify the purpose of each Exchange UM contact.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |String  <br/> |The telephone number of the contact. Display numbers for each contact must be unique (no two Exchange UM contacts can have the same display number). Changing this value will also change the value of the LineURI property.  <br/> This value may begin with a plus sign (+) and may contain any number of digits. The first digit cannot be zero.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether or not the contact has been enabled for Skype for Business Server 2015. Setting this parameter to False will disable the contact, and the Auto Attendant or Subscriber Access associated with this contact will no longer function.  <br/> If you disable an account by using the Enabled parameter, the information associated with that account (including assigned hosted voice mail policies) is retained. If you later re-enable the account using the Enable parameter, the associated account information will be restored.  <br/> |
| _EnterpriseVoiceEnabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether the contact has been enabled for Enterprise Voice. If this value is set to False, the Auto Attendant or Subscriber Access feature associated with this contact will no longer be available.  <br/> |
| _ExchangeArchivingPolicy_ <br/> |Optional  <br/> |ExchangeArchivingPolicyOptionsEnum  <br/> |Indicates where the contact's instant messaging sessions are archived. Allowed values are:  <br/> Uninitialized  <br/> UseLyncArchivingPolicy  <br/> ArchivingToExchange  <br/> NoArchiving  <br/> |
| _PassThru_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Returns the results of the command. By default, this cmdlet does not generate any output.  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |String  <br/> |The SIP address of the contact. This must be a new address that does not already exist as a user or contact in Active Directory Domain Services.  <br/> Changing this value will also change the SIP address stored in the OtherIpPhone property.  <br/> The SipAddress can be used as the Identity value for the **Get-CsExUmContact** cmdlet commands to retrieve specific contacts. When calling that cmdlet, the new SipAddress will be used; queries for the old SIP address will not return an object. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact object. Accepts pipelined input of Exchange UM contact objects.
  
## Return Types

This cmdlet modifies an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact. When the PassThru parameter is used, it also returns an object of this type.
  
## See also

#### 

[New-CsExUmContact](new-csexumcontact.md)
  
[Remove-CsExUmContact](remove-csexumcontact.md)
  
[Get-CsExUmContact](get-csexumcontact.md)
  
[Move-CsExUmContact](move-csexumcontact.md)

