---
title: Set-CsPersistentChatAddin
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1badd6b5-e519-47a1-9434-9fa5a00b79ff
---


# Set-CsPersistentChatAddin
[]
Modifies an existing Persistent Chat add-in. A Persistent Chat add-in is a customized web page that can be embedded within a Persistent Chat client. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Set-CsPersistentChatAddin -Instance <Addin> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

Example 1 modifies the URL assigned to the Persistent Chat add-in ITPersistentChatAddin. In this case, the URL is changed to http://atl-cs-001.litwareinc.com/itchat2.
  
    
    

```

Set-CsPersistentChatAddin -Identity "atl-cs-001.litwareinc.com\\ITPersistentChatAddin" -Url "http://atl-cs-001.litwareinc.com/itchat2"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
Add-ins serve as extensions to a Persistent Chat chat room. Add-ins are external applications (that is, items not built into Persistent Chat itself) that are associated with a particular chat room. For example, a help desk chat room might include a URL that links to a Web page or to a Silverlight application that shows the status of the day's help requests. The Skype for Business Server 2015Windows PowerShell command-line interface cmdlets do not provide the ability to create these add-ins. Instead, the **CsPersistentChatAddin** cmdlets are used to associate (or disassociate) an add-in from a chat room.
  
    
    
 ** **Skype for Business Server Control Panel **:** To modify an existing Persistent Chat add-in using the Skype for Business Server Control Panel, click **Persistent Chat**, click **Add-in**, then double-click the add-in to be modified.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the Persistent Chat add-in. The Identity is composed of the fully qualified domain name of the Persistent Chat pool where the add-in is located, a "\\" character, and the add-in name. For example:  <br/>  `-Identity "atl-gc-001.litwareincom\\ITPersistentChatAddin"` <br/> |
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.Addin  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Friendly name given to the Persistent Chat add-in. Names must be unique per Persistent Chat pool.  <br/> |
| _Url_ <br/> |Optional  <br/> |System.String  <br/> |URL of the Web page to be displayed by the Persistent Chat add-in.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatAddin** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatAddin** cmdlet modifies existing instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsPersistentChatAddin](get-cspersistentchataddin.md)
  
    
    
 [New-CsPersistentChatAddin](new-cspersistentchataddin.md)
  
    
    
 [Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)
