---
title: Set-CcApplianceDirectory
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6da93ddb-ca99-4b5d-9b33-3d70659730b2
---


# Set-CcApplianceDirectory
[]
The Set-CcApplianceDirectory cmdlet sets the working directory on the Skype for Business Cloud Connector Edition host server. All deployment files are stored in this directory.
  
    
    


```

Set-CcApplianceDirectory[[-Path] <string>]
```


## Examples
<a name="Examples"> </a>


### Example 1

The following example sets the working directory on the host server to c:\\cloudconnector\\applianceroot:
  
    
    

```
Set-CcApplianceDirectory -Path "c:\\cloudconnector\\applianceroot"
```


## Parameters
<a name="Examples"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| Path <br/> | Required <br/> |System.String  <br/> | Specifies the path where all deployment files are stored. <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The Set-CcApplianceDirectory cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None
  
    
    

## See also
<a name="ReturnTypes"> </a>

None
  
    
    

