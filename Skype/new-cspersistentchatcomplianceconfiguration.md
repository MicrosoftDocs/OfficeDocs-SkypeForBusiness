---
title: New-CsPersistentChatComplianceConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: a61b76a9-0e2b-4f64-b2fa-cddadc15451c
---


# New-CsPersistentChatComplianceConfiguration
[]
Creates a new collection of Persistent Chat compliance configuration settings at the site or the service scope. Persistent Chat compliance enables administrators to maintain an archive of Persistent Chat items and activities including: new messages; new events (for example, a user entering or existing a chat room); file uploads and downloads; and searches run against the chat history. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

New-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-AdapterName <String>] [-AdapterOutputDirectory <String>] [-AdapterType <String>] [-AddChatRoomDetails <$true | $false>] [-AddUserDetails <$true | $false>] [-Confirm [<SwitchParameter>]] [-CreateFileAttachmentsManifest <$true | $false>] [-CustomConfiguration <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-OneChatRoomPerOutputFile <$true | $false>] [-RunInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 creates a new collection of Persistent Chat compliance configuration settings for the Redmond site. In this example, both the AddUserDetails and the AddChatRoomDetails properties are set to True ($True).
  
    
    

```

New-CsPersistentChatComplianceConfiguration -Identity "site:Redmond" -AddUserDetails $True -AddChatRoomDetails $True
```


### Example 2

Example 2 also demonstrates how to create a new collection of Persistent Chat compliance configuration settings for the Redmond site. In this example, the RunInterval property is set to 30 minutes; that is, 00 hours : 30 minutes : 00 seconds.
  
    
    

```
New-CsPersistentChatComplianceConfiguration -Identity "site:Redmond" -RunInterval "00:30:00"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
Many organizations (including organizations involved in health care and organizations involved in the financial industry) are required to maintain archives of all their electronic communications; this includes conversations that might take place using the Persistent Chat service. Skype for Business Server 2015 allows you to create a separate compliance database that keeps a detailed of archive of everything that happens in your Persistent Chat chat rooms. Persistent Chat compliance can be enabled or disabled at the site scope or at the service scope (that is, compliance can be enabled or disabled for a given Persistent Chat pool). In addition, Persistent Chat compliance can only be managed using the Windows PowerShell command-line interface; there are no options available in the Skype for Business Server Control Panel for managing Persistent Chat compliance.
  
    
    
Skype for Business Server Control Panel: The functions carried out by the **New-CsPersistentChatComplianceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |XdsIdentity  <br/> |Unique identifier for the new Persistent Chat compliance settings being created. New compliance settings can be created at either the site or the service scope (for the Persistent Chat Server service, only). To create new settings at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To create new settings at the service scope, use syntax like this:  <br/>  `-Identity "service:PersistentChatServer:atl-gc-001.litwareinc.com"` <br/> |
| _AdapterName_ <br/> |Optional  <br/> |String  <br/> |Name of the Persistent Chat adapters used by the compliance settings. Adapters are third-party products that convert the data in the compliance database to a specific format.  <br/> |
| _AdapterOutputDirectory_ <br/> |Optional  <br/> |String  <br/> |Full path to the folder where adapter data is stored. You must have a separate folder for each adapter.  <br/> |
| _AdapterType_ <br/> |Optional  <br/> |String  <br/> |Specifies the fully qualified name of a .Net managed type that implements the Microsoft.Rtc.Internal.Chat.Server.Compliance.IComplianceAdapter interface. This adapter is supplied by a third-party or can be set to the internal XML adapter, "Microsoft.Rtc.Internal.Chat.Server.Compliance.XmlAdapter,compliance".  <br/> If you do not specify an adapter type Persistent Chat will not save compliance data.  <br/> |
| _AddChatRoomDetails_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, additional details about each chat room are provided to the adapter. This has the potential to greatly increase the size of the compliance data.  <br/> The default value is False.  <br/> |
| _AddUserDetails_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, additional details about each chat room user are provided to the adapter. This has the potential to greatly increase the size of the compliance data.  <br/> The default value is False.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CreateFileAttachmentsManifest_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, additional output files will be created to track file transfers within chat rooms. These files will have the file extension .ATTACH and are placed in the location specified by the AdapterOutputDirectory.  <br/> |
| _CustomConfiguration_ <br/> |Optional  <br/> |String  <br/> |XSLT transform script that enables Persistent Chat to save compliance data in a custom format of your design.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _OneChatRoomPerOutputFile_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, separate reports are created for each chat room. The default value is False.  <br/> |
| _RunInterval_ <br/> |Optional  <br/> |TimeSpan  <br/> |Amount of time that the server waits before generating the next output file. The RunInterval must be specified using the format days.hours:minutes:seconds. For example, to specify a RunInterval of 30 minutes (the default value) use this syntax:  <br/>  `-RunInterval 00:30:00` <br/> The RunInterval can be set to any value between 1 minute (00:01.00) and 30 days (30.00:00:00), inclusive. The default value is 15 minutes (00:15:00).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **New-CsPersistentChatComplianceConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **New-CsPersistentChatComplianceConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)
  
    
    
 [Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)
  
    
    
 [Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)
