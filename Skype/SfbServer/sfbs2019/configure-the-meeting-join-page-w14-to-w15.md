---
title: "Configure the meeting join page [W14 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 036c9d03-ad95-4d63-a3d8-6cae1a8ad530
description: "When a user clicks a meeting link in a meeting request, the meeting join page detects whether a Lync 2013 client is already installed on the user's computer. If a client is already installed, that client opens and joins the meeting. If a client is not installed, by default the 2013 version of Lync Web App opens."
---

# Configure the meeting join page [W14 to W15]
[]
When a user clicks a meeting link in a meeting request, the meeting join page detects whether a Lync 2013 client is already installed on the user's computer. If a client is already installed, that client opens and joins the meeting. If a client is not installed, by default the 2013 version of Lync Web App opens.
  
You can modify the behavior of the meeting join page if you want to allow users to join meetings with Office Communicator 2007 R2 or Lync 2010 Attendant. These configuration options have been removed from the Lync Server 2013 Control Panel, but you configure them by using the CsWebServiceConfiguration cmdlet.
  
**Meeting Join Page CsWebServiceConfiguration Parameters**

|**CsWebServiceConfiguration Parameter**|**Description**|
|:-----|:-----|
|ShowJoinUsingLegacyClientLink  <br/> |If set to True, users joining a meeting by using a client application other than Lync will be given the opportunity to join the meeting by using Office Communicator 2007 R2. The default value is False.  <br/> |
|ShowAlternateJoinOptionsExpanded  <br/> |When set to True then alternate options for joining an online conference (such as Office Communicator 2007 R2) will automatically be expanded and shown to users. When set to False (the default value) these options will be available, but the user will have to display the list of options for themselves.  <br/> |
   
## To configure the meeting join page by using Lync Server 2013 Management Shell

1. Start the Lync Server 2013 Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlet: 
    
  ```
  Get-CsWebServiceConfiguration
  ```

    This cmdlet returns the web service configuration settings.
    
3. Run the following command, with the parameters set to True or False, depending on your preference (for details about the parameters for this cmdlet, see the Lync Server 2013 Management Shell documentation):
    
  ```
  Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True
  ```


