---
title: Get-CsPersistentChatComplianceConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 01fe3824-32fb-4d75-b80a-8a7dcc109911
---


# Get-CsPersistentChatComplianceConfiguration
[]
Returns information about the Persistent Chat compliance configuration settings currently in use in the organization. Persistent Chat compliance enables administrators to maintain an archive of Persistent Chat items and activities including: new messages; new events (for example, a user entering or existing a chat room); file uploads and downloads; and any searches run against the chat history. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Get-CsPersistentChatComplianceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 returns information about all the Persistent Chat compliance configuration settings currently in use in your organization.
  
    
    

```

Get-CsPersistentChatComplianceConfiguration
```


### Example 2

In Example 2, information is returned for the Persistent Chat compliance configuration settings applied to the Redmond site.
  
    
    

```
Get-CsPersistentChatComplianceConfiguration -Identity "site:Redmond"
```


### Example 3

Example 3 returns information about all the Persistent Chat compliance configuration settings applied to the service scope. This is done by including the Filter parameter and the filter value "service:*".
  
    
    

```
Get-CsPersistentChatComplianceConfiguration -Filter "service:*"
```


### Example 4

In Example 4, information is returned for all the Persistent Chat compliance configuration settings where the OneChatRoomPerOutputFile property is equal to True. To do this, the command first uses the **Get-CsPersistentChatComplianceConfiguration** to return a collection consisting of all the Persistent Chat compliance configuration settings. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the OneChatRoomPerOutputFile property is equal to True ($True).
  
    
    

```
Get-CsPersistentChatComplianceConfiguration | Where-Object {$_.OneChatRoomPerOutputFile -eq $True}
```


### Example 5

In Example 5, returned information is limited to Persistent Chat compliance configuration settings where the CustomConfiguration property is set to a null value. To carry out this task, the command first uses the **Get-CsPersistentChatComplianceConfiguration** cmdlet to return a collection of all the Persistent Chat compliance configuration settings currently in use. That collection is then piped to the **Where-Object** cmdlet, which selects only those settings where CustomConfiguration is equal to a null value ($Null)
  
    
    

```
Get-CsPersistentChatComplianceConfiguration | Where-Object {$_.CustomConfiguration -ne $Null}
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
Many organizations (including organizations involved in health care and organizations involved in the financial industry) are required to maintain archives of all their electronic communications; this includes conversations that might take place using the Persistent Chat service. Lync Server allows you to create a separate compliance database that keeps a detailed of archive of everything that happens in your Persistent Chat chat rooms. Persistent Chat compliance can be enabled or disabled at the site scope or at the service scope (that is, compliance can be enabled or disabled for a given Persistent Chat pool). In addition, Persistent Chat compliance can only be managed using the Windows PowerShell command-line interface; there are no options available in the Skype for Business Server Control Panel for managing Persistent Chat compliance.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsPersistentChatComplianceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the collection (or collections) of Persistent Chat compliance settings to be returned. For example, this syntax returns all the settings policies configured at the service scope:  <br/>  `-Filter "service:*"` <br/> The Filter and Identity parameters cannot be used in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Persistent Chat compliance settings to be returned. To return the global collection, use this syntax:  <br/>  `-Identity "global"` <br/> To return a collection of settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To return a collection configured at the service scope, use syntax like this:  <br/>  `-Identity "service:PersistentChatServer:atl-gc-001.litwareinc.com"` <br/> Note that you cannot use wildcards with the Identity parameter.  <br/> If neither the Identity parameter nor the Filter parameter are included in a command then the **Get-CsPersistentChatComplianceConfiguration** cmdlet will return information about all the Persistent Chat compliance settings in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Persistent Chat compliance data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPersistentChatComplianceConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPersistentChatComplianceConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [New-CsPersistentChatComplianceConfiguration](new-cspersistentchatcomplianceconfiguration.md)
  
    
    
 [Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)
  
    
    
 [Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)
