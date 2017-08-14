---
title: Get-CsImConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: e8f01c91-94aa-4ec2-8861-1a7824c33c8c
---


# Get-CsImConfiguration
[]
Use the **Get-CsImConfiguration** cmdlet to retrieve information about Instant Messaging (IM) configurations.
  
    
    


```

Get-CsImConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example returns information for the Global IM configuration.
  
    
    

```

Get-CsImConfiguration
```


## Detailed Description
<a name="DetailedDescription"> </a>

Use the **Get-CsImConfiguration** cmdlet to retrieve information about Instant Messaging (IM) configurations.
  
    
    
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    



```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection of items. For instance the following usage specifies all the site scoped IM configurations:  `-Filter "site:*"`.  _Filter_ and and _Filter_ and _Identity_ are mutually exclusive. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the unique identity of the IM configuration to be retrieved.  <br/> To retrieve the global IM configuration you can either omit  _Identity_, or use the following syntax: `-Identity Global` <br/> To retrieve an IM configuration at the site scope, use the prefix "site:" followed by the site name. For example: `-Identity "site:Redmond"` <br/> To retrieve an IM configuration at the service scope, use the prefix "service:" followed by the service name. For example: `-Identity "service:Registrar Contoso.RegistrarPool.com"` <br/>  _Identity_ and _Filter_ are mutually exclusive. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Presence of this switch causes the cmdlet to retrieve information from the local replica of the Central Management store, rather than from Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Specifies the globally unique identifier (GUID) of the Skype for Business Online tenant account on which the cmdlet will operate. For example: `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"`. You can return the tenant ID for each of your Skype for Business Online tenants by running this command: `Get-CsTenant | Select-Object DisplayName, TenantID`.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

