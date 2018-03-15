---
title: "Set-CsTrustedApplicationPool"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f42d12b-d09a-41fd-892f-2b7515a35344
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsTrustedApplicationPool
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies a pool that contains the computers that host trusted applications. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsTrustedApplicationPool [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-OutboundOnly <$true | $false>] [-Registrar <String>] [-RequiresReplication <$true | $false>] [-ThrottleAsServer <$true | $false>] [-TreatAsAuthenticated <$true | $false>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example modifies the pool with the FQDN TrustPool.litwareinc.com. We use the Identity parameter to specify the FQDN of the pool we want to modify. This example modifies the OutboundOnly property of the pool by specifying a value of True ($True) for the parameter OutboundOnly. (The default value is False.)
  
```
Set-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com -OutboundOnly $True
```

## Detailed Description
<a name="sectionSection1"> </a>

We recommend that the computers that are running trusted applications within a Lync Server deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. The **Set-CsTrustedApplicationPool** cmdlet modifies the settings for an existing trusted application pool. Note that you can't modify the computers that are associated with a pool by using this cmdlet; you must use the CsTrustedApplicationComputer cmdlets to do that. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsTrustedApplicationPool** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsTrustedApplicationPool"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AppSharingPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of ports available in the port range for application sharing connections.  <br/> |
| _AppSharingPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of the first port in the port range available for application sharing connections.  <br/> |
| _AudioPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of ports available in the port range for audio connections.  <br/> |
| _AudioPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of the first port in the port range available for audio connections.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The fully qualified domain name (FQDN) or service ID of the pool whose settings you want to modify.  <br/> |
| _OutboundOnly_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether a trusted application can initiate a connection to a server within the pool. Set this value to True if you want all connections to be initiated by the server rather than the application.  <br/> |
| _Registrar_ <br/> |Optional  <br/> |System.String  <br/> |The service ID or FQDN of the Registrar service for the pool. Note that changing the Registrar will orphan any contacts attached to the application. Those contacts must be moved by calling the **Move-CsApplicationEndpoint** cmdlet.  <br/> |
| _RequiresReplication_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether replication is required for this pool. Set this value to False if replication is not required. You would ordinarily set this parameter to False for Microsoft Outlook Web Access and manually-provisioned applications.  <br/> |
| _ThrottleAsServer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Set this parameter to false to throttle connections between the servers within the pool and trusted applications as clients. This places greater restrictions on the connections than the default True, which throttles connections as servers. Throttling a connection simply places restrictions on the number of transactions that can occur simultaneously.  <br/> |
| _TreatAsAuthenticated_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether authentication is required for trusted applications connecting to servers within the pool. Set this parameter to False if you want to require trusted applications to be authenticated. The default value of True allows the trusted applications to connect under the assumption they've already been authenticated.  <br/> |
| _VideoPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of ports available in the port range for video connections.  <br/> |
| _VideoPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of the first port in the port range available for video connections.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.Xds.DisplayExternalServer object. Accepts pipelined input of trusted application pool objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.Xds.DisplayExternalServer.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)
  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)
  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)
  
[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)

