---
title: "Set-CsRegistrarConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9616b967-09dd-470d-8d0a-acce1ff4fbf9

description: "Modifies the property values in an existing collection of Registrar configuration settings. Registrars are used to authenticate logon requests and to maintain information about user status and availability. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsRegistrarConfiguration
 
Modifies the property values in an existing collection of Registrar configuration settings. Registrars are used to authenticate logon requests and to maintain information about user status and availability. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsRegistrarConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 modifies the Registrar configuration settings applied to the Redmond site (-Identity site:Redmond). In this example, the value of the EnableDHCPServer property is set to True.
  
```
Set-CsRegistrarConfiguration -Identity site:Redmond -EnableDHCPServer $True
```

### EXAMPLE 2

In Example 2, any Registrar configuration settings that allow users more than 8 endpoints are modified. To accomplish this, the command first calls the **Get-CsRegistrarConfiguration** cmdlet without any parameters; this returns a collection of all the Registrar configuration settings used in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the MaxEndpointsPerUser property is greater than (-gt) 8. Finally, the filtered collection is piped to the **Set-CsRegistrarConfiguration** cmdlet, which sets the maximum number of endpoints for each item in that collection to 8.
  
```
Get-CsRegistrarConfiguration | Where-Object {$_.MaxEndpointsPerUser -gt 8} | Set-CsRegistrarConfiguration -MaxEndpointsPerUser 8
```

### EXAMPLE 3

The command shown in Example 3 disables client registration via DHCP for each site in the organization that hosts a collection of Registrar configuration settings. To do this, the command calls the **Get-CsRegistrarConfiguration** cmdlet along with the Filter parameter; the parameter value "site:*" limits the returned data to settings that have been configured at the site scope. This collection is then piped to the **Set-CsRegistrarConfiguration** cmdlet, which uses the EnableDHCPServer parameter and the parameter value $False to prevent clients from using a DHCP server to locate a Registrar.
  
```
Get-CsRegistrarConfiguration -Filter "site:*"| Set-CsRegistrarConfiguration -EnableDHCPServer $False
```

## Detailed Description

The Registrar is perhaps the most important component in Skype for Business Server 2015; after all, without a Registrar, users would not be able to log on to the system, and Skype for Business Server 2015 would not be able to keep track of users and their current status. When a user logs on to Skype for Business Server 2015, the endpoint the user is logging on from sends a REGISTER request to the Registrar; in turn, the server responds by challenging the client device for authentication credentials. If the client passes the challenge (that is, if the client presents a valid set of credentials), then the user is authenticated and endpoint information such as IP address, port, and user name is logged in the registration database. When a user logs off, this information is then removed from the database. In between log on and log off, the Registrar keeps status information up-to-date and helps to route messages to and from the user.
  
Registrar configuration settings are used to help manage endpoints and endpoint subscriptions; these settings can be applied at the global, site, or service scope. (Service scoped-settings are only used with the Registrar service.) The **Set-CsRegistrarConfiguration** cmdlet can be used to modify any (or all) of the Registrar configuration collections currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BackupStoreUnavailableThreshold_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time the system will wait before determining that the backup store is unavailable; at that point, users will be placed in survivability mode. The default value is 30 minutes (00:30:00).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultEndpointExpiration_ <br/> |Optional  <br/> |System.Int32  <br/> |When endpoints log on they have the option of requesting an expiration timeout; this specifies the time interval that an endpoint can remain logged onto the system before it must contact the server and request an extension. The DefaultEndpointExpiration property represents the expiration timeout interval for clients that do not request a specific timeout value.  <br/> The DefaultEndpointExpiration must be between 300 (5 minutes) and 900 (15 minutes). The default value is 600 (10 minutes).  <br/> |
| _EnableDHCPServer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether endpoints can use DHCP servers to locate a Registrar. If True, clients will send a DHCP Inform message when they first start; the DHCP server will respond by sending the fully qualified domain name (FQDN) of a Registrar that can be used to log on the user.  <br/> |
| _EnableWinFabLogUpload_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> Setting this parameter to $false will disable the upload of WinFabDumpFiles and WinFabTraceFiles on the configured file share.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Registrar configuration settings to be modified. To modify the global settings, use this syntax:  <br/>  `-Identity global` <br/> To modify settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To modify settings at the service level, use syntax like this:  <br/>  `-Identity service:Registrar:atl-cs-001.litwareinc.com` <br/> Note that Registrar settings can only be applied to the Registrar service. An error message will occur if you try to apply these settings to any other service.  <br/> |
| _Instance_ <br/> |Optional  <br/> |RegistrarSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MaxEndpointExpiration_ <br/> |Optional  <br/> |System.Int32  <br/> |When endpoints log on they have the option of requesting an expiration timeout; this specifies the time interval that an endpoint can remain logged onto the system before it must contact the server and request an extension. The MaxEndpointExpiration property represents the maximum amount of time that clients can be granted. For example, if the maximum time is set to 600 seconds and a client requests a timeout interval of 800 seconds, the client will be given the maximum allowed expiration period: 600 seconds.  <br/> The MaxEndpointExpiration must be between 300 (5 minutes) and 900 (15 minutes). The default value is 900.  <br/> |
| _MaxEndpointsPerUser_ <br/> |Optional  <br/> |System.UInt16  <br/> |Indicates the maximum number of endpoints a user can simultaneously have connected to the system. For example, a user who is logged on to Skype for Business Server 2015 with both a computer and a mobile phone would be using two endpoints. MaxEndPointsPerUser must be set to a value between 1 and 64, inclusive. The default value is 8.  <br/> Although it is possible to allow a user as many as 64 endpoints, it is recommended that the maximum number of endpoints not exceed 8. Values of 9 or more are used for backwards compatibility and, in rare cases, when suggested by Microsoft support personnel. For new deployments, the maximum number of endpoints should be no more than 8.  <br/> Note, too, that the maximum number of endpoints is intended to give individual users multiple points of presence. As such, this setting is designed for individual users and not for groups of users (such as an entire department.)  <br/> |
| _MaxUserCount_ <br/> |Optional  <br/> |System.UInt64  <br/> |Indicates the maximum number of users that can simultaneously be logged on to a Registrar. MaxUserCount can be set to any integer value between 2000 and 100000, inclusive. The default value is 7500.  <br/> |
| _MinEndpointExpiration_ <br/> |Optional  <br/> |System.Int32  <br/> |When endpoints log on they have the option of requesting an expiration timeout; this specifies the time interval that an endpoint can remain logged onto the system before it must contact the server and request an extension. The MinEndpointExpiration property represents the minimum amount of time that clients can be granted. For example, if the minimum time is set to 600 seconds and a client requests a timeout interval of 200 seconds, the client will be given the minimum allowed expiration period: 600 seconds.  <br/> The MinEndpointExpiration must be between 300 (5 minutes) and 900 (15 minutes). The default value is 300.  <br/> |
| _PoolState_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.PoolState  <br/> |Current state for the Registrar pool. Allowed values are:  <br/> \* Active  <br/> \* FailedOver  <br/> \* FailingOver  <br/> \* FailedBack  <br/> The default value is Active.  <br/> |
| _UserCertificateReplicationThreshold_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> The minimum interval in minutes for user certificates to be replicated. The default is 0.  <br/> > [!CAUTION]> Do not change unless directed to by Microsoft Support.           |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _WinFabMaxLogsSizeMb_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> Limits the amount of locally stored data in C:\ProgramData\Windows Fabric.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ReplicateUserCertsToBackend_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings object. The **Set-CsRegistrarConfiguration** cmdlet accepts pipelined instances of the Registrar settings object.
  
## Return Types

The **Set-CsRegistrarConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings object.
  
## See also

#### 

[Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)
  
[New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)
  
[Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)

