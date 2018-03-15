---
title: "Move a conferencing device to a new Registrar pool in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26e02ca3-e881-4f90-8bf0-b13649108100
description: "Move a conferencing device from one Registrar pool to another by using the Move-CsMeetingRoom cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell."
---

# Move a conferencing device to a new Registrar pool in Lync Server 2013
[]
Move a conferencing device from one Registrar pool to another by using the **Move-CsMeetingRoom** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
## 

### Moving a Conferencing Device to a New Registrar Pool

- To move a conferencing device, you must specify the identity of the room to be moved, and then set the Target parameter to the fully qualified domain name (FQDN) of the Registrar pool the device will be moved to. For example:
    
  ```
  Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com" -Identity "Room 14"
  ```

For details, see the Help topic for the [Move-CsMeetingRoom](move-csmeetingroom.md) cmdlet. 
  

