---
title: Sync-CsUserData
ms.prod: SKYPEFORBUSINESS
ms.assetid: c385041f-f3f7-4db0-9ca7-b5f20a5d81d5
---


# Sync-CsUserData
[]
Synchronizes user data between a pair of Skype for Business Server 2015 pools. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Sync-CsUserData -PoolFqdn <Fqdn> [-LocalStore <SwitchParameter>] [-RoutingGroup <String>] [-Target <SwitchParameter>]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 syncs the pool atl-cs-001.litwareinc.com with its designated backup pool.
  
    
    

```

Sync-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **Sync-CsUserData** cmdlet synchronizes user data between a Registrar pool and its assigned backup pool. Note that any call to this cmdlet will fail if the backup service has not been activated the pool in question.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Sync-CsUserData** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the primary Skype for Business Server 2015 pool. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the user data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _RoutingGroup_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to synchronize data only for the specified routing groups. Routing groups are used to indicate the Front End server that users register with.  <br/> |
| _Target_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Synchronizes data with the preassigned backup pool.  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Sync-CsUserData** cmdlet does not accept pipelined output.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Convert-CsUserData](convert-csuserdata.md)
  
    
    
 [Export-CsUserData](export-csuserdata.md)
  
    
    
 [Import-CsUserData](import-csuserdata.md)
  
    
    
 [Update-CsUserData](update-csuserdata.md)
