---
title: "Configure the meeting join page in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6537765e-4384-416f-92f1-a7f3b39ebe56
description: "Summary: Learn how to configure the meeting join page in Skype for Business Server."
---

# Configure the meeting join page in Skype for Business Server
 
**Summary:** Learn how to configure the meeting join page in Skype for Business Server.
  
When a user clicks a meeting link in a meeting request, the meeting join page detects whether a Skype for Business client is already installed on the user's computer. If a client is already installed, the client opens and joins the meeting. If a client is not installed, by default the Skype for Business client opens. 
  
## Configure the meeting join page

You can modify the behavior of the meeting join page if you want to allow users to join meetings with other versions of the client. These configuration options have been removed from the Skype for Business Server Control Panel, but you configure them by using the Set-CsWebServiceConfiguration cmdlet.
  
**Meeting Join Page Set-CsWebServiceConfiguration parameters**

|**Set-CsWebServiceConfiguration parameter**|**Description**|
|:-----|:-----|
|ShowJoinUsingLegacyClientLink  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server.  <br/> If set to True, users joining a meeting by using a client application other than Skype for Business will be given the opportunity to join the meeting by using their current client application. The default value is False.  <br/> |
|ShowAlternateJoinOptionsExpanded  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server.  <br/>  If set to True, alternate options for joining an online conference are automatically expanded and shown to users. If set to False (the default value), these options will be available, but the user will have to display the list of options for themselves.  <br/> |
   

