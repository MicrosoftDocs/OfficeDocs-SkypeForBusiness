---
title: "New-CsTrustedApplicationEndpoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 78b34ba4-4c31-4f68-9069-3c7e7c162fbf
description: "Creates a new endpoint contact for a trusted application. This cmdlet was introduced in Lync Server 2010."
---

# New-CsTrustedApplicationEndpoint
 
Creates a new endpoint contact for a trusted application. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsTrustedApplicationEndpoint -ApplicationId <String> -TrustedApplicationPoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrimaryLanguage <String>] [-SecondaryLanguages <MultiValuedProperty>] [-SipAddress <String>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example creates a trusted application endpoint for the application with the Application ID tapp1 homed on the pool TrustPool.litwareinc.com. ApplicationID and TrustedApplicationPoolFqdn are the only parameters that are required to create a trusted application endpoint. However, keep in mind that assigning values to only these two parameters will auto-generate a SIP address for the contact. In order to ensure the SIP address is unique, the auto-generated address will include a globally unique identifier (GUID) and will look something like this: sip:RtcApplication-fbf9e2d1-c6aa-45a3-a045-b92d4ef961b2@litwareinc.com. If you'd like a more readable SIP address, see Example 2. 
  
```
New-CsTrustedApplicationEndpoint -ApplicationId tapp1 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com
```

### EXAMPLE 2

Example 2 is identical to Example 1 in that it creates a trusted application endpoint for the application with the Application ID tapp1 on the TrustPool.litwareinc.com pool. Unlike Example 1, we include one more parameter in our endpoint creation: SipAddress. Rather than allowing the system to generate a SIP address, we've specified an address of endpoint1@litwareinc.com.
  
```
New-CsTrustedApplicationEndpoint -ApplicationId tapp1 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com -SipAddress sip:endpoint1@litwareinc.com
```

## Detailed Description

A trusted application endpoint is an Active Directory contact object that enables routing of calls to a trusted application. This cmdlet creates a new endpoint contact object in Active Directory Domain Services for a specified application.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ApplicationId_ <br/> |Required  <br/> |System.String  <br/> |The application ID of the trusted application for which the endpoint contact is being created. An application with this ID must already exist. Note that you may include only the name part of the application ID, you don't need to (but you can) include the prefix information. For example, if the application ID is urn:application:TrustedApp1 you only need to pass the string TrustedApp1 to this parameter.  <br/> |
| _TrustedApplicationPoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the trusted application pool associated with the application. The application must already be associated with this pool for the endpoint to be created.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |The display name of the endpoint contact object.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |System.String  <br/> |The telephone number of the contact as it will appear in the Address Book.  <br/> |
| _LineURI_ <br/> |Optional  <br/> |System.String  <br/> |The phone number of the contact. Must be in the format TEL:\<number\>, for example TEL:+14255551212.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns the results of this command. Running this cmdlet will display the newly created object; including this parameter will simply repeat that output, making the use of this parameter redundant.  <br/> |
| _PrimaryLanguage_ <br/> |Optional  <br/> |System.String  <br/> |The primary language used for the trusted application. The language must be configured using a valid language code, such as en-US (U.S. English), fr-FR (French), etc.  <br/> |
| _SecondaryLanguages_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty  <br/> |A collection of languages that can also be used for trusted applications. Values must be configured as a comma-separated values list of language codes. For example, the following syntax sets French Canadian and French as secondary languages: -SecondaryLanguages "fr-CA","fr-FR".  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |A SIP address for the new contact object. If you do not include a value for this parameter a SIP address will be auto-generated in the format sip:RtcApplication-\<GUID\>.\<domain\>, for example sip:RtcApplication-fbf9e2d1-c6aa-45a3-a045-b92d4ef961b2@litwareinc.com. The domain will be the default SIP domain.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new trusted application pool endpoint is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.
  
## See also

#### 

[Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)
  
[Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)
  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)

