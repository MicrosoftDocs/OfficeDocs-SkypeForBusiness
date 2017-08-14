---
title: New-CsExUmContact
ms.prod: SKYPEFORBUSINESS
ms.assetid: 085d0a0f-0efb-4c65-b742-2c1cb7a5ae8f
---


# New-CsExUmContact
[]
Creates a new Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010.
  
    
    


> [!NOTE]
> This cmdlet can be used only with Skype for Business on-premises. 
  
    
    


```

New-CsExUmContact -DisplayNumber <String> -OU <OUIdParameter> -RegistrarPool <Fqdn> -SipAddress <String> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

This example calls the **New-CsExUmContact** cmdlet to create a new Exchange UM Active Directory contact object. To create a new contact you must supply the SIP address (in this example, sip:exumsa1@fabrikam.com) of the Auto Attendant or Subscriber Access. In addition, you must supply the name of the pool where the Skype for Business Server 2015 Registrar service is running (RedmondPool.litwareinc.com), the OU where this information will be stored (OU=ExUmContacts,DC=litwareinc,DC=com), and the phone number of the Auto Attendant or Subscriber Access (2065554567). Because we didn't specifically set the AutoAttendant parameter, the default of False will be applied and this contact object will be assumed to be a Subscriber Access contact.
  
    
    

```

New-CsExUmContact -SipAddress sip:exumsa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065554567
```


### EXAMPLE 2

This example is similar to Example 1 in that it calls the **New-CsExUmContact** cmdlet to create a new Exchange UM contact. We again create a new Auto Attendant or Subscriber Access contact, this time with the SIP address sip:exumaa1@fabrikam.com. We then supply the name of the pool where the Skype for Business Server 2015 Registrar service is running (RedmondPool.litwareinc.com), the OU where this information will be stored (OU=ExUmContacts,DC=litwareinc,DC=com), and the phone number of the Auto Attendant or Subscriber Access (2065554567). The difference in this example is that we set the optional parameter AutoAttendant to True ($True) to show that this object is, in fact, an Auto Attendant contact.
  
    
    

```
New-CsExUmContact -SipAddress sip:exumaa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065559876 -AutoAttendant $True
```


## Detailed Description

Skype for Business Server 2015 works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on-premises), contact objects must be created with this cmdlet to apply the Auto Attendant and Subscriber Access functionality. These objects are created by calling the **New-CsExUmContact** cmdlet.
  
    
    
A contact object created with this cmdlet will not be available for use within the system until a hosted voice mail policy has been applied that configures routing for the contact. You can retrieve hosted voice mail policies by calling the **Get-CsHostedVoicemailPolicy** cmdlet. From the policies retrieved you can determine whether an appropriate global or site policy exists, or if a per-user policy exists that needs to be granted to this contact.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DisplayNumber_ <br/> |Required  <br/> |System.String  <br/> |The telephone number of the contact. Display numbers for each contact must be unique (for instance, no two Exchange UM contacts can have the same display number).  <br/> This value may begin with a plus sign (+) and may contain any number of digits. The first digit cannot be zero.  <br/> |
| _OU_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |The organizational unit (OU) where this contact will be located in Active Directory.  <br/> Full data type: Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |
| _RegistrarPool_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the pool on which the Registrar service is running.  <br/> Note that an Exchange UM contact in Skype for Business Server 2015 cannot be moved to pools that are part of Microsoft Office Communications Server 2007 or Microsoft Office Communications Server 2007 R2 deployments.  <br/> Full data type: Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |
| _SipAddress_ <br/> |Required  <br/> |System.String  <br/> |The SIP address of the contact. This must be a new address that does not already exist as a user or contact in Active Directory Domain Services. This value must begin with the string sip: followed by the SIP address.  <br/> |
| _AutoAttendant_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether this contact object is an Auto Attendant. (Auto Attendant provides a set of voice prompts that allow callers to navigate the phone system and reach the intended party.)  <br/> Default: False  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of this contact. The description is for use by administrators to identify the type of contact (Auto Attendant or Subscriber Access), the location, provider, or any other information that will identify the purpose of each Exchange UM contact.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns the results of this command. Running this cmdlet will display the newly created object; including this parameter will simply repeat that output, making the use of this parameter redundant.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

Creates an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.
  
    
    

## See also


#### 


  
    
    
 [Remove-CsExUmContact](remove-csexumcontact.md)
  
    
    
 [Set-CsExUmContact](set-csexumcontact.md)
  
    
    
 [Get-CsExUmContact](get-csexumcontact.md)
  
    
    
 [Move-CsExUmContact](move-csexumcontact.md)
  
    
    
 [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
