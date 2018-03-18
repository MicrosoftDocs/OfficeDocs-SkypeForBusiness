---
title: "New-CsConferencingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c4295f94-f525-46ce-93b8-ae9338c9bc4e
description: "Creates a new collection of conference configuration settings. Conference settings determine such things as the maximum-allowed size for conference content and handouts, the content grace period (that is, the amount of time content will be stored before being deleted), and the URLs for the internal and external downloads of the supported client. This cmdlet was introduced in Lync Server 2010."
---

# New-CsConferencingConfiguration
 
Creates a new collection of conference configuration settings. Conference settings determine such things as the maximum-allowed size for conference content and handouts, the content grace period (that is, the amount of time content will be stored before being deleted), and the URLs for the internal and external downloads of the supported client. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsConferencingConfiguration -Identity <XdsIdentity> [-ClientAppSharingPort <UInt16>] [-ClientAppSharingPortRange <UInt32>] [-ClientAudioPort <UInt16>] [-ClientAudioPortRange <UInt32>] [-ClientFileTransferPort <UInt16>] [-ClientFileTransferPortRange <UInt32>] [-ClientMediaPort <UInt16>] [-ClientMediaPortRange <UInt32>] [-ClientMediaPortRangeEnabled <$true | $false>] [-ClientSipDynamicPort <UInt16>] [-ClientSipDynamicPortRange <UInt32>] [-ClientVideoPort <UInt16>] [-ClientVideoPortRange <UInt32>] [-CloudPollServicePrimaryUrl <String>] [-CloudPollServiceSecondaryUrl <String>] [-Confirm [<SwitchParameter>]] [-ConsoleDownloadExternalUrl <String>] [-ConsoleDownloadInternalUrl <String>] [-ContentGracePeriod <TimeSpan>] [-Force <SwitchParameter>] [-HelpdeskExternalUrl <String>] [-HelpdeskInternalUrl <String>] [-InMemory <SwitchParameter>] [-MaxBandwidthPerAppSharingServiceMb <UInt64>] [-MaxContentStorageMb <UInt16>] [-MaxUploadFileSizeMb <UInt16>] [-Organization <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new collection of conferencing configuration settings for the Redmond site (site:Redmond). In this example, one additional parameter is included (Organization) which is used to set the value of the Organization property to Litwareinc. Note that this command will fail if the Redmond site already has a collection of conferencing configuration settings. That's because you can have only one such collection per site.
  
```
New-CsConferencingConfiguration -Identity site:Redmond -Organization Litwareinc
```

### EXAMPLE 2

In Example 2, a new collection of conferencing configuration settings is initially created in memory only; these virtual settings are only later applied to the Redmond site. To do this, the first command in the example uses the **New-CsConferencingConfiguration** cmdlet to create a new, in-memory collection of settings stored in the variable $x; the InMemory parameter specifies that the collection should be created in memory rather than immediately applied to the Redmond site.
  
After the collection has been created, the second command sets the value of the Organization property to Litwareinc. Finally, the third command uses the **Set-CsConferencingConfiguration** cmdlet to actually apply the new settings to the Redmond site. (This command will fail if conferencing configuration settings have already been applied to site:Redmond.) If you do not call the **Set-CsConferencingConfiguration** cmdlet the new settings will never take effect. Instead, they will disappear as soon as you end your Windows PowerShell session or delete the variable $x.
  
```
$x = New-CsConferencingConfiguration -Identity site:Redmond -InMemory
$x.Organization = "Litwareinc"
Set-CsConferencingConfiguration -Instance $x
```

## Detailed Description

For conferences, management and administration is split between two sets of cmdlets. If you want to manage the things users can and cannot do (for example, can users invite anonymous participants to join a conference, are users allowed to offer application sharing in a conference, or are users allowed to transfer files within a conference), then you need to use the **CsConferencingPolicy** cmdlets.
  
Administrators also need to manage the Web Conferencing service. For example, administrators need to be able to do such things as specify the maximum amount of content storage allotted to a single conference and to specify the grace period before that conference content is automatically deleted. They also need to be able to specify the ports used for activities such as application sharing and file transfer.
  
These latter activities can be managed by using the **CsConferencingConfiguration** cmdlets. These cmdlets enable you to manage the actual servers themselves. The **CsConferencingConfiguration** cmdlets (which can be applied to the global, the site, and the service scopes) aren't used to specify whether or not a user can share applications during a conference; if application sharing is allowed, however, these cmdlets enable you to indicate which ports should be used for that activity. Likewise, the cmdlets enable you to specify such things as storage limits and expiration periods, as well as pointers to internal and external URLs where users can obtain conferencing help and resources.
  
When you install Skype for Business Server 2015, the system provides you with a single collection of conferencing configuration settings (the global collection). If you need to create custom settings for a site or service, you can do so using the **New-CsConferencingConfiguration** cmdlet. Note that new settings can be applied only at the site or service scope; you cannot create a new global collection of conferencing configuration settings. In addition, no site or service can host more than one collection of settings. If you try to create new settings for the Redmond site and the Redmond site already hosts a collection of conferencing configuration settings, then your command will fail.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of conferencing configuration settings to be modified. To refer to a collection configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"`. To refer to a collection at the service scope, use syntax like the following:  `-Identity "service:ConferencingServer:atl-cs-001.litwareinc.com"`. Note the Web Conferencing service is the only service that can host these configuration settings.  <br/> |
| _ClientAppSharingPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Represents the starting port number used for application sharing. The ClientAppSharingPort must be a value port number between 1024 and 65535, inclusive. The default value is 5350.  <br/> |
| _ClientAppSharingPortRange_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the total number of ports available for application sharing. (The default value is 40.) To determine the actual ports used for application sharing, use this value and the ClientAppSharingPort value. For example, if ClientAppSharingPort is set to 5350 and ClientAppSharingPortRange is set to 3, then the following 3 ports are available for application sharing: 5350; 5351; 5352.  <br/> |
| _ClientAudioPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Represents the starting port number used for client audio. The ClientAudioPort must be a value port number between 1024 and 65535, inclusive. The default value is 5350.  <br/> |
| _ClientAudioPortRange_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the total number of ports available for client audio. (The default value is 40.) To determine the actual ports used for client audio, use this value and the ClientAudioPort value. For example, if ClientAudioPort is set to 5350 and ClientAudioPortRange is set to 3, then the following 3 ports are available for client audio: 5350; 5351; 5352.  <br/> |
| _ClientFileTransferPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Represents the starting port number used for file transfers. The ClientFileTransferPort must be a value port number between 1024 and 65535, inclusive. The default value is 5350.  <br/> |
| _ClientFileTransferPortRange_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the total number of ports available for file transfers. (The default value is 40.) To determine the actual ports used for file transfers, use this value and the ClientFileTransferPort value. For example, if ClientFileTransferPort is set to 5350 and ClientFileTransferPortRange is set to 3, then the following three ports are available for file transfers: 5350; 5351; 5352.  <br/> |
| _ClientMediaPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Represents the starting port number used for client media. Use this parameter for Microsoft Office Communicator 2007 R2 clients. The ClientMediaPort must be a value port number between 1024 and 65535, inclusive. The default value is 5350.  <br/> |
| _ClientMediaPortRange_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the total number of ports available for client media. (The default value is 40.) Use this parameter for Office Communicator 2007 R2 clients. To determine the actual ports used for client media, use this value and the ClientMediaPort value. For example, if ClientMediaPort is set to 5350 and ClientMediaPortRange is set to 3, then the following three ports are available for client media: 5350; 5351; 5352.  <br/> |
| _ClientMediaPortRangeEnabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, clients will use the specified port range for media traffic. When set to False (the default value) any available port (from port 1024 through port 65535) will be used to accommodate media traffic.  <br/> |
| _ClientSipDynamicPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Represents the starting port number used for SIP traffic. The ClientSipDynamicPort must be a value port number between 1024 and 65535, inclusive. The default value is 7100.  <br/> |
| _ClientSipDynamicPortRange_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the total number of ports available for SIP traffic. (The default value is 3.) To determine the actual ports used for SIP traffic, use this value and the ClientSipDynamicPort value. For example, if ClientSipDynamicPort is set to 7100 and ClientSipDynamicPortRange is set to 3, then the following three ports are available for client media: 7100; 7101; 7102.  <br/> |
| _ClientVideoPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Represents the starting port number used for client video. The ClientVideoPort must be a value port number between 1024 and 65535, inclusive. The default value is 5350.  <br/> |
| _ClientVideoPortRange_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the total number of ports available for client video. (The default value is 40.) To determine the actual ports used for client video, use this value and the ClientVideoPort value. For example, if ClientVideoPort is set to 5350 and ClientVideoPortRange is set to 3, then the following three ports are available for client video: 5350; 5351; 5352.  <br/> |
| _CloudPollServicePrimaryUrl_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not currently used with Skype for Business Server 2015.  <br/> |
| _CloudPollServiceSecondaryUrl_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not currently used with Skype for Business Server 2015.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ConsoleDownloadExternalUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL where external users can download a supported client such as Skype for Business. Note that this setting applies only to legacy clients (such as Microsoft Office Communicator 2007 R2) that are logging on to a Skype for Business Server 2015 pool.  <br/> |
| _ConsoleDownloadInternalUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL where internal users can download a supported client such as Skype for Business. Note that this setting applies only to legacy clients (such as Microsoft Office Communicator 2007 R2) that are logging on to a Skype for Business Server 2015 pool.  <br/> |
| _ContentGracePeriod_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Indicates how long conference content will remain on the server following the end of a meeting. The ContentGracePeriod must be specified using the format Days.Hours:Minutes:Seconds. For example, to set the content grace period to 30 days use this syntax:  `-ContentGracePeriod 30.00:00:00`.  <br/> The content grace period can be set to any value between 30 minutes (00:30:00) and 180 days (180.00:00:00). The default value is 15 days (15.00:00:00).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HelpdeskExternalUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL where external users who click Help during a conference will be directed.  <br/> |
| _HelpdeskInternalUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL where internal users who click Help during a conference will be directed.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _MaxBandwidthPerAppSharingServiceMb_ <br/> |Optional  <br/> |System.UInt64  <br/> |Indicates the maximum amount of bandwidth (in megabytes) set aside for the Application Sharing Conferencing service. MaxBandwidthPerAppSharingServiceMb can be set to any integer value between 50 and 100000, inclusive. The default value is 375 megabytes.  <br/> |
| _MaxContentStorageMb_ <br/> |Optional  <br/> |System.UInt16  <br/> |Maximum amount of file space (in megabytes) allowed for the storage of conference content. MaxContentStorageMb can be set to any integer value between 50 and 1024 (1 gigabyte), inclusive. The default value is 500.  <br/> |
| _MaxUploadFileSizeMb_ <br/> |Optional  <br/> |System.UInt16  <br/> |Maximum total size of the files (including handouts and PowerPoint slides) that can be used in a given conference. This setting is typically used when conference content is being archived in Microsoft Exchange Server: by setting a maximum upload file size you can ensure that the content used in the conference (and thus the content which must be archived) does not exceed the maximum file size configured for Microsoft Exchange. The default value is 500 megabytes.  <br/> |
| _Organization_ <br/> |Optional  <br/> |System.String  <br/> |Name of the organization hosting the conference.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsConferencingConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsConferencingConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings object.
  
## See also

#### 

[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)
  
[Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)
  
[Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

