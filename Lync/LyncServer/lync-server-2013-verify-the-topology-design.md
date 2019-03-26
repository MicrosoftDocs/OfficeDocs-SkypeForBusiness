---
title: 'Lync Server 2013: Verify the topology design'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Verify the topology design
ms:assetid: c1b61814-239e-4101-aab0-de3db1d8793c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412951(v=OCS.15)
ms:contentKeyID: 48185311
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Verify the topology design in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-01-02_

Topology Builder automatically verifies the topology. Any topology error is identified as a validation error, indicated by the validation error icon next to the server role. It is important to also verify that the topology correctly represents the topology for your deployment.

<div>

## To verify the topology prior to publication

1.  Check that all simple URLs are configured correctly.

2.  Confirm that the SQL Server-based server is online and available to the computer where Topology Builder is installed, including any necessary firewall rules.

3.  Confirm that the file share is available and has the proper permissions defined.

4.  Confirm that the correct server roles that meet the deployment requirements are defined in the topology.

5.  Verify that the servers exist in Active Directory Domain Services. This will happen automatically if you have joined the servers to the domain.

When you have verified the topology and there are no validation errors, you should be ready to publish the topology. If there are validation errors, you must correct these before you can publish the topology. For details about publishing your topology, see [Publish the topology in Lync Server 2013](lync-server-2013-publish-the-topology.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

