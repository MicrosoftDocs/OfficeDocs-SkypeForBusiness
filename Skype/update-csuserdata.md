---
title: Update-CsUserData
ms.prod: SKYPEFORBUSINESS
ms.assetid: e3cb48e9-9b5e-4c73-ab54-4aea16533ed8
---


# Update-CsUserData
[]
Uses previously-exported user information to update Skype for Business Server 2015 user data. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Update-CsUserData -FileName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-RoutingGroupFilter <String>] [-TargetPoolFqdn <Fqdn>] [-TestMode <SwitchParameter>] [-ThreadCount <Int32>] [-UserFileFilter <String>] [-UserFilter <String>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 updates Skype for Business Server 2015 user data based on information stored in the file C:\\Logs\\ExportedUserData.zip.
  
    
    

```

Update-CsUserData -Filename "C:\\Logs\\ExportedUserData.zip"
```


### Example 2

In Example 2, user data is updated for a single user: the user with the SIP address kenmyer@litwareinc.com. This is done by including the UserFilter parameter followed by the user's SIP address (minus the sip: prefix).
  
    
    

```
Update-CsUserData -Filename "C:\\Logs\\ExportedUserData.zip" -UserFilter "kenmyer@litwareinc.com"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **Update-CsUserData** cmdlet enables administrators to update user data for a specified user or set of users. (Note that this data must have previously been exported by using the [Export-CsUserData](export-csuserdata.md) cmdlet.) This updating is typically done in order to restore lost data to a logged-on user.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Update-CsUserData** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Full path to the .ZIP file or .XML file containing the user data to be updated. For example:  <br/>  `-FileName "C:\\Data\\Lync2010.zip"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the FQDN of the domain controller to be used when running the **Update-CsUserData** cmdlet. If not specified, the cmdlet will use the first available domain controller. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _RoutingGroupFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to update data only for the specified routing groups. Routing groups are used to indicate the Front End server that users register with.  <br/> |
| _TargetPoolFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Registrar pool containing the user accounts to be updated.  <br/> |
| _TestMode_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When included in a command, Update-CsUserData will verify that the data can be updated, but will not actually update that data.  <br/> |
| _ThreadCount_ <br/> |Optional  <br/> |System.Int32  <br/> |Number of threads that can be devoted to the update task.  <br/> |
| _UserFileFilter_ <br/> |Optional  <br/> |System.String  <br/> |Full path to a text file containing a list of user URIs for whom data should be exported.  <br/> |
| _UserFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to update data for a single user. That user specified by using his or her SIP address, minus the sip: prefix. For example:  <br/>  `-UserFilter "kenmyer@litwareinc.com"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Update-CsUserData** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Update-CsUserData** cmdlet updates Skype for Business Server 2015 user information.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Convert-CsUserData](convert-csuserdata.md)
  
    
    
 [Export-CsUserData](export-csuserdata.md)
  
    
    
 [Import-CsUserData](import-csuserdata.md)
  
    
    
 [Sync-CsUserData](sync-csuserdata.md)
