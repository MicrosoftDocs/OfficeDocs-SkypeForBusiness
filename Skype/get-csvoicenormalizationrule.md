---
title: Get-CsVoiceNormalizationRule
ms.prod: SKYPEFORBUSINESS
ms.assetid: 59fe1370-1cec-4cf9-8f65-029a7c2454d1
---


# Get-CsVoiceNormalizationRule
[]
Returns information about the voice normalization rules used in your organization. Voice normalization rules convert telephone dialing requirements (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This example retrieves all voice normalization rules defined for the organization.
  
    
    

```

Get-CsVoiceNormalizationRule
```


### EXAMPLE 2

Example 2 retrieves all voice normalization rules specified for all sites. 
  
    
    

```
Get-CsVoiceNormalizationRule -Filter site*
```


### EXAMPLE 3

Example 3 retrieves all voice normalization rules with the letter s anywhere in the scope. For example, this will return all site- and service-level rules, as well as per-user rules with an s in the scope name, such as RedmondEastUsers.
  
    
    

```
Get-CsVoiceNormalizationRule -Filter *s*
```


### EXAMPLE 4

The Filter parameter used in Examples 2 and 3 matches only on the scope portion of the Identity. This example performs a match on the name portion to return all rules with a Name containing the string "seattle". To do this, we first call the **Get-CsVoiceNormalizationRule** cmdlet to retrieve all the normalization rules for the organization. We then pipe this collection to the **Where-Object** cmdlet to find all the items in the collection where the Name property matches the string "seattle".
  
    
    

```
Get-CsVoiceNormalizationRule | Where-Object {$_.Name -match "seattle"}
```


## Detailed Description

This cmdlet returns a named voice normalization rule or a collection of voice normalization rules. These rules are a required part of phone authorization and call routing. They define the requirements for converting--or translating--numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. An understanding of regular expressions is helpful in order to define number patterns that will be translated.
  
    
    
The same rules accessed by this cmdlet can also be accessed through the NormalizationRules property returned by a call to the **Get-CsDialPlan** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Uses wildcard strings to return a collection of normalization rules based on Identity. Note that Filter works only on the scope portion of the Identity, not on the name. For example, the filter value *lob* will return all rules at the global scope (scopes that contain the letters lob), but not a rule with the identity site:Redmond/lobby, where lob is only in the name portion of the identity, not the scope.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the rule. If a value is specified for this parameter, it must be in the format scope/name; for example, site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice normalization rule from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

The **Get-CsVoiceNormalizationRule** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object.
  
    
    

## See also


#### 


  
    
    
 [New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)
  
    
    
 [Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)
  
    
    
 [Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)
  
    
    
 [Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)
  
    
    
 [Get-CsDialPlan](get-csdialplan.md)
