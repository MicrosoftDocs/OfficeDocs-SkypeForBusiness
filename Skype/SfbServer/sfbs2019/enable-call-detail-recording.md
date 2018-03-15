---
title: "Enable call detail recording in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b28e432-596f-45a5-a070-577d6fa748d9
description: "Call detail recording (CDR) records usage and diagnostic information about peer-to-peer activities including instance messaging, Voice over Internet Protocol (VoIP) calls, application sharing, file transfer, and meetings. The usage data can be used to calculate return on investment (ROI) and the diagnostic data can be used to troubleshoot peer-to-peer activities and meetings."
---

# Enable call detail recording in Lync Server 2013
[]
Call detail recording (CDR) records usage and diagnostic information about peer-to-peer activities including instance messaging, Voice over Internet Protocol (VoIP) calls, application sharing, file transfer, and meetings. The usage data can be used to calculate return on investment (ROI) and the diagnostic data can be used to troubleshoot peer-to-peer activities and meetings. 
  
Use the following procedure to enable CDR for your whole organization or each site in your organization.
  
> [!NOTE]
> In order to enable CDR you must configure monitoring and a monitoring database. For details, see [Deploying monitoring in Lync Server 2013](deploying-monitoring.md). 
  
### To enable CDR with Lync Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Call Detail Recording**. 
    
4. On the **Call Detail Recording** page, click the appropriate site from the table, click **Action**, and then click **Enable CDR**.
    
    > [!NOTE]
    > CDR is enabled by default. 
  
## Enabling CDR by Using Windows PowerShell Cmdlets

You can enable CDR by using Windows PowerShell and the **Set-CsCdrConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To enable CDR for a single location

- To disable CDR, set the EnableCDR parameter to True ($True).
    
  ```
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $True
  ```

### To disable CDR for a single location

- To disable CDR, set the EnableCDR parameter to False ($False). Disabling CDR does not uninstall monitoring. It pauses the collection and storage of CDR data.
    
  ```
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False
  ```

### To use a single command to enable CDR in multiple locations

- This command enables CDR for all the CDR configuration settings currently in use in your organization.
    
  ```
  Get-CsCdrConfiguration | Set-CsCdrConfiguration "site:Redmond" -EnableCDR $True
  ```

For more information, see the help topic for the [Set-CsCdrConfiguration](set-cscdrconfiguration.md) cmdlet. 
  
## See also

#### 

[Planning for monitoring in Lync Server 2013](planning-for-monitoring.md)
  
[Deploying monitoring in Lync Server 2013](deploying-monitoring.md)

