---
title: "Delete a Group Call Pickup number range in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 521891f3-7a5d-45de-92dc-d57025453159
description: "Use the following procedure to delete a Group Call Pickup number range."
---

# Delete a Group Call Pickup number range in Lync Server 2013
[]
Use the following procedure to delete a Group Call Pickup number range. 
  
### To delete a call pickup group number range

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, type:
    
  ```
  Remove-CsCallParkOrbit -Identity "<group number range name>" 
  ```

    For example:
    
  ```
  Remove-CsCallParkOrbit -Identity "Redmond call pickup"
  ```

    > [!NOTE]
    > For details about more options, see [Remove-CsCallParkOrbit](remove-cscallparkorbit.md). 
  
## See also

#### 

[Create or modify a Call Park orbit range in Lync Server 2013](create-or-modify-a-call-park-orbit-range.md)
#### 

[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)
  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

