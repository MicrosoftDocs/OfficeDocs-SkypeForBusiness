---
title: Import-CsPersistentChatData
ms.prod: SKYPEFORBUSINESS
ms.assetid: 17151a25-5dea-498a-93d5-fed3da7d3fa5
---


# Import-CsPersistentChatData
[]
Enables administrators to import data exported from a Microsoft Lync Server 2010 Group Chat database into a Skype for Business Server 2015 Persistent Chat database. This data must have previously been exported from the Group Chat database by using the **Export-CsPersistentChatData** cmdlet. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Import-CsPersistentChatData -FileName <String> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown on Example 1 reads exported Persistent Chat data from the file C:\\Logs\\PersistentChatExport.xml and then adds that data to the Persistent Chat database atl-sql-001.litwareinc.com\\rtc (where "atl-sql-001.litwareinc.com" is the fully qualified domain name of the SQL Server computer and "rtc" is the SQL Server database instance).
  
    
    

```

Import-CsPersistentChatData -DBInstance "atl-sql-001.litwareinc.com\\rtc" -FileName "C:\\Logs\\PersistentChatExport.zip"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
    
    
If you are currently running Lync Server 2010, you can migrate your current Group Chat implementation by using the E **xport-CsPersistentChatData** cmdlet to export your existing Group Chat configuration settings, then use the **Import-CsPersistentChatData** cmdlet to migrate that information to Lync Server 2013 and the Persistent Chat service. Note that the **Export-CsPersistentChatData** cmdlet gives you the option of importing all your Group Chat settings and data or only a portion of your Group Chat settings and data; for example, you can export (and then import) your Group Chat categories and chat rooms without exporting all the content associated with those categories and chat rooms.
  
    
    
Although primarily intended for migration purposes, the **CsPersistentChatData** cmdlets can also be used to manage Persistent Chat data on Skype for Business Server 2015.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Import-CsPersistentChatData** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ByteInput_ <br/> |Required  <br/> |System.Byte[]  <br/> |When specified, data is imported as a byte array rather than an XML file.  <br/> |
| _DBInstance_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name and name of the SQL Server instance where the Skype for Business Server 2015 Persistent Chat database is located. For example, this syntax specifies the database found in the RTC database instance on the server atl-sql-001.litwareinc.com:  <br/>  `-DBInstance "atl-sql-001.litwareinc.com\\rtc"` <br/> |
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Full path to the XML file being imported. For example:  <br/>  `-FileName "C:\\Logs\\PersistentChatExport.xml"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\\Logs\\PersistentChatExport.html"` <br/>  If this file already exists, it will be overwritten when you run the cmdlet. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Import-CsPersistentChatData** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None.
  
    
    

