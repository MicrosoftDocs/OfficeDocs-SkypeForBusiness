---
title: "Configure the meeting join page"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: End User
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "When a user clicks a meeting link in a meeting request, the meeting join page detects which client is already installed on the user's computer. If a client is already installed, that client opens and joins the meeting. If a client is not installed, by default the Web App opens."
---

# Configure the meeting join page

When a user clicks a meeting link in a meeting request, the meeting join page detects which client is already installed on the user's computer. If a client is already installed, that client opens and joins the meeting. If a client is not installed, by default the Web App opens.
  
You can modify the behavior of the meeting join page if you want to allow users to join meetings. These configuration options have been removed from the Control Panel, but you configure them by using the CsWebServiceConfiguration cmdlet.
  
**Meeting Join Page CsWebServiceConfiguration Parameters**

|**CsWebServiceConfiguration Parameter**|**Description**|
|:-----|:-----|
|ShowJoinUsingLegacyClientLink  <br/> |If set to True, users joining a meeting by using a client application other than Lync will be given the opportunity to join the meeting. The default value is False.  <br/> |
|ShowAlternateJoinOptionsExpanded  <br/> |When set to True, alternate options for joining an online conference will automatically be expanded and shown to users. When set to False (the default value), these options will be available, but the user will have to display the list of options for themselves.  <br/> |
   
### To configure the meeting join page by using Skype for Business Server 2019 Management Shell

1. Start the Skype for Business Server 2019 Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.
    
2. Run the following cmdlet: 
    
   ```
   Get-CsWebServiceConfiguration
   ```

    This cmdlet returns the web service configuration settings.
    
3. Run the following command, with the parameters set to True or False, depending on your preference (for details about the parameters for this cmdlet, see the [Skype for Business Server Management Shell](../../SfbServer/manage/management-shell.md) documentation):
    
   ```
   Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True
   ```


