---
title: "Enable or disable a conferencing device in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d5140e38-d015-4706-9bde-cf2fa748c36b
description: "Enable and disable a conferencing device by using the Enable-CsMeetingRoom cmdlet and the Disable-CsMeetingRoom cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell."
---

# Enable or disable a conferencing device in Lync Server 2013
[]
Enable and disable a conferencing device by using the **Enable-CsMeetingRoom** cmdlet and the **Disable-CsMeetingRoom** cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
## 

### Enabling a Conferencing Device

- To enable a conferencing device, use the **Enable-CsMeetingRoom** cmdlet. When enabling a conferencing device, you must include a) the conferencing device identity, b) the Registrar pool where the room account will be homed, and c) the SIP address to be assigned to that account. 
    
  ```
  Enable-CsMeetingRoom -Identity "Redmond Conferencing device" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:RedmondMeetingRoom@litwareinc.com"
  ```

### Disabling a Conferencing Device

- To disable a conferencing device, use the **Disable-CsMeetingRoom** cmdlet. Make sure that you specify the identity of the conferencing device to be disabled: 
    
  ```
  Disable-CsMeetingRoom -Identity "sip:RedmondMeetingRoom@litwareinc.com"
  ```

For details, see the Help topics for the [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet and the [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet. 
  

