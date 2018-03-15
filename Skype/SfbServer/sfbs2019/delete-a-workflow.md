---
title: "Delete a workflow in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0469a6b8-ce1e-459b-bc3d-4c8adf2d97d5
description: "Use one of the following procedures to delete a workflow."
---

# Delete a workflow in Lync Server 2013
[]
Use one of the following procedures to delete a workflow.
  
### To use Lync Server Control Panel delete a workflow

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Response Groups**, and then click **Workflow**.
    
4. On the **Workflow** page, click **Create or edit a workflow**.
    
5. In the **Select a Service** search field, type part or all of the name of the **ApplicationServer** service that hosts the workflow that you want to delete. 
    
6. In the list of services, click the service that you want, and then click **OK**.
    
    > [!NOTE]
    > The Response Group Configuration Tool webpage opens. You can also open the Response Group Configuration Tool webpage directly from a web browser by connecting to **https:// _\<webPoolFqdn\>_/RgsConfig**. 
  
7. Under **Manage an Existing Workflow**, locate the workflow you want to delete, and then under **Action**, click **Delete**.
    
8. Click **Yes**.
    
### To use Windows PowerShell to delete a workflow

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, run:
    
  ```
  Get-CsRgsWorkflow -Identity <Application Server service> -Name "<name of workflow>" | Remove-CsRgsWorkflow
  ```

    For example:
    
  ```
  Get-CsRgsWorkflow -Identity service:ApplicationServer:redmond.contoso.com -Name "Help Desk" | Remove-CsRgsWorkflow
  ```


