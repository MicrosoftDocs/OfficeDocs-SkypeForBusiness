---
title: "Set-CsPresenceProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f2e30d1-edb5-4839-a24f-11b77b699a1d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsPresenceProvider
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies a presence provider configured for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPresenceProvider [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 demonstrate how you can use the **Set-CsPresenceProvider** cmdlet to modify the FQDN of an existing presence provider. To do this, the first command in the example uses the **Get-CsPresenceProvider** cmdlet to create an object reference to the presence provider with the Identity "global/contoso.com". This object reference is stored in the variable $x. 
  
In the second command, the FQDN property of the object reference is set to contoso2.com, the new FQDN for the presence provider. After the FQDN property has been configured, the **Set-CsPresenceProvider** cmdlet is used, along with the Instance property, to write these changes to the global collection of User Services configuration settings. 
  
```
$x = Get-CsPresenceProvider -Identity "global/contoso.com" 
$x.Fqdn = "contoso2.com"
Set-CsPresenceProvider -Instance $x
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **CsPresenceProvider** cmdlets are used to manage the PresenceProviders property found in the User Services configuration settings. Among other things, these settings are used to maintain presence information, including a collection of authorized presence providers. That collection is stored in the PresenceProviders property. 
  
The **Set-CsPresenceProvider** cmdlet can be used to modify the FQDN of a presence provider currently configured for use in the organization. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsPresenceProvider"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsPresenceProvider** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the presence provider to be modified. The Identity of a presence provider is composed of two parts: the scope (Parent) where the rule has been applied (for example, service:UserServer:atl-cs-001.litwareinc.com) and the provider Fqdn. To modify a presence provider at the global scope use syntax similar to this:  <br/> -Identity "global/fabrikam.com"  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsPresenceProvider** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPresenceProvider** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPresenceProvider](get-cspresenceprovider.md)
  
[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
[New-CsPresenceProvider](new-cspresenceprovider.md)
  
[Remove-CsPresenceProvider](remove-cspresenceprovider.md)

