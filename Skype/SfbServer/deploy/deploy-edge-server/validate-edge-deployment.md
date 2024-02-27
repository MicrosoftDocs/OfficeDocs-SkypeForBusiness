---
ms.date: 03/17/2018
title: "Validate your Edge deployment in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
audience: ITPro
manager: serdars
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 69837f86-d141-4884-a4ca-c7e7463afaad
description: "Summary: Learn how to verify that your deployment of Microsoft Edge Server or Microsoft Edge Server pool is working in Skype for Business Server."
---

# Validate your Edge deployment in Skype for Business Server
 
**Summary:** Learn how to verify that your deployment of Microsoft Edge Server or Microsoft Edge Server pool is working in Skype for Business Server.
  
Once you deploy your Microsoft Edge Server or Microsoft Edge Server pool, you need to know if it's working properly. Here are a couple of things that can help with confirming your Edge environment is connected to your internal servers, and also that your external users can connect to your Skype for Business Server environment through your Edge.
  
## Verify connectivity between your internal servers and your Edge servers

While validation of connectivity is done automatically in Edge Server or Edge Server pool when the Edge Servers are installed, you can still confirm this for yourself with Windows PowerShell. Run the Get-CsManagementStoreReplicationStatus cmdlet on the internal server, which has the Central Management store, or any domain joined computer on which Skype for Business Server Core Components (OcsCore.msi) are installed.
  
The initial result of running this command might give a False status, rather than True, for replication. If that happens run the Invoke-CsManagementStoreReplication cmdlet. Give it some time to complete the replication, and then run the Get-CsManagementStoreReplicationStatus cmdlet again.
  
## Verify connectivity for your external users

We do have a great tool for confirming your Edge Server configuration, and the ability to connect, send, and receive the correct messages for Edge Server scenarios. It's the [Remote Connectivity Anaylzer site](https://testconnectivity.microsoft.com/). This site is managed and maintained by Microsoft Support. To use this tool, browse to the website and follow the instructions to choose the right scenario for you.
  
### Things to consider when testing external user connectivity

Any test for external user access needs to include each type of internal user your organization supports, which could include any or all of the following:
  
- Users from at least one federated domain (we do recommend testing them all though).
    
- Anonymous users.
    
- Users in your organization who are logged into Skype for Business remotely, but aren't using VPN.
    
These tests determine whether your Microsoft Edge Server is:
  
- Listening on the necessary ports by using a telnet client from outside your network.
    
  - For example: telnet sip.contoso.com 443
    
  - You should perform the preceding test on the ports you're using on your Edge Server or Edge Server pool, depending on your deployment.
    
- Performing accurate external DNS resolution.
    
  - From outside your network, ping each of the external FQDNs of your Microsoft Edge Server or Microsoft Edge Server pool. Even if the ping fails, you see the IP addresses, with which you can compare the IP addresses you previously assigned.
    


