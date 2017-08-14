---
title: Set-CsPersistentChatComplianceConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 615625f8-574a-4832-8d3f-26721cd124d8
---


# Set-CsPersistentChatComplianceConfiguration
[]
Modifies an existing collection of Persistent Chat compliance configuration settings. Persistent Chat compliance enables administrators to maintain an archive of Persistent Chat items and activities including: new messages; new events (for example, a user entering or existing a chat room); file uploads and downloads; and searches run against the chat history. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Set-CsPersistentChatComplianceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

Example 1 sets the RunInterval property of the global collection of Persistent Chat compliance configuration settings to 10 minutes: 00 hours : 10 minutes : 00 seconds.
  
    
    

```

Set-CsPersistentChatComplianceConfiguration -Identity "global" -RunInterval "00:10:00"
```


### Example 2

In Example 2, the RunInterval property for all the Persistent Chat compliance configuration settings currently in use in the organization is set to 10 minutes. To do this, the **Get-CsPersistentChatComplianceConfiguration** cmdlet is first called without any parameters in order to return a collection of all the compliance settings. This collection is then piped to the **Set-CsPersistentChatComplianceConfiguration** cmdlet, which changes the value of the RunInterval property for each item in the collection to 10 minutes.
  
    
    

```
Get-CsPersistentChatComplianceConfiguration | Set-CsPersistentChatComplianceConfiguration  -RunInterval "00:10:00"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
Many organizations (including organizations involved in health care and organizations involved in the financial industry) are required to maintain archives of all their electronic communications; this includes conversations that might take place using the Persistent Chat service. Lync Server allows you to create a separate compliance database that keeps a detailed of archive of everything that happens in your Persistent Chat chat rooms. Persistent Chat compliance can be enabled or disabled at the site scope or at the service scope (that is, compliance can be enabled or disabled for a given Persistent Chat pool). In addition, Persistent Chat compliance can only be managed using Windows PowerShell command-line interface; there are no options available in the Skype for Business Server Control Panel for managing Persistent Chat compliance.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsPersistentChatComplianceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AdapterName_ <br/> |Optional  <br/> |String  <br/> |Name of the Persistent Chat adapters. Adapters are third-party products that convert the data in the compliance database to a specific format.  <br/> |
| _AdapterOutputDirectory_ <br/> |Optional  <br/> |String  <br/> |Full path to the folder where adapter data is stored. You must have a separate folder for each adapter.  <br/> |
| _AdapterType_ <br/> |Optional  <br/> |String  <br/> |Specifies the fully qualified name of a .Net managed type that implements the Microsoft.Rtc.Internal.Chat.Server.Compliance.IComplianceAdapter interface. This adapter is supplied by a third-party or can be set to the internal XML adapter, "Microsoft.Rtc.Internal.Chat.Server.Compliance.XmlAdapter,compliance".  <br/> If you do not specify an adapter type Persistent Chat will not save compliance data.  <br/> |
| _AddChatRoomDetails_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, additional details about each chat room are provided to the adapter. This has the potential to greatly increase the size of the compliance data.  <br/> The default value is False.  <br/> |
| _AddUserDetails_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, additional details about each chat room user are provided to the adapter. This has the potential to greatly increase the size of the compliance data.  <br/> The default value is False.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CreateFileAttachmentsManifest_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, additional output files will be created to track file transfers within chat rooms. These files will have the file extension .ATTACH and are placed in the location specified by the AdapterOutputDirectory.  <br/> |
| _CustomConfiguration_ <br/> |Optional  <br/> |String  <br/> |XSLT transform script that enables Persistent Chat to save compliance data in a custom format of your design.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsIdentity  <br/> |Unique identifier for the Persistent Chat compliance settings to be modified. To modify the global collection, use this syntax:  <br/>  `-Identity "global"` <br/> To modify a collection of settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To modify a collection configured at the service scope, use syntax like this:  <br/>  `-Identity "service:PersistentChatServer:atl-gc-001.litwareinc.com"` <br/> If this parameter is not included then the **Set-CsPersistentChatComplianceConfiguration** cmdlet will modify the global collection. <br/> |
| _Instance_ <br/> |Optional  <br/> |PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _OneChatRoomPerOutputFile_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, separate reports are created for each chat room. The default value is False.  <br/> |
| _RunInterval_ <br/> |Optional  <br/> |TimeSpan  <br/> |Amount of time that the server waits before generating the next output file. The RunInterval must be specified using the format days.hours:minutes:seconds. For example, to specify a RunInterval of 15 minutes (the default value) use this syntax:  <br/>  `-RunInterval 00:15:00` <br/> The RunInterval can be set to any value between 1 minute (00:01.00) and 30 days (30.00:00:00), inclusive.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatComplianceConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatComplianceConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)
  
    
    
 [New-CsPersistentChatComplianceConfiguration](new-cspersistentchatcomplianceconfiguration.md)
  
    
    
 [Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)
