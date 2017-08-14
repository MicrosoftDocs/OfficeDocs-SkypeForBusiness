---
title: Get-CsPersistentChatCategory
ms.prod: SKYPEFORBUSINESS
ms.assetid: 2ec14091-cb05-4c4c-b091-b7e88f5ca3cf
---


# Get-CsPersistentChatCategory
[]
Returns information about the Persistent Chat categories in use in your organization. A Persistent Chat category represents a collection of Persistent Chat chat rooms. Each chat room must be associated with a category. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Get-CsPersistentChatCategory [-PersistentChatPoolFqdn <String>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 returns information for all the Persistent Chat categories configured for use in the organization.
  
    
    

```

Get-CsPersistentChatCategory
```


### Example 2

In Example 2, information is returned for all the Persistent Chat categories configured for use on the pool atl-cs-001.litwareinc.com.
  
    
    

```
Get-CsPersistentChatCategory -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"
```


### Example 3

Example 3 returns information for all the Persistent Chat categories where the Invites property has been set to False. To do this, the command first uses the **Get-CsPersistentChatCategory** cmdlet to return a collection of all the Persistent Chat categories. This collection is then piped to the Where-Object cmdlet, which picks out only those categories where the Invites property is set to False ($False).
  
    
    

```
Get-CsPersistentChatCategory | Where-Object {$_.Invites -eq $False}
```


### Example 4

In Example 4, information is returned for all the Persistent Chat categories where Ken Myer is listed as one of the creators. To do this, the **Get-CsPersistentChatCategory** cmdlet is first used to return a collection of all the Persistent Chat categories. This collection is then piped to the **Where-Object** cmdlet, which picks out any category where the Creators property includes (-contains) the name "Ken Myer".
  
    
    

```
Get-CsPersistentChatCategory | Where-Object {$_.Creators -contains "Ken Myer"}
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
Persistent Chat categories provide a way for administrators to organize, and manage, Persistent Chat chat rooms. Categories provide a way for administrators to group related chat rooms; for example, all chat rooms used by the finance department can be grouped in the same category. Likewise, categories provide a way for administrators to manage permissions to these rooms, dictating which users are allowed access to the rooms, which users are denied access to the rooms, and which users are allowed to create new chat rooms within the category.
  
    
    
Note that all chat rooms must belong to a category; you cannot create a chat room without assigning that room to a category. That means that you must create at least one category before you can add any chat rooms to your Persistent Chat implementation.
  
    
    
 **Skype for Business Server Control Panel:** To view Persistent Chat categories in Skype for Business Server Control Panel, click **Persistent Chat** and then click **Category**.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the chat room category. The Identity consists of the Persistent Chat pool were the category is located followed by the category Name; for example:  <br/>  `-Identity "atl-gc-001.litwareinc.com\\ITChat"` <br/> |
| _AsObject_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, Active Directory display names are used when showing users who are on the AllowedMembers, DeniedMembers, or Creators lists. When not specified, SIP addresses are used when showing these users.  <br/> |
| _PersistentChatPoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the Persistent Chat pool that hosts Persistent Chat categories. If you use the PoolFqdn parameter without including the Name parameter, information will be returned for all the Persistent Chat categories on the specified pool. If you leave off both the Name and PoolFqdn parameters, then information will be returned for all your Persistent Chat categories.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPersistentChatCategory** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPersistentChatCategory** cmdlet returns instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [New-CsPersistentChatCategory](new-cspersistentchatcategory.md)
  
    
    
 [Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)
  
    
    
 [Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)
