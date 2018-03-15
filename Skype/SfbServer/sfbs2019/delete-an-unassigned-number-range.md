---
title: "Delete an unassigned number range in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a8141bfb-b94d-4d0f-a7a9-2e60d10b103a
description: "Use one of the following procedures to delete an unassigned number range for Announcements."
---

# Delete an unassigned number range in Lync Server 2013
[]
Use one of the following procedures to delete an unassigned number range for Announcements.
  
### To use Lync Server Control Panel to delete an unassigned number range

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Features** and then click **Unassigned Number**.
    
4. On the **Unassigned Number** page, in the search field, type all or part of the name of the unassigned number range you want to delete. 
    
5. In the resulting list of number ranges, click the name, click **Edit**, and then click **Delete**.
    
6. Click **Commit all**.
    
### To use Windows PowerShell to delete an unassigned number range

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, type:
    
  ```
  Remove-CsUnassignedNumber -Identity "<name of unassigned number range>" 
  ```

    For example:
    
  ```
  Remove-CsUnassignedNumber -Identity "Unassigned range 1"
  ```

    > [!NOTE]
    > For details about more options, see [Remove-CsCallParkOrbit](remove-cscallparkorbit.md). 
  
## See also

#### 

[Create or modify an unassigned number range in Lync Server 2013](create-or-modify-an-unassigned-number-range.md)
#### 

[Remove-CsUnassignedNumber](remove-csunassignednumber.md)
  
[Get-CsUnassignedNumber](get-csunassignednumber.md)

