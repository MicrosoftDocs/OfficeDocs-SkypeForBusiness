---
title: "Test SIP trunk configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: c8712308-0e2d-4e39-8f90-d1a250487a94
description: "Summary: Learn how to test SIP trunk configuration settings by using the Skype for Business Server Management Shell."
---

# Test SIP trunk configuration settings in Skype for Business Server
 
**Summary:** Learn how to test SIP trunk configuration settings by using the Skype for Business Server Management Shell.
  
SIP trunk configuration settings define the relationship and capabilities between a Mediation Server and the Public Switched Telephone Network (PSTN) gateway, an IP-Public Branch eXchange (PBX), or a Session Border Controller (SBC) at the service provider. These settings do such things as specify:
  
- Whether media bypass should be enabled on the trunks.
    
- The conditions under which Realtime Transport Control Protocol (RTCP) packets are sent.
    
- Whether or not Secure Realtime Transport Protocol (SRTP) encryption is required on each trunk.
    
When you install Skype for Business Server, a global collection of SIP trunk configuration settings is created for you. In addition, administrators can create custom setting collections at the site scope or at the service scope (for the PSTN gateway service, only). Administrators can also use the Test-CsTrunkConfiguration cmdlet to verify that a trunk can convert a number as dialed by a user to a number that can be handled by the gateway.
  
Trunk configuration settings can only be tested by using Windows PowerShell and the [Test-CsTrunkConfiguration](https://docs.microsoft.com/powershell/module/skype/test-cstrunkconfiguration?view=skype-ps) cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Skype for Business Server Management Shell.
  
### To test SIP trunk configuration settings

- This command verifies that the trunk configuration settings for the Redmond site can correctly convert the dialed number 4255551212.
    
  ```
  $trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"
  Test-CsTrunkConfiguration -DialedNumber 4255551212 -TrunkConfiguration $trunk
  ```


