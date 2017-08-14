---
title: Get-CsPersistentChatRoom
ms.prod: SKYPEFORBUSINESS
ms.assetid: 9826c44b-35a6-473e-97d4-952415d640d1
---


# Get-CsPersistentChatRoom
[]
Returns information about the Persistent Chat chat rooms configured for use in your organization. A chat room is a discussion forum that typically revolves around a specific topic. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Get-CsPersistentChatRoom [-Addin <String>] [-Category <String>] [-ChatContentExceedsMB <Int32>] [-Disabled <$true | $false>] [-Filter <String>] [-Invitations <False | Inherit>] [-Manager <String>] [-Member <String>] [-PersistentChatPoolFqdn <String>] [-Privacy <Open | Closed | Secret>] [-ResultSize <Int32>] [-SearchDescription <SwitchParameter>] [-Type <Normal | Auditorium>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 returns information about the Persistent Chat chat rooms configured for use in the organization.
  
    
    

```

Get-CsPersistentChatRoom
```


### Example 2

Example 2 returns information for a single Persistent Chat chat room: the room with the Identity atl-cs-001.litwareinc.com\\ITChatRoom.
  
    
    

```
Get-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\\ITChatRoom"
```


### Example 3

In Example 3, information is returned for all the Persistent Chat chat rooms configured for the pool atl-cs-001.litwareinc.com.
  
    
    

```
Get-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
Persistent Chat discussions take the form of messages posted in individual chat rooms; chat rooms are discussion forums based on specific topics. By design, messages posted in a chat room remain there forever; at any time, users can return to the room and review all the messages that have been previously posted. 
  
    
    
The **Get-CsPersistentChatRoom** cmdlet provides a way to return information about all the chat rooms configured for use in your organization.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Addin_ <br/> |Optional  <br/> |System.String  <br/> |Returns chat rooms associated with the specified chat room add-in.  <br/> Note that you can only specify one add-in per command.  <br/> |
| _AsObject_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, Active Directory display names are used when showing users who are on the Managers or Presenters lists. When not specified, SIP addresses are used when showing these users.  <br/> |
| _Category_ <br/> |Optional  <br/> |System.String  <br/> |Returns information for all the Persistent Chat chat rooms in the specified category. For example:  <br/>  `-Category "ITChat"` <br/> You can only specify a single category when using the Category parameter. In addition, you cannot use the PersistentChatPoolFqdn, Filter, or Identity parameters in any command that uses the Category parameter.  <br/> |
| _ChatContentExceedsMB_ <br/> |Optional  <br/> |System.Int32  <br/> |Returns chat rooms whose cumulative chat content exceeds the specified value (in megabytes).  <br/> |
| _Disabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Enables you to search for active chat rooms (by using the parameter value $False) or disabled chat rooms (by using the parameter value $True).  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to return information for Persistent Chat chat rooms based on the Name and/or the Description of the room. To return information for a chat room with a specific name, use syntax similar to this:  <br/>  `-Filter {Name -like "ITChat"}` <br/> That syntax returns information only for chat rooms that have the name ITChat.  <br/> |
| _Identity_ <br/> |Optional  <br/> |System.String  <br/> |Unique Identifier for the Persistent Chat chat room being returned. The Identity for a chat room consists of the Persistent Chat pool where the room has been configured plus the name of the room; for example:  <br/>  `-Identity "atl-gc-001.litwareinc.com\\RedmondChatRoom"` <br/> You cannot use the Category, Filter, or PersistentChatPoolFqdn parameters in any command that uses the Identity parameter. If you call the **Get-CsPersistentChatRoom** cmdlet without any parameters the cmdlet will return information about all the chat rooms configured for use in your organization. <br/> |
| _Invitations_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomInvitations  <br/> |Returns chat rooms that use invitations (by using the parameter value Inherit) or chat rooms that do not use invitations (by using the parameter value False).  <br/> |
| _Manager_ <br/> |Optional  <br/> |System.String  <br/> |Returns chat rooms managed by the specified user. For example:  <br/>  `-Manager "sip:kenmyer@litwareinc.com"` <br/> Note that you can only specify a single manager per command.  <br/> |
| _Member_ <br/> |Optional  <br/> |System.String  <br/> |Returns chat rooms that the specified user is a member of. For example:  <br/>  `-Member "sip:kenmyer@litwareinc.com"` <br/> Note that you can only specify a single member per command.  <br/> |
| _PersistentChatPoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Returns information about all the Persistent Chat chat rooms configured on the specified Persistent Chat pool. For example:  <br/>  `-PersistentChatPoolFqdn "atl-gc-001.litwareinc.com"` <br/> You cannot use the Category, Filter, or Identity parameters in any command that uses the PersistentChatPoolFqdn parameter.  <br/> |
| _Privacy_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomPrivacy  <br/> |Enables you to return chat rooms that meet the specified privacy setting. Allowed values are:  <br/> * Open (any user can locate the chat room by doing a directory search, and anyone can participate in chat room activities)  <br/> * Secret (only chat room members can locate the room by doing a directory search, and only members can participate in chat room activities)  <br/> * Closed (any user can locate the chat room by doing a directory search, but only members can participate in chat room activities)  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |System.Int32  <br/> |Enables you to limit the number of records returned by the cmdlet. For example, to return seven chat rooms (regardless of the number of rooms in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven rooms will be returned.  <br/>  The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the ResultSize to 7 but you have only three rooms in your forest, the command will return those three rooms, and then complete without error. <br/> |
| _SearchDescription_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to search for the specified text value in either the chat room Name or the chat room Description. To search both the Name and the Description, include the SearchDescription parameter along with the Filter parameter. For example:  <br/>  `-SearchDescription -Filter "IT chat room"` <br/> |
| _Type_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomType  <br/> |Returns chat rooms by room type. Allowed values are:  <br/> * Normal (chat rooms where all members can post messages)  <br/> * Auditorium (chat rooms where only presenters can post messages)  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPersistentChatRoom** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPersistentChatRoom** cmdlet returns instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)
  
    
    
 [New-CsPersistentChatRoom](new-cspersistentchatroom.md)
  
    
    
 [Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)
  
    
    
 [Set-CsPersistentChatRoom](set-cspersistentchatroom.md)
