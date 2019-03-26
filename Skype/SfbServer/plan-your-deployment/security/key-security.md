---
title: "Key security features in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: bf2a3b8f-73c6-47e1-8c9e-ca1dc1a502bf
description: "Skype for Business Server includes several security features, including server-to-server authentication, role-based access control, and centralized storage of configuration data."
---

# Key security features in Skype for Business Server
 
Skype for Business Server includes several security features, including server-to-server authentication, role-based access control, and centralized storage of configuration data. 
  
This article provides a high level overview of Skype for Business Server security. 
  
## Key Security Features in Skype for Business Server

Security is a very broad topic. Security reaches across every feature of Skype for Business Server as well as databases, services, and hardware that make up a Skype for Business Server ecosystem. This article outlines some of the features in Skype for Business Server in particular that are designed for security.
  
### Planning and Design Tools

Skype for Business Server provides two tools to facilitate planning and design and to reduce the chance of mis-configuring Skype for Business Server components. 
  
- **Topology Planning Tool** automates much of the topology design process. You can export the results from the Planning Tool to Topology Builder, which is the tool that is required to install each server running Skype for Business Server.
    
- **Topology Builder** stores all configuration information in the Central Management store.
    
For details about these tools, see [Skype for Business Server Management Tools](../../management-tools/management-tools.md).
  
### Central Management Store

In Skype for Business Server, configuration data about servers and services is part of the Central Management store. The Central Management store provides a robust, schematized storage of the data needed to define, set up, maintain, administer, describe, and operate a Skype for Business Server deployment. It also validates the data to ensure configuration consistency. All changes to this configuration data happen at the Central Management store, eliminating "out-of-sync" issues. 
  
Read-only copies of the data are replicated to all servers in the topology, including Edge Servers and Survivable Branch Appliances. Replication is managed by a service that is, by default, run under the context of the Network service, reducing the rights and permissions to that of a simple user on the computer. 
  
### Server-to-Server Authentication

In Skype for Business Server, authentication can be configured between servers by using the Open Authorization (OAuth) protocol. For example, you can configure Skype for Business Server to authenticate with a server that is running Microsoft Exchange Server 2016. Using the OAuth protocol, the Skype for Business Server and the Microsoft Exchange Server can trust each other. This provides the ability to integrate the products in a seamless manner. For details, see [Manage server-to-server authentication (OAuth) and partner applications in Skype for Business Server](../../manage/authentication/server-to-server-and-partner-applications.md).
  
### Windows PowerShell-based management and Web-based Management Interface

Skype for Business Server provides a powerful management interface, built on the Windows PowerShell command-line interface. It includes cmdlets for managing security, and Windows PowerShell security features are enabled by default so that users cannot easily or unknowingly run scripts. This means that the software defaults are set to automatically help maximize security and reduce the avenues of attack. For details about Windows PowerShell management support in Skype for Business Server, see [Skype for Business Server Management Shell](../../manage/management-shell.md). 
  
### Role-Based Access Control (RBAC)

Skype for Business Server provides role-based access control (RBAC) to enable you to delegate administrative tasks while maintaining high standards for security. You can use RBAC to follow the principle of "least privilege," in which users are given only the administrative rights that their jobs require. Skype for Business Server provides the ability to create a new role and also the ability to modify an existing role. 
  
## Network Address Translation (NAT)

Skype for Business Server does not support the use of network address translation (NAT) on the internal interface of the Edge Server, but it does support placing the external interface of the Access Edge service, Web Conferencing Edge service, and A/V Edge service behind a router or firewall that performs network address translation (NAT) for both single and scaled consolidated Edge Server topologies. Multiple Edge Servers behind a hardware load balancer cannot use NAT. If multiple Edge Servers use NAT on their external interfaces, Domain Name System (DNS) load balancing is required. In turn, using DNS load balancing allows you to reduce the number of public IP addresses per Edge Server in an Edge Server pool. For details, see [Edge Server scenarios in Skype for Business Server](../../plan-your-deployment/edge-server-deployments/scenarios.md).
  
> [!NOTE]
> If you federate with enterprises that have a Microsoft Office Communications Server 2007 deployment and you need to use audio/video between your enterprise and the federated enterprise, the port requirements will be those for the older version of the Edge Servers that are deployed. For example, the port ranges required for those older versions must be opened for both enterprises until the federated partner upgrades its Edge Servers to Skype for Business Server. At that time, the port requirements can be reviewed and reduced according to the new configuration. 
  
## Simplified Certificates for Edge Servers

The Deployment Wizard can automatically populate subject names (SNs) and subject alternative names (SANs), reducing the possibility of including unnecessary and potentially unsecure entries.
  
## Trustworthy Computing Security Development Lifecycle (SDL)

Skype for Business Server is designed and developed in compliance with the [Microsoft Trustworthy Computing Security Development Lifecycle](https://go.microsoft.com/fwlink/p/?linkid=68761) (SDL).
  
- **Trustworthy by Design** The first step in creating a more secure unified communications system was to design threat models and test each feature as it was designed. In addition, Microsoft performs testing outside of the designed behavior in order to find security vulnerabilities resulting from unexpected product behavior. Multiple security-related improvements were built into the coding process and practices. Build-time tools detect buffer overruns and other potential security threats before the code is checked in to the final product. Of course, it is impossible to design against all unknown security threats. No system can guarantee complete security. However, because product development embraced secure design principles from the start, Skype for Business Server incorporates industry standard security technologies as a fundamental part of its architecture.
    
- **Trustworthy by Default** By default, network communications in Skype for Business Server are encrypted. Because all servers use certificates and Kerberos authentication, TLS, Secure Real-Time Transport Protocol (SRTP), and other industry-standard encryption techniques, including 128-bit Advanced Encryption Standard (AES) encryption, virtually all Skype for Business Server data is protected on the network. In addition, role-based access control makes it possible to deploy servers running Skype for Business Server so that each server role runs only the services, and has only the permissions related to those services, that are appropriate for the server role.
    
- **Trustworthy by Deployment** All Skype for Business Server documentation includes best practices and recommendations to help you determine and configure the optimal security levels for your deployment and assess the security risks of activating non-default options.
    

