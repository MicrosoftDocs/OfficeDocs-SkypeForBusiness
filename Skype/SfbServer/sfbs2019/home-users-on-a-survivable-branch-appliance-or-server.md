---
title: "Home users on a Survivable Branch Appliance or Server in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/10/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: faf1ebb9-6d7d-4a58-8ff7-801b7b31d3ba
description: "The process of homing users on a Survivable Branch Appliance or a Survivable Branch Server is similar to the process of homing users on a Front End pool. Perform the Survivable Branch Appliance or Survivable Branch Server procedure at the central site."
---

# Home users on a Survivable Branch Appliance or Server in Lync Server 2013
[]
The process of homing users on a Survivable Branch Appliance or a Survivable Branch Server is similar to the process of homing users on a Front End pool. Perform the Survivable Branch Appliance or Survivable Branch Server procedure at the central site.
  
### To home users on Survivable Branch Appliance or Survivable Branch Server

1. Before moving users to the Survivable Branch Server or Survivable Branch Server, open the Lync Server Management Shell, and then do all of the following:
    
  - Run the cmdlet **Test-CsPstnOutboundCall** to verify that the Survivable Branch Server is running and that the public switched telephone network (PSTN) connectivity is configured. If you need to modify PSTN gateway properties, use the cmdlet **Set-CsPstnGateway**. 
    
  - Run the cmdlet **Get-CsVoicePolicy** to verify that the users who will be homed on the Survivable Branch Server have the appropriate VoIP routing policy. If you need to modify the VoIP policy, use the cmdlet **Set-CsVoicePolicy**. 
    
  - Run the cmdlet **Get-CsVoicemailReroutingConfiguration** to verify that the voice mail rerouting settings are configured. If you need to modify the voice mail rerouting settings, use the cmdlet **Set-CsVoicemailReroutingConfiguration**. 
    
2. In the Lync Server Management Shell, run the cmdlet **Move-CsUser** to move home users. 
    
> [!NOTE]
> You can also use Lync Server Control Panel to verify prerequisites and home users. 
  
> [!NOTE]
> Users who are homed on a Lync Server Survivable Branch Appliance are unable to create new chat rooms or view the room card for existing rooms. 
  
## See also

#### 

[Test-CsPstnOutboundCall](test-cspstnoutboundcall.md)
  
[Get-CsVoicePolicy](get-csvoicepolicy.md)
  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)
  
[Move-CsUser](move-csuser.md)

