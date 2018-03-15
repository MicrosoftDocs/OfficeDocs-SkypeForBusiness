---
title: "Remove-CsFIPSConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b7e43419-0154-4fed-bfc6-9053335ce5d8
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsFIPSConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Removes one or more collections of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsFIPSConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 resets the properties in the global collection of FIPS configuration settings to their default values.
  
```
Remove-CsFIPSConfiguration -Identity "Global"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Federal Information Processing Standards (FIPS) are a series of standards and guidelines used by computers engaged in work for the United States government; for example, there are FIPS standards that govern the use of such things as cryptography, encryption, and digital signatures. (See [http://www.itl.nist.gov/fipspubs/by-num.htm](http://www.itl.nist.gov/fipspubs/by-num.md) for more information.) Lync Server 2013 provides an option that enables the software to use only algorithms that meet the FIPS standards. If you need to work with the United States government (or with other entities that follow FIPS) then you can enable FIPS compliance in Lync Server 2013. 
  
Keep in mind, however, that, for the on-premises version of Lync Server, you have only a single, global collection of FIPS configuration settings: FIPS compliance can only be enabled or disabled for your entire Lync Server implementation. You cannot selectively enable or disable FIPS compliance on, say, an individual site or an individual Registrar pool. If you do enable FIPS compliance, you could potentially encounter problems when trying to communicate with organizations that do not fully adhere to the FIPS standards.
  
By default, FIPS compliance is disabled in Lync Server 2013.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsFIPSConfiguration
  
 **Lync Server Control Panel:** The functions carried out by the Remove-CsFIPSConfiguration cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the FIPS configuration settings to be removed. Because Lync Server 2013 only supports a single, global collection of FIPS settings, the only collection that can be deleted is the global collection:  <br/> -Identity global  <br/> Note that, in this case, the global collection will not actually be removed from the system; Lync Server 2013 does not support the deletion of the global settings. Instead, the lone property in that collection - RequireFIPSCompliantMedia - will be reset to its default value of False.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the FIPS configuration settings being deleted. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsFIPSConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsFIPSConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)
  
[New-CsFIPSConfiguration](new-csfipsconfiguration.md)
  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

