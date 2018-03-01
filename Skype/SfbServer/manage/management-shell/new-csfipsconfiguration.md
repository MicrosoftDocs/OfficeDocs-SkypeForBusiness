---
title: "New-CsFIPSConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9ce030fb-fb6b-47a2-9fb9-69e8369b43be
description: "Creates a new collection of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013."
---

# New-CsFIPSConfiguration
 
Creates a new collection of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsFIPSConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-RequireFIPSCompliantMedia <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 create a new, in-memory-only set of FIPS configuration settings and then later use these settings to update the global collection of FIPS configuration settings. In order to do this, the first command in the example uses the **New-CsFIPSConfiguration** cmdlet and the InMemory parameter to create a new collection of FIPS configurations settings with the Identity "global"; the resulting settings object is stored in a variable named $x.
  
In the second command, the **Set-CsFIPSConfiguration** cmdlet and the Instance parameter are then used to replace the existing global collection of FIPS settings with the new collection stored in $x.
  
Although this example works, it is easier to modify FIPS configuration settings by using the **Set-CsFIPSConfiguration** cmdlet.
  
```
$x = New-CsFIPSConfiguration -Identity "global" -RequireFIPSCompliantMedia $False -InMemory

Set-CsFIPSConfiguration -Instance $x
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Federal Information Processing Standards (FIPS) are a series of standards and guidelines used by computers engaged in work for the United States government; for example, there are FIPS standards that govern the use of such things as cryptography, encryption, and digital signatures. (See [http://www.itl.nist.gov/fipspubs/by-num.htm](http://www.itl.nist.gov/fipspubs/by-num.md) for more information.) Skype for Business Server 2015 provides an option that enables the software to use only algorithms that meet the FIPS standards. If you need to work with the United States government (or with other entities that follow FIPS) then you can enable FIPS compliance in Skype for Business Server 2015.
  
Keep in mind, however, that, for the on-premises version of Skype for Business Server 2015, you have only a single, global collection of FIPS configuration settings: FIPS compliance can only be enabled or disabled for your entire Skype for Business Server 2015 implementation. You cannot selectively enable or disable FIPS compliance on, say, an individual site or an individual Registrar pool. If you do enable FIPS compliance, you could potentially encounter problems when trying to communicate with organizations that do not fully adhere to the FIPS standards. That means that the **New-CsFIPSConfiguration** cmdlet is primarily used to manage FIPS compliance for Skype for Business Online.
  
By default, FIPS compliance is disabled in Skype for Business Server 2015.
  
 **Skype for Business Server Control Panel:** The functions carried out by the New-CsFIPSConfiguration cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new collection of FIPS configuration settings. Because Skype for Business Server 2015 only supports a single, global collection of FIPS settings, the only way you can use this parameter is to create a "new" global collection that exists only in memory. You will also need to use the InMemory parameter in order to do that.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _RequireFIPSCompliantMedia_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Skype for Business Server 2015 will only allow media sessions with entities that use FIPS compliant algorithms for authentication and authorization.  <br/> Note that, if you require FIPS compliance, then your users will no longer be able to connect to your system by using a Microsoft Lync Server 2010 A/V Edge server. Instead, you will need to upgrade all your Edge servers to Skype for Business Server 2015.  <br/> The default value is False.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new FIPS configuration settings are being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsFIPSConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsFIPSConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)
  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)
  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

