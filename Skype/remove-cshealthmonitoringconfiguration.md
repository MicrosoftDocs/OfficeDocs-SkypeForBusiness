---
title: Remove-CsHealthMonitoringConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 2e401908-2366-4e67-ba5b-68ba7ece166e
---


# Remove-CsHealthMonitoringConfiguration
[]
Removes an existing collection of health monitoring configuration settings. These settings enable administrators to run quality assurance tests without having to supply the user names and passwords for the required test accounts. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsHealthMonitoringConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 deletes the collection of health monitoring configuration settings with the Identity atl-cs-001.litwareinc.com. Because identities must be unique, this command will delete, at most, a single collection of settings.
  
    
    

```

Remove-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com
```


### EXAMPLE 2

Example 2 deletes all the health monitoring configuration settings currently in use. To do this, the command first calls the **Get-CsHealthMonitoringConfiguration** cmdlet without any parameters; this returns a collection of all the health monitoring configuration settings in the organization. This collection is then piped to the **Remove-CsHealthMonitoringConfiguration** cmdlet, which deletes each item in the collection.
  
    
    

```
Get-CsHealthMonitoringConfiguration | Remove-CsHealthMonitoringConfiguration 
```


### EXAMPLE 3

Example 3 deletes all the health monitoring configuration settings that have been created for the domain litwareinc.com. To do this, the **Get-CsHealthMonitoringConfiguration** cmdlet is called along with the Filter parameter; the filter value "*.litwareinc.com" ensures that only those settings that have an Identity that ends with the string value ".litwareinc.com" will be returned. The filtered collection is then piped to the **Remove-CsHealthMonitoringConfiguration** cmdlet, which deletes each item in the collection.
  
    
    

```
Get-CsHealthMonitoringConfiguration -Filter *.litwareinc.com  | Remove-CsHealthMonitoringConfiguration 
```


### EXAMPLE 4

The command shown in Example 4 deletes all the health monitoring configuration settings that include the user with the SIP address sip:kenmyer@litwareinc.com as one of the test users. To perform this task, the command starts off by calling the **Get-CsHealthMonitoringConfiguration** cmdlet without any parameters; this returns a collection of all the health monitoring configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the FirstTestUserSipUri property is equal to "sip:kenmyer@litwareinc.com" or where the SecondTestUserSipUri property is equal to "sip:kenmyer@litwareinc.com". In turn, those settings are piped to, and removed by, the **Remove-CsHealthMonitoringConfiguration** cmdlet.
  
    
    

```
(Get-CsHealthMonitoringConfiguration | Where-Object {$_.FirstTestUserSipUri -eq "sip:kenmyer@litwareinc.com" -or $_.SecondTestUserSipUri -eq " sip:kenmyer@litwareinc.com"}) | Remove-CsHealthMonitoringConfiguration
```


## Detailed Description

Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
    
    
Synthetic transactions can be conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test accounts for each of their Registrar pools. These test accounts are a pair of user accounts that have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) When these test accounts are configured for a pool, administrators can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test. Instead, the synthetic transaction will automatically use the preconfigured test accounts when performing its checks.
  
    
    
Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator can run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts). If you decide to conduct a synthetic transaction using actual user accounts you will have to supply the credentials for each user.
  
    
    
The **Remove-CsHealthMonitoringConfiguration** cmdlet provides a way for you to remove any of the health monitoring configuration settings that have been configured for use in your organization.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the pool hosting the health monitoring configuration settings that are to be deleted. For example:  `-Identity atl-cs-001.litwareinc.com`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings object. The **Remove-CsHealthMonitoringConfiguration** cmdlet accepts pipelined instances of the health monitoring configuration object.
  
    
    

## Return Types

None. Instead, the **Remove-CsHealthMonitoringConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)
  
    
    
 [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)
  
    
    
 [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)
