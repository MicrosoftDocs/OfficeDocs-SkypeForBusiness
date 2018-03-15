---
title: "Delete a Call Park orbit range in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 85e9f916-062d-450d-ac0a-aeaefc0f7cdc
description: "Use one of the following procedures to delete a Call Park orbit range."
---

# Delete a Call Park orbit range in Lync Server 2013
[]
Use one of the following procedures to delete a Call Park orbit range. 
  
### To use Lync Server Control Panel to delete a Call Park orbit range

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Features** and then click **Call Park**.
    
4. On the **Call Park** page, in the search field, type all or part of the name of the orbit range that you want to delete. 
    
5. In the resulting list of orbits, click the orbit, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
### To use Windows PowerShell to delete a Call Park orbit range

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, type:
    
  ```
  Remove-CsCallParkOrbit -Identity "<orbit range name>" 
  ```

    For example:
    
  ```
  Remove-CsCallParkOrbit -Identity "Redmond orbit 1"
  ```

    > [!NOTE]
    > For details about more options, see [Remove-CsCallParkOrbit](remove-cscallparkorbit.md). 
  
## See also

#### 

[Create or modify a Call Park orbit range in Lync Server 2013](create-or-modify-a-call-park-orbit-range.md)
#### 

[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)
  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

