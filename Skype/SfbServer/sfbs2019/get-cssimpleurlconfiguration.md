---
title: "Get-CsSimpleUrlConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 59f5528b-d1f4-4da9-9dfe-102c96c6d7c2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsSimpleUrlConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the simple URLs configured for use in your organization. Simple URLs make it easier for users to join meetings and conferences, and also make it easier for Administrators to log on to the Lync Server Control Panel. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsSimpleUrlConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns information about all the simple URL configuration collections currently in use in the organization. This is achieved by calling the **Get-CsSimpleUrlConfiguration** cmdlet without any additional parameters. 
  
```
Get-CsSimpleUrlConfiguration
```

### EXAMPLE 2

In Example 2, information is returned for a single simple URL configuration collection: the configuration with the Identity site:Redmond.
  
```
Get-CsSimpleUrlConfiguration -Identity "site:Redmond"
```

### EXAMPLE 3

Example 3 returns information for all the simple URL configuration collections that have been assigned to the site scope. To do this, the **Get-CsSimpleUrlConfiguration** cmdlet is called along with the Filter parameter; the filter value "site:*" limits the returned data to those collections that have an Identity that begins with the string value "site:". 
  
```
Get-CsSimpleUrlConfiguration -Filter "site:*"
```

### EXAMPLE 4

In Example 4, detailed information is displayed for each simple URL configured for use in the organization. To carry out this task, the command first calls the **Get-CsSimpleUrlConfiguration** cmdlet to return a complete set of simple URL information. This data is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to "expand" the value of the SimpleUrl property. Expanding a property value displays all the data stored in that property in an easy-to-read format. 
  
```
Get-CsSimpleUrlConfiguration | Select-Object -ExpandProperty SimpleUrl
```

### EXAMPLE 5

The command shown in Example 5 returns all the simple URLs for meeting management that are currently in use in your organization. To do this, the command first calls the **Get-CsSimpleUrlConfiguration** cmdlet without any additional parameters; this returns a complete set of simple URL information. This data is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to expand the value of the SimpleUrl property. The filtered collection is then piped to the **Where-Object** cmdlet, which picks out only those simple URLs where the Component property is equal to "Meet". 
  
```
Get-CsSimpleUrlConfiguration | Select-Object -ExpandProperty SimpleUrl | Where-Object {$_.Component -eq "Meet"}
```

## Detailed Description
<a name="sectionSection1"> </a>

In Microsoft Office Communications Server 2007 R2, meetings had URLs similar to this: 
  
https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8&amp;key=EcznhLh5K5t
  
However, such URLs are not especially intuitive, and not easy to convey to someone else. The simple URLs introduced in Lync Server 2010 help overcome those problems by providing users with URLs that look more like this:
  
https://meet.litwareinc.com/kenmyer/071200
  
Simple URLs are an improvement over the URLs used in Office Communications Server. However, simple URLs are not automatically created for you; instead, you must configure the URLs yourself. (You must also create Domain Name System (DNS) records for each URL; configure reverse proxy rules for external access; add the simple URLs to your Front End Server certificates; and so on.)
  
Lync Server enables you to create three different simple URLs:
  
Meet - Used for meetings. You must have at least one Meet URL for each of your SIP domains.
  
Admin - Used to point administrators toward the Lync Server Control Panel.
  
Dialin - Used for the dial-in conferencing webpage.
  
Simple URLs are stored in simple URL configuration collections. When you install Lync Server, a global collection is created for you; you can also create custom collections at the site scope. This gives you the ability to use different simple URLs at each of your sites.
  
The **Get-CsSimpleUrlConfiguration** cmdlet provides a way for you to retrieve information about all the simple URL configuration collections currently in use in your organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsSimpleUrlConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsSimpleUrlConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters to specify the simple URL collection (or collections) to be returned. For example, this syntax returns all the simple URL collections that have been configured at the site scope: -Filter "site:\*".  <br/> Note that you cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of simple URLs to be returned. To return the global collection, use this syntax: -Identity global. To return a collection from the site scope, use syntax similar to this: -Identity "site:Redmond." Note that you cannot use wildcards when specifying an Identity. If you want to use wildcards, use the Filter parameter instead.  <br/> Calling the **Get-CsSimpleUrlConfiguration** cmdlet without any parameters returns all the simple URLs configured for use in your organization.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the simple URL configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account where whose Simple URL configuration settings are to be retrieved. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsSimpleUrlConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SimpleUrl.SimpleUrlConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)
  
[Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)
  
[Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

