---
title: "Verify connectivity for external users in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5c02bd6e-1c96-448a-a21d-58c9961c6640
description: "Validating connectivity for external users requires ensuring connectivity from users to the server and port for the Access Edge service."
---

# Verify connectivity for external users in Lync Server 2013
[]
Validating connectivity for external users requires ensuring connectivity from users to the server and port for the Access Edge service.
  
A valuable resource for confirming your configuration and the ability to connect, send and receive the correct messages for the scenarios that external user access requires is the Remote Connectivity Analyzer site ([http://www.testocsconnectivity.com](http://www.testocsconnectivity.com)). The site is managed and maintained by Microsoft Support. To reach the Remote Connectivity Analyzer, open the Web site in a browser and follow the instructions to select the scenario.
  
## Test Connectivity of External Users and External access

Tests for external user access should include each type of external user that your organization supports, including any or all of the following:
  
- Users from at least one federated domain, and test IM, presence, A/V and desktop sharing.
    
- Users of each public IM service provider that your organization supports (and for which provisioning has been completed).
    
- Anonymous users.
    
- Users within your organization who are logged into Lync remotely, but not using VPN.
    
These tests determine whether your Edge Server is:
  
- Listening on the necessary ports by using a telnet client from outside your network.
    
  - Example: telnet sip.contoso.com 443
    
  - Perform the preceding test on ports you are using on the Edge Server or Edge Server pool depending on your deployment.
    
- Performing accurate external DNS resolution.
    
  - From outside your network ping each of the external FQDN's of your Edge or Edge pool. Even if the ping fails you will see the IP addresses, which you can compare to the ones you have assigned. 
    

