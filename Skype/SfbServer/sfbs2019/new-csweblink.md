---
title: "New-CsWebLink"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f5c19896-4ce0-42cd-a934-30b1cdc64e3a
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsWebLink
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new web link that points to the Autodiscover service. The Autodiscover service provides a way for client applications such as Lync Web App or Lync Mobile to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
New-CsWebLink -Href <String> -Token <String>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The commands shown in Example 1 add a new Autodiscover URL (http://LyncDiscover.fabrikam.com) to the Autodiscover configuration settings assigned to the Redmond site. To do this, the first command in the example uses the **New-CsWebLink** cmdlet to create a new Autodiscover URL; that URL is stored in a variable named $Link1. After that, the **Set-CsAutoDiscoverConfiguration** cmdlet is used to add the new URL to any URLs already assigned to these settings. This is done by using the WebLinks parameter and the parameter value @{Add=$Link1}. 
  
```
$Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"
Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1}
```

### EXAMPLE 2

The commands in Example 2 assign a pair of Autodiscover URLs (http://LyncDiscover.fabrikam.com and http://LyncDiscoverInternal.fabrikam.com) to the Autodiscover configuration settings assigned to the Redmond site.. In order to carry out this task, the first two commands use the **New-CsWebLink** cmdlet to create the two Autodiscover URLs; the newly-created URLs are then stored in variables named $Link1 and $Link2. After the two URLs are created, the third command uses the **Set-CsAutoDiscoverConfiguration** cmdlet to assign the two URLs to the Redmond site. To do this, the WebLinks parameter is included along with the parameter value @{Add=$Link1,$Link2}. That syntax causes the values stored in the variables $Link1 and $Link2 to be added to the settings' WebLinks property. 
  
```
$Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"
$Link2 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscoverInternal.fabrikam.com"
Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1,$Link2}
```

## Detailed Description
<a name="sectionSection1"> </a>

For client applications to make the most effective use of Lync Server those applications need to know the location of key Lync Server components. For example, authenticated users must be able to locate their home pool; after all, they can only be authenticated by that home pool. Likewise, unauthenticated users must be able to do such things as locate the URL used for joining a conference.
  
If all your users logged on from behind the organization's firewall discovering these locations would be a relatively simple task. However, this relatively simple task gets more and more complicated as users access the system from external locations using Lync Mobile or Lync Web App.
  
This is especially true in split-domain scenarios, scenarios in which some of an organization's users have accounts on the on-premises version of Lync Server while other users have accounts on Microsoft Office 365. In cases such as this, user accounts might be located in different Active Directory forests. That can pose a problem: for example, if a US-based user logs on from Europe the system must be able to recognize his or her forest and then refer the logon request to the proper pool.
  
The Autodiscover service was introduced in the November 2011 release of Lync Server in order to address these issues. When a client application attempts to access Lync Server, the Autodiscover service parses the client SIP address and then redirects that request to the appropriate pool. Client applications connect to the Autodiscover service by sending an HTTP request to an Autodiscover URL; these URLs must be configured by administrators in order for the Autodiscover service to work. (Note that, in addition to configuring URLs, administrators must also create DNS records that correspond to these URLs.)
  
Autodiscover URLs are assigned to Autodiscover configuration settings; in turn, these settings can be applied to the global scope or to the site scope. When you install Lync Server a global collection of settings will be created for you. (However, no Autodiscover URLs will be assigned to that collection.) If a single collection of Autodiscover settings will not fill your needs, then you can use the **New-CsAutoDiscoverConfiguration** cmdlet to create additional configuration settings at the site scope. 
  
Managing Autodiscover configuration settings typically means adding Autodiscover URLs. These URLs must be created using the **New-CsWebLink** cmdlet, with the resulting URL stored in a variable and then added to a collection of Autodiscover configuration settings. Autodiscover URLs are based on the SIP domains used in your organization; administrators will typically create one URL for use by users outside the organization's firewall (for example, http://LyncDiscover.litwareinc.com) and a second URL (for example, http://LyncDiscoverInternal.litwareinc.com) for use by users inside the firewall. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsWebLink** cmdlet locally: RTCUniversalServerAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Href_ <br/> |Required  <br/> |System.String  <br/> |URL for the Autodiscover service, For example:  <br/> -Href "http://LyncDiscover.fabrikam.com"  <br/> |
| _Token_ <br/> |Required  <br/> |System.String  <br/> |Unique name to be given to the URL. For example:  <br/> -Token "Fabrikam"  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsWebLink** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

Creates new instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.WebLink.WebLink object
  

