---
title: "Set-CsFIPSConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 920f58ce-e175-41ac-b681-5ac873091593
description: "Modifies an existing collection of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsFIPSConfiguration
 
Modifies an existing collection of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsFIPSConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

In Example 1, the RequireFIPSCompliantMedia property of the global FIPS configuration settings is set to True ($True).
  
```
Set-CsFIPSConfiguration -Identity "global" -RequireFIPSCompliantMedia $True
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Federal Information Processing Standards (FIPS) are a series of standards and guidelines used by computers engaged in work for the United States government; for example, there are FIPS standards that govern the use of such things as cryptography, encryption, and digital signatures. (See [http://www.itl.nist.gov/fipspubs/by-num.htm](http://www.itl.nist.gov/fipspubs/by-num.md) for more information.) Skype for Business Server 2015 provides an option that enables the software to use only algorithms that meet the FIPS standards. If you need to work with the United States government (or with other entities that follow FIPS) then you can enable FIPS compliance in Skype for Business Server 2015.
  
Keep in mind, however, that, for the on-premises version of Skype for Business Server 2015, you have only a single, global collection of FIPS configuration settings: FIPS compliance can only be enabled or disabled for your entire Skype for Business Server 2015 implementation. You cannot selectively enable or disable FIPS compliance on, say, an individual site or an individual Registrar pool. If you do enable FIPS compliance, you could potentially encounter problems when trying to communicate with organizations that do not fully adhere to the FIPS standards.
  
By default, FIPS compliance is disabled in Skype for Business Server 2015.
  
The **Set-CsFIPSConfiguration** cmdlet is used to enable or disable FIPS compliance.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsFIPSConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the FIPS configuration settings to be modified. Because Skype for Business Server 2015 only supports a single, global collection of FIPS settings, the only collection that can be modified is the global collection:  <br/>  `-Identity global` <br/> If you do not include this parameter the **Set-CsFIPSConfiguration** cmdlet will modify the global collection. <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _RequireFIPSCompliantMedia_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True will Skype for Business Server 2015 only allow media sessions with entities that use FIPS compliant algorithms for authentication and authorization.  <br/> Note that, if you require FIPS compliance, then your users will no longer be able to connect to your system by using a Microsoft Lync Server 2010 A/V Edge server. Instead, you will need to upgrade all your Edge servers to Skype for Business Server 2015.  <br/> The default value is False.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the FIPS configuration settings are being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsFIPSConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsFIPSConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)
  
[New-CsFIPSConfiguration](new-csfipsconfiguration.md)
  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)

