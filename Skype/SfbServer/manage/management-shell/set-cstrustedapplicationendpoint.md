---
title: "Set-CsTrustedApplicationEndpoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6c2713f4-8e2c-48fc-9f27-07c1d6b87a18
description: "Modifies an existing endpoint contact for a trusted application. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsTrustedApplicationEndpoint
 
Modifies an existing endpoint contact for a trusted application. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsTrustedApplicationEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-Enabled <$true | $false>] [-EnabledForFederation <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrimaryLanguage <String>] [-SecondaryLanguages <MultiValuedProperty>] [-SipAddress <String>] [-Type <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example modifies the application endpoint contact object with the SIP address endpoint1@litwareinc.com. Notice that the Identity value begins with the string sip: followed by the SIP address. The next parameter, DisplayName, is given a value of "Endpoint 1", which changes the display name of the contact to that value.
  
```
Set-CsTrustedApplicationEndpoint -Identity "sip:endpoint1@litwareinc.com" -DisplayName "Endpoint 1"
```

### EXAMPLE 2

This example modifies the display number of the endpoint application with the display name Endpoint 1. The command begins with a call to the **Get-CsTrustedApplicationEndpoint** cmdlet with an Identity of Endpoint 1. This retrieves the endpoint contact object with that display name. This object is then piped to the **Set-CsTrustedApplicationEndpoint** cmdlet, which modifies the DisplayNumber to the value, in this case, (425)555-1212.
  
```
Get-CsTrustedApplicationEndpoint -Identity "Endpoint 1" | Set-CsTrustedApplicationEndpoint -DisplayNumber "(425)555-1212"
```

## Detailed Description

A trusted application endpoint is an Active Directory contact object that enables routing of calls to a trusted application. This cmdlet modifies an existing endpoint contact object in Active Directory Domain Services.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity (the distinguished name) or the SIP address of the application endpoint to be modified.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |The display name of the endpoint contact object.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |System.String  <br/> |The telephone number of the contact as it will appear in the Address Book.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether the contact is enabled for Skype for Business Server 2015.  <br/> Default: True  <br/> |
| _EnabledForFederation_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether federated users have access to this contact.  <br/> Default: False  <br/> |
| _EnterpriseVoiceEnabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether the contact is enabled for Enterprise Voice.  <br/> Default: True  <br/> |
| _ExchangeArchivingPolicy_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.ExchangeArchivingPolicyOptionsEnum  <br/> |Indicates where the contact's instant messaging sessions are archived. Allowed values are:  <br/> \* Uninitialized  <br/> \* UseLyncArchivingPolicy  <br/> \* ArchivingToExchange  <br/> \* NoArchiving  <br/> |
| _LineURI_ <br/> |Optional  <br/> |System.String  <br/> |The phone number of the contact. Must be in the format TEL:\<number\>, for example TEL:+14255551212.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Including this parameter will cause the cmdlet to not only modify the contact object but will return the new object as output.  <br/> |
| _PrimaryLanguage_ <br/> |Optional  <br/> |System.String  <br/> |The primary language used for the trusted application. The language must be configured using a valid language code, such as en-US (U.S. English), fr-FR (French), etc.  <br/> |
| _SecondaryLanguages_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty  <br/> |A collection of languages that can also be used for trusted applications. Values must be configured as a comma-separated values list of language codes. For example, the following syntax sets French Canadian and French as secondary languages: -SecondaryLanguages "fr-CA","fr-FR".  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |You cannot modify the SIP address of a contact. The SIP address is assigned when the application endpoint is created.  <br/> |
| _Type_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not used with this cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact object. Accepts pipelined input of trusted application endpoint objects.
  
## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.
  
## See also

#### 

[New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)
  
[Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)
  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)

