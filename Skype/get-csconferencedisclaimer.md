---
title: Get-CsConferenceDisclaimer
ms.prod: SKYPEFORBUSINESS
ms.assetid: 2382aaef-9c5e-43f8-99de-6c880134db7d
---


# Get-CsConferenceDisclaimer
[]
Returns information about the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 returns information about the conference disclaimer configured for use in your organization. Because you are limited to a single disclaimer (configured at the global scope), you do not need to specify an Identity when running this command.
  
    
    

```

Get-CSConferenceDisclaimer
```


## Detailed Description

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants at the time participants join conferences hosted by Skype for Business Server 2015. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference, and users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note that this disclaimer is only shown to users who join a conference by using a hyperlink.
  
    
    
The **Get-CsConferenceDisclaimer** cmdlet enables you to view the body and header of your organization's disclaimer.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values when referencing a conference disclaimer. Because you can only have a single, global instance of the conference disclaimer, there is really no reason to ever use the Filter parameter. However, you can use the following syntax to reference the global disclaimer:  `-Filter "g*"`. That syntax brings back all the conference disclaimers that have an Identity that begins with the letter "g".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the conference disclaimer. Because you can only have a single, global instance of the conference disclaimer, you do not need to specify an Identity when calling the **Get-CsConferenceDisclaimer** cmdlet. You can, however, use the following syntax to reference the global disclaimer: `-Identity global`.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the conference disclaimer data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

The **Get-CsConferenceDisclaimer** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object.
  
    
    

## See also


#### 


  
    
    
 [Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)
  
    
    
 [Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)
