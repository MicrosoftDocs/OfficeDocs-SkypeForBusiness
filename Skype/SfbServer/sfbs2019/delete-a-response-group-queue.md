---
title: "Delete a Response Group queue in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67c7a489-8c5f-4c6b-9387-9d4c11d43695
description: "Use one of the following procedures to delete a queue."
---

# Delete a Response Group queue in Lync Server 2013
[]
Use one of the following procedures to delete a queue.
  
### To use Lync Server Control Panel to delete a queue

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Response Groups**, and then click **Queue**.
    
4. In the search field, type part or all of the name of the queue you want to delete. 
    
5. In the list of queues, click the queue that you want, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
### To use Windows PowerShell to delete a queue

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, run:
    
  ```
  Get-CsRgsQueue -Identity <Application Server service> -Name "<name of queue>" | Remove-CsRgsQueue
  ```

    For example:
    
  ```
  Get-CsRgsQueue -Identity service:ApplicationServer:redmond.contoso.com -Name "Help Desk" | Remove-CsRgsQueue
  ```


