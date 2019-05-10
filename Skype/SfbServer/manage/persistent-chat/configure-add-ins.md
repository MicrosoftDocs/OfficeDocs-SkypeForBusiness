---
title: "Configure add-ins for Persistent Chat rooms in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c1037909-0750-411a-98c1-3a327eed4ae8
description: "Summary: Learn how to configure add-ins for Persistent Chat Server chat rooms in Skype for Business Server 2015."
---

# Configure add-ins for Persistent Chat rooms in Skype for Business Server 2015
 
**Summary:** Learn how to configure add-ins for Persistent Chat Server chat rooms in Skype for Business Server 2015.
  
Add-ins are used to extend the in-room experience by associating URLs with chat rooms. These URLs appear in the client conversation extensibility pane. A typical add-in might include a URL pointing to a Silverlight application that intercepts when a stock ticker is posted to a chat room, and shows the stock history in the extensibility pane. Other examples include embedding a OneNote 2013 URL in the chat room as an add-in to include some shared context, such as "Top of mind" or "Topic of the day."
  
 Before users can see an add-in in the client, you must add the add-in to the list of registered add-ins, and chat room Managers or Creators need to associate rooms with the add-in.
  
> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 

## Configure add-ins for chat rooms by using the Control Panel

To configure add-ins for chat rooms by using the Control Panel:
  
1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Add-in**.
    
    For multiple Persistent Chat Server pool deployments, select the appropriate pool from the drop-down list.
    
4. On the **Add-in** page, click **New**.
    
5. In **Select a Service**, select the service corresponding to the Persistent Chat Server pool where you need to create the Add-in. Add-ins cannot be moved from one pool to another or shared between different pools.
    
6. In **New Add-in**, do the following:
    
   - In **Name**, specify a name for the new add-in.
    
   - In **URL**, specify the URL to be associated with the add-in. URLs are limited to the http and https protocols.
    
7. Click **Commit**.
    
## Configure add-ins by using Windows PowerShell

You can configure add-ins for chat rooms by using the following Windows PowerShell cmdlets. For details about syntax, including all available parameters, see [Skype for Business Server 2015 Management Shell](../management-shell.md).
  

|**Cmdlet**|**Description**|
|:-----|:-----|
|New-CsPersistentChatAddin  <br/> |Create a new add-in  <br/> |
|Set-CsPersistentChatAddin  <br/> |Configure settings for an existing add-in  <br/> |
|Get-CsPersistentChatAddin  <br/> |Retrieve information about add-ins  <br/> |
|Remove-CsPersistentChatAddin  <br/> |Remove an add-in  <br/> |
   
### Create a new add-in

You can create a new Add-in by using the **New-CsPersistentChatAddin** cmdlet.
  
For example, the following command creates a new add-in (with the name ITPersistentChatAddin) for the pool atl-cs-001.contoso.com. The URL parameter and the parameter value http://atl-cs-001.contoso.com/itchat specify the location of the add-in's webpage:
  
```
New-CsPersistentChatAddin -Name "ITPersistentChatAddin" -PersistentChatPoolFqdn "atl-cs-001.contoso.com" -Url "http://atl-cs-001.contoso.com/itchat"
```

### Configure settings for an existing add-in

You can configure settings for an existing add-in by using the **Set-CsPersistentChatAddIn** cmdlet. For example, the following command modifies the URL assigned to the Persistent Chat add-in ITPersistentChatAddin. In this case, the URL is changed to http://atl-cs-001.contoso.com/itchat2:
  
```
Set-CsPersistentChatAddin -Identity "atl-cs-001.contoso.com\ITPersistentChatAddin" -Url "http://atl-cs-001.contoso.com/itchat2"
```

### Retrieve information about add-ins

You can get information about add-ins by using the **Get-CsPersistentChatAddin** cmdlet. For example, the following command returns information about all the Persistent Chat add-ins configured for use in the organization:
  
```
Get-CsPersistentChatAddin
```

### Remove an add-in

You can remove an Add-in by using the **Remove-CsPersistentChatAddIn** cmdlet. For example, the following command removes the Persistent Chat add-in ITChatAddin found on the pool atl-cs-001.contoso.com:
  
```
Remove-CsPersistentChatAddin -Identity "atl-cs-001.contoso.com\ITChatAddin"
```


