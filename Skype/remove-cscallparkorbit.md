---
title: Remove-CsCallParkOrbit
ms.prod: SKYPEFORBUSINESS
ms.assetid: b8e7c236-f8de-45bd-966b-60c815b37aed
---


# Remove-CsCallParkOrbit
[]
Removes a specific call park orbit range. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsCallParkOrbit -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In this example, the **Remove-CsCallParkOrbit** cmdlet is used to delete the call park orbit range with the name Redmond CPO 1.
  
    
    

```

Remove-CsCallParkOrbit -Identity "Redmond CPO 1"
```


### EXAMPLE 2

The command in this example removes all call park orbit ranges that have been defined for an organization. The command first calls the **Get-CsCallParkOrbit** cmdlet with no parameters to retrieve all the defined call park orbit ranges. It then pipes that collection of call park orbit ranges to the **Remove-CsCallParkOrbit** cmdlet, which removes each call park orbit.
  
    
    

```
Get-CsCallParkOrbit | Remove-CsCallParkOrbit
```


### EXAMPLE 3

This command removes all call park orbit ranges that have an identity that includes the string "Redmond", such as "Redmond 501", "CP Redmond 1", and "ARedmond". The command first calls the **Get-CsCallParkOrbit** cmdlet with the Filter parameter to retrieve all call park orbit ranges that have an Identity with the string Redmond in it. This collection is piped to the **Remove-CsCallParkOrbit** cmdlet, which removes everything in the collection.
  
    
    

```
Get-CsCallParkOrbit -Filter *Redmond* | Remove-CsCallParkOrbit
```


## Detailed Description

The **Remove-CsCallParkOrbit** cmdlet deletes the call park orbit range with the name passed to the Identity parameter (this parameter is required). Each call park orbit within an organization must have a unique range of numbers. Removing a call park orbit frees up the range that was in that call park orbit. The freed numbers can then be used in a newly defined call park orbit.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The name of the call park orbit range. This name was assigned by the administrator when the call park orbit range was defined.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit object. Accepts pipelined input of call park orbit objects.
  
    
    

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit.
  
    
    

## See also


#### 


  
    
    
 [New-CsCallParkOrbit](new-cscallparkorbit.md)
  
    
    
 [Set-CsCallParkOrbit](set-cscallparkorbit.md)
  
    
    
 [Get-CsCallParkOrbit](get-cscallparkorbit.md)
