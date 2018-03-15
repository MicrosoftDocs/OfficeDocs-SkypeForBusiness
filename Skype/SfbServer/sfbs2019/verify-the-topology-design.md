---
title: "Verify the topology design in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c1b61814-239e-4101-aab0-de3db1d8793c
description: "Topology Builder automatically verifies the topology. Any topology error is identified as a validation error, indicated by the validation error icon next to the server role. It is important to also verify that the topology correctly represents the topology for your deployment."
---

# Verify the topology design in Lync Server 2013
[]
Topology Builder automatically verifies the topology. Any topology error is identified as a validation error, indicated by the validation error icon next to the server role. It is important to also verify that the topology correctly represents the topology for your deployment.
  
### To verify the topology prior to publication

1. Check that all simple URLs are configured correctly.
    
2. Confirm that the SQL Server-based server is online and available to the computer where Topology Builder is installed, including any necessary firewall rules.
    
3. Confirm that the file share is available and has the proper permissions defined.
    
4. Confirm that the correct server roles that meet the deployment requirements are defined in the topology.
    
5. Verify that the servers exist in Active Directory Domain Services. This will happen automatically if you have joined the servers to the domain.
    
When you have verified the topology and there are no validation errors, you should be ready to publish the topology. If there are validation errors, you must correct these before you can publish the topology. For details about publishing your topology, see [Publish the topology in Lync Server 2013](publish-the-topology.md).

