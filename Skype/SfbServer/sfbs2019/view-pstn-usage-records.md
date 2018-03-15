---
title: "View PSTN usage records in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 65025c78-c263-472c-9ff9-e170588f10b5
description: "A public switched telephone network (PSTN) usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users or groups of users in an organization. For details, see PSTN usage records in Lync Server 2013 in the Planning documentation."
---

# View PSTN usage records in Lync Server 2013
[]
A public switched telephone network (PSTN) usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users or groups of users in an organization. For details, see [PSTN usage records in Lync Server 2013](pstn-usage-records.md) in the Planning documentation. 
  
### To view a PSTN usage record by using Lync Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing** and then click **PSTN Usage**.
    
4. On the **PSTN Usage** page, highlight the PSTN usage record you want to view, click **Edit** and then click **Show details**.
    
    > [!NOTE]
    > A read-only page of the selected PSTN usage record shows the associated routes and associated voice policies. 
  
## Viewing PSTN Usage Information by Using Windows PowerShell Cmdlets

You can also view PSTN usages by using Windows PowerShell and the **Get-CsPstnUsage** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view PSTN usage information by using Windows PowerShell cmdlets

- To view information about all of your PSTN usages, type the following command in the Lync Server Management Shell, and then press ENTER:
    
  ```
  Get-CsPstnUsage
  ```

    This command returns information similar to the following:
    
  ```
  Identity : Global
  Usage    : {Internal, Local, Long Distance}
  ```

For details, see [Get-CsPstnUsage](get-cspstnusage.md).
  
## See also

#### 

[Create a voice policy and configure PSTN usage records in Lync Server 2013](create-a-voice-policy-and-configure-pstn-usage-records.md)
  
[Modify a voice policy and configure PSTN usage records in Lync Server 2013](modify-a-voice-policy-and-configure-pstn-usage-records.md)

