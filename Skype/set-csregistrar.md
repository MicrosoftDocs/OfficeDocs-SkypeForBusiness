---
title: Set-CsRegistrar
ms.prod: SKYPEFORBUSINESS
ms.assetid: e0c31acc-179c-4423-910e-8bd7807e6489
---


# Set-CsRegistrar
[]
Enables you to modify the properties of one or more Registrars. Registrars are used to authenticate logon requests, and to maintain information about user status and availability. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsRegistrar [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingDatabase <String>] [-ArchivingServer <String>] [-BackupRegistrar <String>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-EnableAutomaticFailover <$true | $false>] [-FailbackDetectionInterval <TimeSpan>] [-FailureDetectionInterval <TimeSpan>] [-Force <SwitchParameter>] [-LyssWcfMtlsPort <UInt16>] [-MirrorArchivingDatabase <String>] [-MirrorMonitoringDatabase <String>] [-MonitoringDatabase <String>] [-MonitoringServer <String>] [-Registrar <String>] [-SipHealthPort <UInt16>] [-SipPort <UInt16>] [-SipServerTcpPort <UInt16>] [-UserServer <String>] [-WebPort <UInt16>] [-WebServer <String>] [-WhatIf [<SwitchParameter>]] [-WinFabClientConnectionPort <UInt16>] [-WinFabFederationPort <UInt16>] [-WinFabIPCPort <UInt16>] [-WinFabLeaseAgentPort <UInt16>] [-WinFabReplicationPort <UInt16>] [-XmppGatewaySipPort <UInt16>]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 sets the SIP port for the Registrar Registrar:atl-cs-001.litwareinc.com to 5072.
  
    
    

```

Set-CsRegistrar -Identity "Registrar:atl-cs-001.litwareinc.com" -SipPort 5072
```


### EXAMPLE 2

Example 2 sets the SIP port for all the Registrars in the organization to 5072. To do this, the command first uses the **Get-CsService** cmdlet and the Registrar parameter to return a collection of all the Registrars currently in use. This collection is then piped to the **ForEach-Object** cmdlet, which takes each Registrar in the collection and runs the **Set-CsRegistrar** cmdlet in order to change the SIP port to 5072.
  
    
    

```
Get-CsService -Registrar | ForEach-Object {Set-CsRegistrar -Identity $_.Identity -SipPort 5072}
```


### EXAMPLE 3

Example 3 configures both a backup Registrar (BackupRegistrar) and automatic failover (EnableAutomaticFailover) for the Registrar Registrar:atl-cs-001.litwareinc.com.
  
    
    

```
Set-CsRegistrar -Identity "Registrar:atl-cs-001.litwareinc.com" -BackupRegistrar "Registrar:dublin-cs-001.litwareinc.com" -EnableAutomaticFailover $True
```


## Detailed Description

The Registrar is perhaps the most important component in Skype for Business Server 2015; without a Registrar, users would not be able to log on to the system, and Skype for Business Server 2015 would not be able to keep track of users and their current status. When a user logs on to Skype for Business Server 2015, the endpoint the user is logging on from (be it a computer, a mobile phone, or some other device) sends a REGISTER request to the registration server; in turn the server responds by challenging the client device for authentication credentials. If the client passes the challenge (that is, if the client presents a valid set of credentials), then the user is authenticated and endpoint information such as IP address, port, and user name is logged in the registration database. When a user logs off, this information is then removed from the database. In between log on and log off, the Registrar keeps status information up-to-date and helps to route messages to and from the user.
  
    
    
The **Set-CsRegistrar** cmdlet provides a way for you to modify the properties of one or more Registrars in your organization. These modifications include changing port settings as well as specifying the action that should be taken if a Registrar should become unavailable.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ArchivingDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service Identity of the database used by the Archiving service.  <br/> |
| _ArchivingServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Archiving Server to be associated with the Registrar. For example:  <br/>  `-ArchivingServer "ArchivingServer:atl-cs-001.litwareinc.com"` <br/> |
| _BackupRegistrar_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Registrar to be used if this Registrar is not available. For example:  <br/>  `-BackupRegistrar "Registrar:dublin-cs-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EdgeServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Edge Server to be associated with the Registrar. For example:  <br/>  `-EdgeServer "EdgeServer:atl-edge-001.litwareinc.com"` <br/> |
| _EnableAutomaticFailover_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, the backup Registrar will be employed any time the primary Registrar is unavailable. If False, the backup Registrar will not be used if the primary Registrar is not available.  <br/> This parameter also affects users who have registered with a backup Registrar. If this parameter is set to True, then those users will be dropped from the backup Registrar and re-registered on the primary Registrar if and when that Registrar becomes available.  <br/> |
| _FailbackDetectionInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time that the system will wait before checking to see if a Registrar that had become unavailable is now available. If you have set EnableAutomaticFailover to True, the system will "failover" to the backup Registrar any time a Registrar becomes unavailable. That simply means that the system will take users who are logged-on to the failed Registrar and attempt to log them on to the backup Registrar.  <br/> The FailbackDetectionInterval property specifies the amount of time that the system will wait before checking to see if the original Registrar is available again. If so, Skype for Business Server 2015 will then attempt to "failback" to that Registrar. Failback simply means reverting back to the Registrar initially in use; in other words, logging users back on to their original Registrar.  <br/> Note that failback is an automated process only. You cannot manually failback from one Registrar to another.  <br/> The detection interval can be set to any value between 30 seconds and 84,400 seconds (24 hours); specify the time span using the format hours:minutes:seconds. For example, this sets the interval to 1 hour and 15 minutes:  <br/>  `-FailbackDetectionInterval 01:15:00` <br/> This parameter cannot be used unless you have specified a backup Registrar.  <br/> |
| _FailureDetectionInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the time interval that the system will wait before deciding that a Registrar is unavailable. If EnableAutomaticFailover has been set to True, the system will then attempt to log users on to the backup Registrar instead.  <br/> The detection interval can be set to any value between 30 seconds and 84,400 seconds (24 hours); specify the time span using the format hours:minutes:seconds. For example, this sets the interval to 1 hour and 15 minutes:  <br/>  `-FailureDetectionInterval 01:15:00` <br/> This parameter cannot be used unless you have specified a backup Registrar.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Registrar to be modified. For example:  <br/>  `-Identity "Registrar:atl-cs-001.litwareinc.com"` <br/> Note that you can leave off the prefix "Registrar:" when specifying a Registrar. For example:  <br/>  `-Identity "atl-cs-001.litwareinc.com"` <br/> |
| _LyssWcfMtlsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used by the Lync Storage Service (LYSS). The default value is 5077.  <br/> |
| _MirrorArchivingDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service Identity of the mirror database used by the Archiving service.  <br/> |
| _MirrorMonitoringDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service Identity of the mirror database used by the Monitoring service.  <br/> |
| _MonitoringDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service Identity of the monitoring database associated with the Registrar.  <br/> |
| _MonitoringServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Monitoring Server to be associated with the Registrar. For example:  <br/>  `-MonitoringServer "MonitoringServer:atl-cs-001.litwareinc.com"` <br/> |
| _Registrar_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Registrar.  <br/> |
| _SipHealthPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for monitoring server health.  <br/> |
| _SipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for SIP (Session Initiation Protocol) traffic.  <br/> |
| _SipServerTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP listening port. The default value is 5060.  <br/> |
| _UserServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the User Services server to be associated with the Registrar. For example:  <br/>  `-UserServer "UserServer:atl-cs-001.litwareinc.com"` <br/> |
| _WebPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for communicating with Web servers.  <br/> |
| _WebServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Web Server to be associated with the Registrar. For example:  <br/>  `-WebServer "WebServer:atl-cs-001.litwareinc.com"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _WinFabClientConnectionPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for client connections to Windows Fabric. The default value is 5092.  <br/> |
| _WinFabFederationPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for Windows Fabric federation. Federation refers to the process by which Windows fabric routes messages. The default value is 5090.  <br/> |
| _WinFabIPCPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used by Windows Fabric for inter-process communication (IPC). IPC is a technology that allows for multiple threads in a process to exchange data. The default value is 5093.  <br/> |
| _WinFabLeaseAgentPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used by the Windows Fabric lease agent. Lease agents are used to interact with the kernel level lease driver. The default value is 5091.  <br/> |
| _WinFabReplicationPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for Windows Fabric replication. Skype for Business Server 2015 uses Windows Fabric to replicate conference directories to all the Front End servers within a Registrar pool. The default value is 5094.  <br/> |
| _XmppGatewaySipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used by the XMPP gateway associated with the Registrar. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. An allowed partner is an IM and presence provider whose users are allowed to exchange instant messages and presence information with your Skype for Business Server 2015 users. The default value is 5098.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **Set-CsRegistrar** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **Set-CsRegistrar** cmdlet does not return any objects or values. Instead, the command modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayRegistrar object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsService](get-csservice.md)
