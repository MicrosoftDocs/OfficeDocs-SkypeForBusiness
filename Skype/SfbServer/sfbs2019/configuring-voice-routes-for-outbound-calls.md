---
title: "Configuring voice routes for outbound calls in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c182cdd-7a4a-4a9d-bdac-4199f0abd947
description: "A Lync Server 2013 voice route associates destination phone numbers with one or more public switched telephone network (PSTN) gateways or SIP trunks and one or more PSTN usage records."
---

# Configuring voice routes for outbound calls in Lync Server 2013
[]
A Lync Server 2013 voice route associates destination phone numbers with one or more public switched telephone network (PSTN) gateways or SIP trunks and one or more PSTN usage records.
  
### To view voice routes by using Lync Server Control Panel

1. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
2. Click **Voice Routing**. 
    
3. Click **Route**.
    
4. Double-click a voice route to view additional properties from the list of voice routes, or select the route and click **Edit**. Then click **Show details**. 
    
    > [!NOTE]
    > You can only view detailed information for a single route at a time. 
  
### To view voice routes by using Windows PowerShell

- Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**. Voice routes can be viewed by using Windows PowerShell and the **Get-CsVoiceRoute** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
    
    To view information about all of your voice routes, type the following command in the Lync Server Management Shell, and then press ENTER:
    
  ```
  Get-CsVoiceRoute
  ```

    That will return information similar to this:
    
  ```
  Identity          : global
  Priority          : -1
  Description       :
  NumberPattern     : ^(\+1[0-9]{10})$
  PstnUsages        : {}
  PstnGatewayList   : {}
  Name              : global
  SuppressCallerId  :
  AlternateCallerId :
  
  ```

> [!NOTE]
> For details, see [Voice routes in Lync Server 2013](voice-routes.md) in the Planning documentation. 
  
## In this section

- [Create a voice route in Lync Server 2013](create-a-voice-route.md)
    
- [Modify a voice route in Lync Server 2013](modify-a-voice-route.md)
    
## See also

#### 

[Managing voice routing in Lync Server 2013](managing-voice-routing.md)

