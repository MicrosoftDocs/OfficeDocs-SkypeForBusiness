---
title: "Get-CsTrustedApplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e6623931-3bac-4146-92a9-4465396e9fe6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsTrustedApplication
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves the settings for a trusted application. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTrustedApplication [-ApplicationId <String>] [-TrustedApplicationPoolFqdn <String>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves information about all trusted applications defined within the Lync Server deployment.
  
```
Get-CsTrustedApplication
```

### EXAMPLE 2

Example 2 retrieves the trusted application with the Identity TrustPool.litwareinc.com/urn:application:tapp2. Notice that we were able to omit the urn:application: prefix. The **Get-CsTrustedApplication** cmdlet adds the prefix automatically and retrieves the correct application. 
  
```
Get-CsTrustedApplication -Identity TrustPool.litwareinc.com/tapp2
```

### EXAMPLE 3

Example 3 retrieves all trusted applications that have identities matching the wildcard string specified as the Filter value. In this case, with a Filter value of \*trust\*, the command will retrieve all trusted applications with the string "trust" anywhere within the Identity. This string can be contained within any part of the Identity, the pool FQDN, or the application ID. So this command will retrieve trusted applications with identities such as TrustedPool.litwareinc.com/urn:application:application1, Pool1.litwareinc.com/urn:application:trustedapp, and Pool1.litwareinc.com/urn:application:trust.
  
```
Get-CsTrustedApplication -Filter *trust*
```

### EXAMPLE 4

Example 4 will return the same results as Example 2 (where the Identity was specified as the only parameter). The only difference between the two examples is that Example 2 retrieves the trusted application based on the Identity, which consists of the trusted pool FQDN followed by the application ID. In this example, the application ID and trusted pool FQDN are entered as values to two separate parameters: ApplicationId and TrustedApplicationPoolFqdn.
  
```
Get-CsTrustedApplication -ApplicationId tapp2 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com
```

### EXAMPLE 5

Example 5 retrieves all the trusted applications on the pool TrustPool.litwareinc.com. The example begins by calling the **Get-CsTrustedApplication** cmdlet. This returns a collection of all trusted applications defined within the Lync Server deployment. This collection is then piped to the **Where-Object** cmdlet, which looks through the collection item-by-item to find those with a TrustedApplicationPoolFqdn property value equal to (-eq) TrustPool.litwareinc.com. 
  
```
Get-CsTrustedApplication | Where-Object {$_.TrustedApplicationPoolFqdn -eq "TrustPool.litwareinc.com"}
```

## Detailed Description
<a name="sectionSection1"> </a>

A trusted application is an application developed by a third party that is given trusted status to run as part of Lync Server but that is not a built-in part of the product. This cmdlet enables you to retrieve port and Globally Routable User Agent URI (GRUU) settings for one or more trusted applications.
  
When you use this cmdlet to retrieve a single trusted application, you must supply a value for the Identity parameter. The Identity is the fully qualified domain name (FQDN) of the pool on which the application is homed followed by a slash (/) followed by the application ID. For example, TrustPool.litwareinc.com/tapp2, where TrustPool.litwareinc.com is the pool FQDN and tapp2 is the application ID. Note that when you retrieve an application by calling this cmdlet, you'll see an ID that looks more like this: TrustPool.litwareinc.com/urn:application:tapp2. Notice the prefix urn:application: before the application name (tapp2). While this prefix is part of the Identity, it's not required when you specify the value for the Identity parameter.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsTrustedApplication** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsTrustedApplication\b"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ApplicationId_ <br/> |Optional  <br/> |System.String  <br/> |The name of the application. This can include the application ID prefix, but doesn't need to. For example, ApplicationId values of urn:application:tapp1 and tapp1 will both return the same application. If you supply a value for ApplicationId, you cannot supply a value for the Identity, but you must supply a value for the TrustedApplicationPoolFqdn parameter.  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string that includes wildcards that enables you to retrieve trusted applications based on Identity values that match the given wildcard string. Identities consist of a trusted application pool FQDN followed by a slash (/) followed by the trusted application ID. The Filter value will match any part of the Identity, both the FQDN and the application ID.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.ExternalApplicationIdentity  <br/> |The unique identifier of the trusted application you want to retrieve. Identity values must be entered in the format \<pool FQDN\>/\<application ID\>, where pool FQDN is the FQDN of the pool on which the application resides, and application ID is the name of the application. Note that if you specify an Identity, you cannot specify an ApplicationID or a TrustedApplicationPoolFqdn.  <br/> |
| _TrustedApplicationPoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |The FQDN of the trusted application pool on which the application will reside. If you supply a value for TrustedApplicationPoolFqdn, you cannot supply a value for the Identity, but you must supply a value for the ApplicationID parameter.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns an object of type Microsoft.Rtc.Management.Xds.DisplayTrustedApplication.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrustedApplication](new-cstrustedapplication.md)
  
[Remove-CsTrustedApplication](remove-cstrustedapplication.md)
  
[Set-CsTrustedApplication](set-cstrustedapplication.md)

