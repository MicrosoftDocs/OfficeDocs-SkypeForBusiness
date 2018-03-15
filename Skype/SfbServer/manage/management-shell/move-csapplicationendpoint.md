---
title: "Move-CsApplicationEndpoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f5a5b7a-aca5-4672-b712-d47683e28caf
description: "Moves an endpoint to a different Registrar pool. This cmdlet was introduced in Lync Server 2010."
---

# Move-CsApplicationEndpoint
 
Moves an endpoint to a different Registrar pool. This cmdlet was introduced in Lync Server 2010.
  
```
Move-CsApplicationEndpoint -Identity <UserIdParameter> -TargetApplicationPool <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example moves the application endpoint contact object with the SIP address endpoint1@litwareinc.com to the trusted Registrar pool TrustPoolA.litwareinc.com. Use this command to upgrade a UCMA 2.0 application to a Skype for Business Server 2015 application after coexistence.
  
```
Move-CsApplicationEndpoint -Identity sip:endpoint1@litwareinc.com -TargetApplicationPool TrustPoolA.litwareinc.com
```

### EXAMPLE 2

This example moves the application endpoint contact object with the SIP address endpoint2@litwareinc.com to the trusted Registrar pool TrustPoolA.litwareinc.com. This example differs from Example 1 in that this command includes the Force parameter. Use this command for an in-place migration of a UCMA 2.0 application or for direct deployment of a UCMA 2.0 application against a pure Skype for Business Server 2015 deployment. This will update an existing object in Active Directory with the necessary attributes so that routing can occur through the Skype for Business Server 2015 Registrar.
  
```
Move-CsApplicationEndpoint -Identity sip:endpoint2@litwareinc.com -TargetApplicationPool TrustPoolA.litwareinc.com -Force
```

## Detailed Description

This cmdlet moves an existing endpoint contact object in Active Directory Domain Services to a Skype for Business Server 2015 application pool. The application associated with the given endpoint must exist on the target pool. To determine which application is associated with the endpoint, run the **Get-CsTrustedApplicationEndpoint** cmdlet.
  
This cmdlet is also used to upgrade the Active Directory contact object properties when an application is retargeted against Skype for Business Server 2015. Note that the source and target application pool will be the same in that case. Also, if an application originally designed to work against Skype for Business Server 2015 is directly deployed against Skype for Business Server 2015, then this cmdlet must be used with the Force flag to upgrade the Active Directory contact object properties.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The SIP address or distinguished name (DN) of the endpoint contact you want to move.  <br/> |
| _TargetApplicationPool_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the pool to which the endpoint is moving. The target pool must have a Registrar service dependency.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |This flag is required if you are moving a Microsoft Unified Communications Managed API (UCMA) 2.0 contact object to the same pool but on a Skype for Business Server 2015 deployment. This will force routing to occur through the Skype for Business Server 2015 Registrar.  <br/> |
| _IgnoreBackendStoreException_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the application endpoint despite those errors.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifying this parameter will return the application endpoint object after the object has been moved.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

String. Accepts a pipelined string value representing the Identity of an application endpoint.
  
## Return Types

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.
  
## See also

#### 

[Get-CsApplicationEndpoint](get-csapplicationendpoint.md)

