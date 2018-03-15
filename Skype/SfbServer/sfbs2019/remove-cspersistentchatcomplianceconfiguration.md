---
title: "Remove-CsPersistentChatComplianceConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2d54eabf-fbb5-435b-9a71-d6b03beb09a5
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsPersistentChatComplianceConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Removes an existing collection of Persistent Chat compliance configuration settings. Persistent Chat compliance enables administrators to maintain an archive of Persistent Chat items and activities including: new messages; new events (for example, a user entering or existing a chat room); file uploads and downloads; and searches run against the chat history. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 removes the Persistent Chat compliance configuration settings applied to the Redmond site.
  
```
Remove-CsPersistentChatComplianceConfiguration -Identity "site:Redmond"
```

### Example 2

In Example 2, all the Persistent Chat compliance configuration settings applied to the site scope are removed. To do that, the command first uses the **Get-CsPersistentChatComplianceConfiguration** cmdlet and the Filter parameter to retrieve all the settings assigned to the site scope; that task is performed by using the filter value "site:*". After the site-scoped settings have been retrieved, they are then piped to, and removed by, the **Remove-CsPersistentChatComplianceConfiguration** cmdlet. 
  
```
Get-CsPersistentChatComplianceConfiguration -Filter "site:*" | Remove-CsPersistentChatComplianceConfiguration
```

### Example 3

Example 3 shows how you can remove all the Persistent Chat compliance configuration settings where both the AddUserDetails and AddChatRoomDetails properties are set to True. To carry out this task, the command first uses the **Get-CsPersistentChatComplianceConfiguration** cmdlet to return a collection of all the Persistent Chat compliance configuration settings. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the AddUserDetails property and the AddChatRoomDetails properties are equal to True ($True). This filtered collection is then piped to the **Remove-CsPersistentChatComplianceConfiguration** cmdlet, which proceeds to delete each item in that filtered collection. 
  
```
Get-CsPersistentChatComplianceConfiguration | Where-Object {$_.AddUserDetals -eq $True -and $_.AddChatRoomDetails -eq $True} | Remove-CsPersistentChatComplianceConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
Many organizations (including organizations involved in health care and organizations involved in the financial industry) are required to maintain archives of all their electronic communications; this includes conversations that might take place using the Persistent Chat service. Lync Server 2013 allows you to create a separate compliance database that keeps a detailed of archive of everything that happens in your Persistent Chat chat rooms. Persistent Chat compliance can be enabled or disabled at the site scope or at the service scope (that is, compliance can be enabled or disabled for a given Persistent Chat pool). In addition, Persistent Chat compliance can only be managed using the Windows PowerShell command-line interface; there are no options available in the Lync Server 2013 Control Panel for managing Persistent Chat compliance.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsPersistentChatComplianceConfiguration"}
  
 **Lync Server Control Panel:** The functions carried out by the **Remove-CsPersistentChatComplianceConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Persistent Chat compliance settings to be removed. To remove a collection of settings configured at the site scope, use syntax similar to this:  <br/> -Identity "site:Redmond"  <br/> To remove a collection configured at the service scope, use syntax like this:  <br/> -Identity "service:PersistentChatServer:atl-gc-001.litwareinc.com"  <br/> Note that you cannot use wildcards with the Identity parameter.  <br/> You can also run the **Remove-CsPersistentChatComplianceConfiguration** cmdlet against the global settings collection. In that case, however, the global collection will not be removed. Instead, all the properties within that collection will be reset to their default values.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPersistentChatComplianceConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPersistentChatComplianceConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)
  
[New-CsPersistentChatComplianceConfiguration](new-cspersistentchatcomplianceconfiguration.md)
  
[Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)

