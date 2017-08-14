---
title: Set-CsClsSearchTerm
ms.prod: SKYPEFORBUSINESS
ms.assetid: 57ccaf25-31ab-4059-8dc4-144f29f3af68
---


# Set-CsClsSearchTerm
[]
Modifies one or more centralized logging search terms. Search terms help define the personally identifiable information available to technical support personnel who are searching the centralized trace logs. Search terms are intended for use with Skype for Business Online.
  
    
    

This cmdlet was introduced in Lync Server 2013. 
```

Set-CsClsSearchTerm [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in sets the Inserts property for the search term "site:Redmond/IP". In this example, a single Insert is configured: ItemURI.
  
    
    

```

Set-CsClsSearchTerm -Identity "site:Redmond/IP" -Inserts "ItemURI"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the  [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
    
    
In Skype for Business Online, administrators can use search terms to mask personally identifiable information from support personnel who are viewing the log files. For example, a user's name, such as Ken Myer, would not appear when viewed using the support console; instead, the name might appear as FIRST1 LAST1. Likewise, the phone number +12065551219 might be displayed as PHONE1.
  
    
    
The **Set-CsClsSearchTerm** cmdlet enables you to modify any of the search terms currently assigned to a collection of centralized logging configuration settings.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsClsSearchTerm** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the search term to be modified. A search term consists of two parts: the scope where the term is configured (that is, the collection of centralized logging configuration settings where the term can be found) and the term name. For example:  <br/>  `-Identity "site:Redmond/CallID"` <br/> You cannot use wildcards when specifying the Identity.  <br/> |
| _Inserts_ <br/> |Optional  <br/> |System.String  <br/> |Specify how personally identifiable information is masked when viewing the log files. For example, the Insert "ItemURI" indicates that user URI information should be masked. As a result, a user URI such as sip:kenmyer@litwareinc.com will appear as a generic URI that hides the user name but preserve the domain name:  <br/> Sip:USER1@litwareinc.com  <br/> Inserts mask such things as user names and computer names; phone numbers; and IP addresses.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Set-CsClsSearchTerm** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SearchTerm#Decorated object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsClsSearchTerm** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SearchTerm#Decorated object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsClsSearchTerm](get-csclssearchterm.md)
