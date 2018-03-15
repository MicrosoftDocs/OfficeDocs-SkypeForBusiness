---
title: "Configure voice mail rerouting settings in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7ab6be28-eabb-4a79-a796-648887d71b83
description: "Survivable Branch Appliances and Survivable Branch Servers can provide voice mail survivability for branch users during a WAN outage, if Exchange Unified Messaging (UM) is installed at the central site and an Exchange UM Message Auto Attendant (AA) is deployed. We recommend that your Exchange administrator configure the AA to accept messages only, which disables other generic functionality, such as transfer to a user or transfer to an operator. Alternatively, you might use a generic AA or an AA customized to route the call."
---

# Configure voice mail rerouting settings in Lync Server 2013
[]
Survivable Branch Appliances and Survivable Branch Servers can provide voice mail survivability for branch users during a WAN outage, if Exchange Unified Messaging (UM) is installed at the central site and an Exchange UM Message Auto Attendant (AA) is deployed. We recommend that your Exchange administrator configure the AA to accept messages only, which disables other generic functionality, such as transfer to a user or transfer to an operator. Alternatively, you might use a generic AA or an AA customized to route the call. 
  
For details, see the "Preparing for Voice Mail Survivability" section of [Branch-site resiliency requirements for Lync Server 2013](branch-site-resiliency-requirements.md) in the Planning documentation. 
  
### To configure voice mail survivability

1. Ask your Exchange administrator to configure the AA to accept messages only (in the Exchange Shell use the following cmdlet: **Set-UMAutoAttendant \<AA name\> -CallSomeoneEnabled $false**. The parameter that specifies to allow leaving messages (  _SendVoiceMsgEnabled_) is true by default. 
    
2. In the Lync Server Management Shell, use the **New-CSVoiceMailReroutingConfiguration** cmdlet to set the AA phone number as the Exchange UM Auto Attendant phone number in the voice mail rerouting configuration on the Survivable Branch Appliance or Survivable Branch Server. 
    
    > [!NOTE]
    > If you need to modify the voice mail rerouting setting later, use the **Set-CsVoiceMailReRoutingConfiguration** cmdlet to do so. For details, about **New-** and **Set-CSVoiceMailReroutingConfiguration**, in the Shell Help topics. 
  
3. Set the Exchange UM subscriber access number that corresponds to the branch user's Exchange UM dial plan as the Exchange UM subscriber access number in the voice mail rerouting configuration on the Survivable Branch Appliance or Survivable Branch Server. 
    
    > [!NOTE]
    > Configure the Exchange UM users' dial plan so that there is only one dial plan associated with all branch users who need access to the Get Voice Mail functionality during a WAN outage. 
  
 **Next step** for Survivable Branch Appliances or Survivable Branch Servers: [Home users on a Survivable Branch Appliance or Server in Lync Server 2013](home-users-on-a-survivable-branch-appliance-or-server.md).

