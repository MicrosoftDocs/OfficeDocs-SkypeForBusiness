---
title: Configure Lync Server 2013 Scenarios
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure Lync Server 2013 Scenarios
ms:assetid: 6705346b-1512-4af3-85e4-64dfa6ee6f80
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945596(v=OCS.15)
ms:contentKeyID: 51541420
ms.date: 12/28/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure Lync Server 2013 Scenarios

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-12-28_

To run the Lync Server 2013 Stress and Performance Tool (LyncPerfTool), the Lync Server 2013 topology must first be configured for the scenarios that will be executed. If Lync Server 2013 is not configured or is configured incorrectly, load simulation will fail in most cases. With the Lync Server 2013 Stress and Performance Tool, we have provided example Lync Server Management Shell scripts and basic resource files that can be used as a starting point for configuring Lync Server 2013. This topic describes the Windows PowerShell examples provided. Note that it is not the goal of this topic to describe how to configure Lync Server 2013 in general. For details about working with Windows PowerShell in Lync Server 2013, see the Lync Server Management Shell documentation at <https://technet.microsoft.com/en-us/library/gg398474.aspx>.

<div>

## About Running Lync Server Management Shell Scripts

We have provided example Lync Server Management Shell scripts that may be used in preparation for running load simulation. Because the scripts are intended for load simulation, they are simple and permissive, and therefore may not be appropriate for production. All scripts are examples and must be reviewed, and, in some cases, modified to reflect your topology. At a minimum, we expect that the Response Group Service (RGS) scenario would need to be modified to specify the agents that are assigned to the agent groups. However, you have the option to not simulate this load.

<div>


> [!WARNING]  
> Take care in reviewing and understanding the examples provided. Scripts will overwrite any existing settings in the topology.



</div>

<div>


> [!NOTE]  
> For details about using Windows PowerShell and the Lync Server Management Shell, see the Lync Server 2013 Windows PowerShell Blog at <A href="https://go.microsoft.com/fwlink/?linkid=203150">https://go.microsoft.com/fwlink/?LinkId=203150</A>.



</div>

</div>

<div>

## Stress and Performance Tool Client Version Monikers

You may need to configure the Client Version Check policy if you have changed the settings from the default values. For details, see “Configuring supported client versions” at <https://technet.microsoft.com/en-us/library/gg412832(v=ocs.15).aspx>. The Lync Server 2013 Stress and Performance Tool uses the following User Agent Versions by default when communicating with Lync Server 2013:

  - LSPT/15.0.0.0 (Lync Server 2013 Stress and Performance Tool)

  - OCPHONE/.0.522

These are for the Mobility (UCWA) client in LyncPerfTool:

  - Ucwa Perf Tool/Web Conference

  - Ucwa Perf Tool/Mobile

</div>

</div>

<span> </span>

</div>

</div>

</div>

