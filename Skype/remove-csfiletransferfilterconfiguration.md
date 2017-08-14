---
title: Remove-CsFileTransferFilterConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: faae4d4b-ea8b-4d50-9c46-16a075476642
---


# Remove-CsFileTransferFilterConfiguration
[]
Removes the specified instant message file transfer filter configuration. (Instant message file transfer filter settings are used to block a user's ability to transfer certain types of files within an instant message.) This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsFileTransferFilterConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the **Remove-CsFileTransferFilterConfiguration** cmdlet is used to remove the file transfer filter configuration that has the Identity site:Redmond.
  
    
    

```

Remove-CsFileTransferFilterConfiguration -Identity site:Redmond
```


### EXAMPLE 2

In Example 2, all the file transfer filter configurations at the site scope are removed. To carry out this task, the command first uses the **Get-CsFileTransferFilterConfiguration** cmdlet and the Filter parameter to return all the configurations at the site scope. The filter value "site:*" tells the **Get-CsFileTransferFilterConfiguration** cmdlet to return only those configurations that have an Identity that begins with the string value "site:". The filtered collection of configurations is then piped to the **Remove-CsFileTransferFilterConfiguration** cmdlet, which deletes each item in the collection.
  
    
    

```
Get-CsFileTransferFilterConfiguration -Filter site:* | Remove-CsFileTransferFilterConfiguration
```


### EXAMPLE 3

Example 3 shows you how you can remove all the file transfer filter configurations that are currently disabled. To do this, the command first uses the **Get-CsFileTransferFilterConfiguration** cmdlet to return a collection of all the file transfer filter configurations currently in use in the organization. That information is then piped to the **Where-Object** cmdlet, which selects only those file transfer filter configurations where the Enabled property is equal to (-eq) False ($False). That filtered collection is then piped to the **Remove-CsFileTransferFilterConfiguration** cmdlet, which proceeds to remove each item in the filtered collection.
  
    
    

```
Get-CsFileTransferFilterConfiguration | Where-Object {$_.Enabled -eq $False} | Remove-CsFileTransferFilterConfiguration
```


## Detailed Description

When sending instant messages, users can attach and send files to the other participants in the conversation. Skype for Business Server 2015 can be configured so that files with certain extensions--typically extensions of file types that could potentially prove harmful--are not allowed to be sent using a Skype for Business Server 2015 client.
  
    
    
The **Remove-CsFileTransferFilterConfiguration** cmdlet enables you to delete a file transfer filter configuration. For configurations at the site scope, the **Remove-CsFileTransferFilterConfiguration** cmdlet will remove the configuration; in turn, the users on the site will automatically inherit the global file transfer filter configuration. The **Remove-CsFileTransferFilterConfiguration** cmdlet can also be run against the global configuration. In that case, however, the global configuration will not be removed; instead, all the property values in that configuration will be reset to their default values.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the file transfer configuration to be removed. To refer to the global configuration, use this syntax:  `-Identity global`. To refer to a configuration at the site scope, use syntax similar to this:  `-Identity site:Redmond`. Note that you cannot use wildcard values when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration object. Accepts pipelined input of file transfer filter configuration objects.
  
    
    

## Return Types

This cmdlet does not return a value or object. Instead, it removes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration object.
  
    
    

## See also


#### 


  
    
    
 [New-CsFileTransferFilterConfiguration](new-csfiletransferfilterconfiguration.md)
  
    
    
 [Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)
  
    
    
 [Get-CsFileTransferFilterConfiguration](get-csfiletransferfilterconfiguration.md)
