---
title: "Delete an agent group in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: df385fd1-62f4-42b7-a349-4eb38dea50c8
description: "Use one of the following procedures to delete an agent group."
---

# Delete an agent group in Lync Server 2013
[]
Use one of the following procedures to delete an agent group. 
  
### To use Lync Server Control Panel to delete an agent group

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Response Groups**, and then click **Group**.
    
4. On the **Response Groups** page, type all or part of the name of the agent group that you want to delete in the search field. 
    
5. In the resulting list, click the group that you want to delete, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
### To use Windows PowerShell to delete an agent group

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, run:
    
  ```
  Get-CsRgsAgentGroup -Identity <Application Server service> -Name "<name of agent group>" | Remove-CsRgsAgentGroup
  ```

    For example:
    
  ```
  Get-CsRgsAgentGroup -Identity service:ApplicationServer:redmond.contoso.com -Name "Human Resources" | Remove-CsRgsAgentGroup
  ```

## See also

#### 

[Create or modify an agent group in Lync Server 2013](create-or-modify-an-agent-group.md)
#### 

[Remove-CsRgsAgentGroup](remove-csrgsagentgroup.md)
  
[Get-CsRgsAgentGroup](get-csrgsagentgroup.md)

