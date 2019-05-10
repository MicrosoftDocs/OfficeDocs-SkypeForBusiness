---
title: 'Lync Server 2013: Beginning the planning process'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Beginning the planning process
ms:assetid: df3722b3-f859-49e1-b3ff-ee6863483731
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398986(v=OCS.15)
ms:contentKeyID: 48185618
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Beginning the planning process for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-24_

While planning an on-premises unified communications deployment may seem intimidating, Lync Server provides two valuable tools to help you:

  - **The Planning Tool** is a wizard that presents a series of questions about your organization, the Lync Server features that you want to enable, and your capacity planning needs. It then creates a recommended deployment topology based on your answers, and produces a Microsoft Visio diagram of this deployment.

  - **Topology Builder** is an installation component of Lync Server. You use Topology Builder to create, adjust, and publish your planned topology. It also validates your topology before you begin server installations. When you install Lync Server on individual servers, the servers read the published topology as part of the installation process, and the installation program deploys the server as directed in the topology.

<div>

## Lync Server Planning Tool

The Planning Tool takes your answers to the questions in the tool and generates a topology based on Lync Server guidelines and best practices. It also provides several views of a deployment based on your answers. It shows both a global view of all your sites (that is, including both central sites and branch sites), and detailed views showing the servers and other components at each site.

Running the Planning Tool does not commit you to any specific deployment or initiate any processes. In fact, running the Planning Tool even before you have a firm plan in mind can be a very instructive way to understand the kinds of questions you need to think about in your planning process.

You can run the Planning Tool multiple times, answering questions differently, and compare the outcomes. If you have a design you are mostly satisfied with but that you need to make changes to, you can return to the Planning Tool, load the design, and make the changes. It takes about 15 minutes to complete the Planning Tool once.

After you are satisfied, you can use the Planning Tool to create a diagram of your planned deployment. You can use this diagram while creating the deployment in Topology Builder.

<div>


> [!NOTE]  
> The Planning Tool included with this release of Lync Server 2013 is a prerelease version. Note that the capacity planning numbers in the Planning Tool are preliminary and are not supported for the final release.



</div>

</div>

<div>

## Lync Server Topology Builder

Once you have decided on your deployment plan, you use Topology Builder to begin deploying. When finished, you use Topology Builder to validate the topology, and then, if it passes, you can publish the topology. When you publish the topology, Lync Server puts the topology into the Central Management store, which is created at this time if it does not already exist. When you install Lync Server on each server in your deployment, the server reads the topology from the Central Management store and installs itself to fit into its role in your deployment.

Alternatively, if you are very familiar with Lync Server and need less prescriptive guidance, you can skip the Planning Tool and use the wizards in Topology Builder for the initial design of your deployment and also for the validation and publishing steps.

Using Topology Builder to plan and publish a topology is a required step. You cannot bypass Topology Builder and install Lync Server individually on the servers in your deployment. Each server must read the topology from a validated, published topology in the Central Management store.

</div>

<div>

## High-Level Planning Process

We recommend the following general process for using both the documentation and the Planning Tool to plan your Lync Server deployment.

1.  If you are familiar with previous versions of Lync Server, read [New features in Lync Server 2013](lync-server-2013-new-features.md) to familiarize yourself with the new features and requirements in Lync Server 2013.

2.  Read the other topics in this section of the documentation: [Topology basics you must know before planning for Lync Server 2013](lync-server-2013-topology-basics-you-must-know-before-planning.md), [Reference topologies in Lync Server 2013](lync-server-2013-reference-topologies.md), [Initial planning decisions for Lync Server 2013](lync-server-2013-initial-planning-decisions.md), and [Clients for Lync Server 2013](lync-server-2013-clients.md). Note the planning decisions represented in [Reference topologies in Lync Server 2013](lync-server-2013-reference-topologies.md).

3.  Now that you are more familiar with Lync Server features and the kinds of questions that must be answered, run the Planning Tool and view the resulting topology and its details. Make sure that the topology fits the unique requirements for your organization.

4.  If there are particular workloads or features you are interested in or need to learn about, read the appropriate sections of [Planning for Lync Server 2013](lync-server-2013-planning.md).

5.  Run the Planning Tool again. You can start with the deployment you created in step 3 and modify the results, or start over from the beginning.
    
    If needed, run the Planning Tool a third time and repeat until you are satisfied with the output.

6.  When you have finalized the topology plan, use Planning Tool to create and print a Visio diagram of your topology. You can use this printout while working with Topology Builder to input your topology.

7.  Before you begin deployment, read [Determining your system requirements for Lync Server 2013](lync-server-2013-determining-your-system-requirements.md) and [Determining your infrastructure requirements for Lync Server 2013](lync-server-2013-determining-your-infrastructure-requirements.md) to familiarize yourself with the prerequisites and necessary infrastructure for Lync Server. Additionally, be sure you have read all the sections of [Planning for Lync Server 2013](lync-server-2013-planning.md) that apply to the workloads and features that you plan to deploy.

</div>

<div>

## Migrating from Previous Versions

If you are migrating to Lync Server from a previous version, see the [Migration](migration.md) documentation for specific instructions for your migration and deployment.

</div>

</div>

<span> </span>

</div>

</div>

</div>

