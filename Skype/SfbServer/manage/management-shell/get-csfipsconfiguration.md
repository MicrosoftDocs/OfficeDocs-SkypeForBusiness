---
title: "Get-CsFIPSConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 56d29011-187f-4034-a5ed-71625087bf36
description: "Returns information about the Federal Information Processing Standards (FIPS) configuration settings currently in use in the organization. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsFIPSConfiguration
 
Returns information about the Federal Information Processing Standards (FIPS) configuration settings currently in use in the organization. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsFIPSConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information for all the FIPS configuration settings currently in use in the organization. Note that there is only a single, global instance of FIPS configuration settings.
  
```
Get-CsFIPSConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Federal Information Processing Standards (FIPS) are a series of standards and guidelines used by computers engaged in work for the US government; for example, there are FIPS standards that govern the use of such things as cryptography, encryption, and digital signatures. (See [http://www.itl.nist.gov/fipspubs/by-num.htm](http://www.itl.nist.gov/fipspubs/by-num.md) for more information.) Skype for Business Server 2015 provides an option that enables the software to use only algorithms that meet the FIPS standards. If you need to work with the United States government (or with other entities that follow FIPS) then you can enable FIPS compliance in Skype for Business Server 2015.
  
Keep in mind, however, that, for the on-premises version of Skype for Business Server 2015, you have only a single, global collection of FIPS configuration settings: FIPS compliance can only be enabled or disabled for your entire Skype for Business Server 2015 implementation. You cannot selectively enable or disable FIPS compliance on, say, an individual site or an individual Registrar pool. If you do enable FIPS compliance, you could potentially encounter problems when trying to communicate with organizations that do not fully adhere to the FIPS standards.
  
By default, FIPS compliance is disabled in Skype for Business Server 2015.
  
 **Skype for Business Server Control Panel:** The functions carried out by the Get-CsFIPSConfiguration cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values when referencing a collection of FIPS configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:  <br/>  `-Filter "g*"` <br/> That syntax brings back all the FIPS configuration settings that have an Identity that begins with the letter "g".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the FIPS configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Get-CsFIPSConfiguration** cmdlet. If you prefer, however, you can use the following syntax to reference the global settings: <br/>  `-Identity global` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the FIPS configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose FIPS configuration settings are to be retrieved.  <br/> For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsFIPSConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsFIPSConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsFIPSConfiguration](new-csfipsconfiguration.md)
  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)
  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

