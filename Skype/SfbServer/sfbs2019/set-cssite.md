---
title: "Set-CsSite"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f4165fdb-5828-4e81-b489-7e263b27e36b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsSite
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies the properties for any of your Lync Server sites. Sites represent a collection of Lync Server pools and are typically designed around geographic regions. Lync Server includes two types of sites: data center sites and remote sites (branch office). This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsSite [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-DefaultPersistentChatPool <String>] [-Description <String>] [-DisplayName <String>] [-FederationRoute <String>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]] [-XmppFederationRoute <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 modifies the Description property for the Redmond site (-Identity Redmond).
  
```
Set-CsSite -Identity Redmond -Description "Full-time employees in Redmond, WA."
```

### EXAMPLE 2

Example 2 changes the display name for the Redmond site to "US Headquarters".
  
```
Set-CsSite -Identity Redmond -DisplayName "US Headquarters"
```

### EXAMPLE 3

The command shown in Example 3 locates all the sites that do not have a Description, and then assigns each of those sites the generic description "Litwareinc.com." To do this, the command first calls the **Get-CsSite** cmdlet without any parameters in order to return a collection of all the Lync Server sites. The returned collection is then piped to the **Where-Object** cmdlet, which picks out only those sites where the Description property is equal to (-eq) a null value ($Null). These sites are then piped to the **ForEach-Object** cmdlet. This cmdlet takes each item in the collection and uses the **Set-CsSite** cmdlet to modify the value of the Description property. 
  
```
Get-CsSite | Where-Object {$_.Description -eq $Null} | ForEach-Object {Set-CsSite $_.Identity -Description "Litwareinc.com"}
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server 2010 introduced a new concept to the Lync Server topology: sites. Sites (which should not be confused with Active Directory sites or Microsoft Exchange Server sites) are a collection of Lync Server pools and servers that are typically organized according to geography and network bandwidth. For example, if all your computers in Redmond are located on the same local area network with high-speed, low-latency connections, you might designate a Redmond site that encompasses those computers. If your computers in Dublin are located on their own local area network, and share high-speed, low-latency connections, then you might create a separate Dublin site as well. Sites also play a key role in Lync Server management: many policies and settings can be configured at the site scope, making it easy to do such things as apply one set of dial plans to users in Redmond and a different set of dial plans to users in Dublin.
  
Sites are created by using Topology Builder, and any changes to the site infrastructure (for example, adding new pools) must also be made by using Topology Builder. However, you can use the **Set-CsSite** cmdlet to change the display name, the description, and the federation route of any site in your organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsSite** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsSite"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultPersistentChatPool_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the default Persistent Chat pool for the site.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to add additional information to a site object. For example, the Description might include contact information for the site.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Friendly name for the site. For example: -DisplayName "North America and South America".  <br/> |
| _FederationRoute_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Edge Server used to provide a bridge between your internal network and the Internet. For example: -FederationRoute "EdgeServer:atl-edge-001.litwareinc.com".  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts or non-fatal error messages that might occur when you run the cmdlet.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Name of the site to be modified; for example: -Identity "Redmond". Do not use the format "site:Redmond" when specifying the identity.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _XmppFederationRoute_ <br/> |Optional  <br/> |System.String  <br/> |Service Identity of the Edge Server used for XMPP (Extensible Messaging and Presence Protocol) federation. For example:  <br/> -XmppFederationRoute EdgeServer:atl-xmpp-001.litwareinc.com  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsSite** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsSite** cmdlet does not return any objects or values. Instead, the cmdlet modifies instances of the Microsoft.Rtc.Management.Deploy.Internal.Site+CentralSite object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsSite](get-cssite.md)

