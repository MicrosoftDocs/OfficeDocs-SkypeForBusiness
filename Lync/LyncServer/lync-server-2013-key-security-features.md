---
title: 'Lync Server 2013: Key security features'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Key security features in Lync Server 2013
ms:assetid: bf2a3b8f-73c6-47e1-8c9e-ca1dc1a502bf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn342829(v=OCS.15)
ms:contentKeyID: 56107266
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Key security features in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-18_

Lync Server 2013 includes several security features, including server-to-server authentication, role-based access control, and centralized storage of configuration data.

This article provides a high level overview of Lync Server 2013 security.

<div>

## Key Security Features in Lync Server 2013

Security is a very broad topic. Security reaches across every feature of Lync Server 2013 as well as databases, services, and hardware that make up a Lync ecosystem. This article outlines some of the features in Lync Server 2013 in particular that are designed for security.

<div>

## Planning and Design Tools

Lync Server 2013 provides two tools to facilitate planning and design and to reduce the chance of misconfiguring Lync Server components.

  - **Topology Planning Tool** automates much of the topology design process. You can export the results from the Planning Tool to Topology Builder, which is the tool that is required to install each server running Lync Server 2013.

  - **Topology Builder** stores all configuration information in the Central Management store.

For details about these tools, see [Planning for Lync Server 2013](lync-server-2013-planning.md).

</div>

<div>

## Central Management Store

In Lync Server 2013, configuration data about servers and services is part of the Central Management store. The Central Management store provides a robust, schematized storage of the data needed to define, set up, maintain, administer, describe, and operate a Lync Server deployment. It also validates the data to ensure configuration consistency. All changes to this configuration data happen at the Central Management store, eliminating “out-of-sync” issues.

Read-only copies of the data are replicated to all servers in the topology, including Edge Servers and Survivable Branch Appliances. Replication is managed by a service that is, by default, run under the context of the Network service, reducing the rights and permissions to that of a simple user on the computer.

</div>

<div>

## Server-to-Server Authentication

In Lync Server 2013, authentication can be configured between servers by using the Open Authorization (OAuth) protocol. For example, you can configure Lync Server 2013 to authenticate with a server that is running Exchange Server 2013. Using the OAuth protocol, the Lync server and the Exchange server can trust each other. This provides the ability to integrate the products in a seamless manner. For details, see [Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)

</div>

<div>

## Windows PowerShell-based management and Web-based Management Interface

Lync Server 2013 provides a powerful management interface, built on the Windows PowerShell command-line interface. It includes cmdlets for managing security, and Windows PowerShell security features are enabled by default so that users cannot easily or unknowingly run scripts. This means that the software defaults are set to automatically help maximize security and reduce the avenues of attack. For details about Windows PowerShell management support in Lync Server 2013, see [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md).

</div>

<div>

## Role-Based Access Control (RBAC)

Microsoft Lync Server 2013 provides role-based access control (RBAC) to enable you to delegate administrative tasks while maintaining high standards for security. You can use RBAC to follow the principle of "least privilege," in which users are given only the administrative rights that their jobs require. Lync Server 2013 introduces the ability to create a new role and also the ability to modify an existing role. For details, see [Planning for role-based access control in Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md).

</div>

</div>

<div>

## Network Address Translation (NAT)

Lync Server 2013 does not support the use of network address translation (NAT) on the internal interface of the Edge Server, but it does support placing the external interface of the Access Edge service, Web Conferencing Edge service, and A/V Edge service behind a router or firewall that performs network address translation (NAT) for both single and scaled consolidated Edge Server topologies. Multiple Edge Servers behind a hardware load balancer cannot use NAT. If multiple Edge Servers use NAT on their external interfaces, Domain Name System (DNS) load balancing is required. In turn, using DNS load balancing allows you to reduce the number of public IP addresses per Edge Server in an Edge Server pool. For details, see[Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md).

<div>


> [!NOTE]  
> If you federate with enterprises that have a Microsoft Office Communications Server 2007 deployment and you need to use audio/video between your enterprise and the federated enterprise, the port requirements will be those for the older version of the Edge Servers that are deployed. For example, the port ranges required for those older versions must be opened for both enterprises until the federated partner upgrades its Edge Servers to Lync Server 2013. At that time, the port requirements can be reviewed and reduced according to the new configuration.



</div>

</div>

<div>

## Simplified Certificates for Edge Servers

The Deployment Wizard can automatically populate subject names (SNs) and subject alternative names (SANs), reducing the possibility of including unnecessary and potentially unsecure entries.

</div>

<div>

## Trustworthy Computing Security Development Lifecycle (SDL)

Lync Server 2013 is designed and developed in compliance with the Microsoft Trustworthy Computing Security Development Lifecycle (SDL), which is described at <http://go.microsoft.com/fwlink/?linkid=68761>.

  - **Trustworthy by Design**   The first step in creating a more secure unified communications system was to design threat models and test each feature as it was designed. In addition, Microsoft performs testing outside of the designed behavior in order to find security vulnerabilities resulting from unexpected product behavior. Multiple security-related improvements were built into the coding process and practices. Build-time tools detect buffer overruns and other potential security threats before the code is checked in to the final product. Of course, it is impossible to design against all unknown security threats. No system can guarantee complete security. However, because product development embraced secure design principles from the start, Lync Server 2013 incorporates industry standard security technologies as a fundamental part of its architecture.

  - **Trustworthy by Default**   By default, network communications in Lync Server 2013 are encrypted. Because all servers use certificates and Kerberos authentication, TLS, Secure Real-Time Transport Protocol (SRTP), and other industry-standard encryption techniques, including 128-bit Advanced Encryption Standard (AES) encryption, virtually all Lync Server data is protected on the network. In addition, role-based access control makes it possible to deploy servers running Lync Server 2013 so that each server role runs only the services, and has only the permissions related to those services, that are appropriate for the server role.

  - **Trustworthy by Deployment**   All Lync Server 2013 documentation includes best practices and recommendations to help you determine and configure the optimal security levels for your deployment and assess the security risks of activating non-default options.

</div>

</div>

<span> </span>

</div>

</div>

</div>

