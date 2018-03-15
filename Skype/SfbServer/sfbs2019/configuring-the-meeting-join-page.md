---
title: "Configuring the meeting join page in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 45880423-47f4-49af-b825-cbd8e3fc1046
description: "When a user clicks a meeting link in a meeting request, the meeting join page detects whether a Lync 2013 client is already installed on the user's computer. If a client is already installed, the client opens and joins the meeting. If a client is not installed, by default the 2013 version of Lync Web App opens."
---

# Configuring the meeting join page in Lync Server 2013
[]
When a user clicks a meeting link in a meeting request, the meeting join page detects whether a Lync 2013 client is already installed on the user's computer. If a client is already installed, the client opens and joins the meeting. If a client is not installed, by default the 2013 version of Lync Web App opens.
  
You can modify the behavior of the meeting join page if you want to allow users to join meetings with Office Communicator 2007 R2 or Lync 2010 Attendant. These configuration options have been removed from the Lync Server 2013 Control Panel, but you configure them by using the Set-CsWebServiceConfiguration cmdlet.
  
**Meeting Join Page Set-CsWebServiceConfiguration Parameters**

|**Set-CsWebServiceConfiguration Parameter**|**Description**|
|:-----|:-----|
|ShowJoinUsingLegacyClientLink  <br/> |If set to True, users joining a meeting by using a client application other than Lync will be given the opportunity to join the meeting by using Office Communicator 2007 R2. The default value is False.  <br/> |
|ShowAlternateJoinOptionsExpanded  <br/> |When set to True then alternate options for joining an online conference (such as Office Communicator 2007 R2) will automatically be expanded and shown to users. When set to False (the default value) these options will be available, but the user will have to display the list of options for themselves.  <br/> |
   
## To configure the meeting join page by using Lync Server 2013 Management Shell

1. Start the Lync Server 2013 Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. To view the web service configuration settings, run the following cmdlet: 
    
  ```
  Get-CsWebServiceConfiguration
  ```

3. Run the following command, with the parameters set to True or False, depending on your preference (for details about the parameters for this cmdlet, see [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md) in the Lync Server 2013 Management Shell documentation): 
    
  ```
  Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True
  ```

## See also

#### 

[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

