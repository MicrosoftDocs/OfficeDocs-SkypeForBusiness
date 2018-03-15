---
title: "Modify the default action for clients not explicitly supported or restricted in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 548dd0f5-62fe-4c3f-8952-2b9fd4c5fff3
description: "In addition to specifying the version of clients that you want to support in your Lync Server 2013 environment, you can also specify a default action for clients that do not already have a version policy defined. This enables you to restrict which client versions are used in your Lync Server environment, which can help you control the costs associated with supporting multiple client versions."
---

# Modify the default action for clients not explicitly supported or restricted in Lync Server 2013
[]
In addition to specifying the version of clients that you want to support in your Lync Server 2013 environment, you can also specify a default action for clients that do not already have a version policy defined. This enables you to restrict which client versions are used in your Lync Server environment, which can help you control the costs associated with supporting multiple client versions.
  
### To modify the default action for clients not explicitly supported or restricted

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click **Client Version Configuration**.
    
4. On the **Client Version Configuration** page, double-click the **Global** configuration in the list. 
    
5. In the **Edit Client Version Configuration** dialog box, verify that the **Enable version control** check box is selected and then, under **Default action**, select one of the following:
    
  - **Allow** Allows the client to log on if the client version does not match any filter in the **Client version policies** list. 
    
  - **Block** Prevents the client from logging on if the client version does not match any filter in the **Client version policies** list. 
    
  - **Block with URL** Prevents the client from logging on if the client version does not match any filter in the **Client version policies** list, and include an error message containing a URL where a newer client can be downloaded. 
    
  - **Allow with URL** Allows the client to log on if the client version does not match any filter in the **Client version policies** list, and include an error message containing a URL where a newer client can be downloaded. 
    
6. If you selected **Block with URL**, type the client download URL to include in the error message in the **URL** box. 
    
7. Click **Commit**.
    
### To disable client version control

- To disable version control to allow all clients to log on regardless of the client version, clear the **Enable version control** check box, and then click **Commit**.
    
## Modifying the Default Action by Using Windows PowerShell Cmdlets

The default action to be taken when users try to sign on using clients that are not explicitly supported or restricted by a client version policy can be managed by using Windows PowerShell command-line interface and the **Set-CsClientVersionPolicy** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To configure the default action to block access

- The following command sets the default action for the Redmond site Block. This will block registration for any client for which no client version configuration rule exists.
    
  ```
  Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Block
  ```

### To configure the default action to allow access

- In this example, the default action for the Redmond site is set to Allow. This will allow registration for any client for which no client version configuration rule exists.
    
  ```
  Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Allow
  ```

For details, see the Help topic for the [Set-CsClientVersionPolicy](set-csclientversionpolicy.md) cmdlet. 
  
## See also

#### 

[Managing devices, phones, and client applications in Lync Server 2013](managing-devices-phones-and-client-applications.md)

