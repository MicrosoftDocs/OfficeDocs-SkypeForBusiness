---
title: "Get-CsHealthMonitoringConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 843876f1-8aa6-4324-a981-8eded4d3b16d
description: "Returns information about the health monitoring configuration settings currently in use in your organization. These settings enable administrators to run quality assurance tests without having to supply user names and passwords for the required test accounts. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsHealthMonitoringConfiguration
 
Returns information about the health monitoring configuration settings currently in use in your organization. These settings enable administrators to run quality assurance tests without having to supply user names and passwords for the required test accounts. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsHealthMonitoringConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns all the health monitoring configuration settings currently in use in your organization.
  
```
Get-CsHealthMonitoringConfiguration
```

### EXAMPLE 2

The command shown in Example 2 returns a single collection of health monitoring configuration settings: the settings that have the Identity atl-cs-001.litwareinc.com.
  
```
Get-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com
```

### EXAMPLE 3

Example 3 returns all the health monitoring configuration settings that have been created for the domain litwareinc.com. To do this, the **Get-CsHealthMonitoringConfiguration** cmdlet is called along with the Filter parameter; the filter value "*.litwareinc.com" ensures that only those settings that have an Identity that ends with the string value ".litwareinc.com" will be returned.
  
```
Get-CsHealthMonitoringConfiguration -Filter *.litwareinc.com
```

### EXAMPLE 4

The command shown in Example 4 returns all the health monitoring configuration settings that include the user with the SIP address sip:kenmyer@litwareinc.com as one of the test users. To carry out this task, the command first calls the **Get-CsHealthMonitoringConfiguration** cmdlet without any additional parameters; this returns a collection of all the health monitoring configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the FirstTestUserSipUri property is equal to "sip:kenmyer@litwareinc.com" or where the SecondTestUserSipUri property is equal to "sip:kenmyer@litwareinc.com". As a result, any collection of settings where Ken Myer's SIP address is used for either the first or the second test user will be returned.
  
```
Get-CsHealthMonitoringConfiguration | Where-Object {$_.FirstTestUserSipUri -eq "sip:kenmyer@litwareinc.com" -or $_.SecondTestUserSipUri -eq " sip:kenmyer@litwareinc.com"}
```

## Detailed Description

Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted "manually" by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
Synthetic transactions can be conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test accounts for each of their Registrar or Director pools. These test accounts are a pair of user accounts that have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) When test accounts have been configured for a pool, administrators can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test. Instead, the synthetic transaction will automatically use the preconfigured test accounts when performing its checks.
  
Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator can run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts). If you decide to conduct a synthetic transaction using actual user accounts you will have to supply the credentials for each user.
  
The **Get-CsHealthMonitoringConfiguration** cmdlet provides a way for you to retrieve information about the health monitoring configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when specifying the health monitoring configuration settings to be retrieved. For example, this syntax returns all the settings configured for the litwareinc.com domain:  `-Filter "*.litwareinc.com"`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the pool where the health monitoring configuration settings have been assigned. For example:  `-Identity atl-cs-001.litwareinc.com`.  <br/> If this parameter is not included, then the **Get-CsHealthMonitoringConfiguration** cmdlet will return information about all the health monitoring configuration settings currently in use. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the health monitoring configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsHealthMonitoringConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsHealthMonitoringConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings object.
  
## See also

#### 

[New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)
  
[Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)
  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

