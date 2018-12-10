---
title: "Skype for Business hybrid solutions"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 5/18/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "A Discussion of the available hybrid solutions in Skype for Business Server 2019."
---

NOTE: THE FOLLOWING IS COPIED FROM 2015 AND IS IN PROGRESS. Additional in-progress placeholder content can be found [below](#placeholder-topic-for-hybrid-solutions).


# Skype for Business hybrid solutions

Find information on planning a Skype for Business hybrid deployment. 
  
This topic introduces you to several hybrid configurations to help you determine which configuration is best for your business. You can then read more about the configuration you're interested in by following the links in this topic. This topic contains the following sections:
  
- [Skype for Business hybrid configurations](hybrid-solutions.md#BKMK_HybridConfigurations)
    
- [Add Skype for Business Online into your existing on-premises Skype for Business environment](hybrid-solutions.md#BKMK_HybridConnectivity)
    
- [Take advantage of Phone System in Office 365 (Cloud PBX)](hybrid-solutions.md#BKMK_CloudPBX)
    
- [Integrate with Exchange and SharePoint](hybrid-solutions.md#BKMK_IntegratewExchangeSharePoint)
    
- [Tasks for planning and configuring a hybrid environment](hybrid-solutions.md#BKMK_Tasks)
    
- [For more information](hybrid-solutions.md#BKMK_MoreInfo)
    
## Skype for Business hybrid configurations
<a name="BKMK_HybridConfigurations"> </a>

Skype for Business supports several hybrid configurations. You can add Skype for Business Online into your existing on-premises Skype for Business environment, integrate your Skype for Business deployment with Exchange Online and SharePoint Online, and take advantage of Phone System in Office 365 (Cloud PBX)—Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud with Skype for Business Online. 
  
With a Skype for Business hybrid deployment, you combine a Skype for Business Online subscription with your on-premises Skype for Business offering. You can start building software-as-a-service management skills in your organization, and move your Skype for Business users to the cloud at your own pace. Your users who are homed in the cloud can take advantage of Phone System in Office 365 while retaining your on-premises Public Switched Telephone Network (PSTN) connectivity.
  
With a Skype for Business hybrid configuration, keep the following in mind:
  
- Some users might be homed on premises and some online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.
    
- You can migrate users from Skype for Business on premises to Skype for Business Online over time, on your schedule.
    
- You can integrate with other Microsoft Office 365 applications, including Exchange Online and SharePoint Online.
    
- You can integrate with Exchange and SharePoint.
    
- You can take advantage of Skype Meeting Broadcast.
    
- You can take advantage of PSTN conferencing.
    
## Add Skype for Business Online into your existing on-premises Skype for Business environment
<a name="BKMK_HybridConnectivity"> </a>

Hybrid connectivity between Skype for Business Server and Skype for Business Online means users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Skype for Business Online. Some of the domain users are homed on premises, and some users are homed online. You can configure your on-premises deployment for hybrid with Skype for Business Online and use Active Directory Synchronization to keep your on-premises and online users synchronized. 
  
The following diagram shows how you can add Skype for Business Online into your existing on-premises Skype for Business environment, allowing you to move users to the cloud at your own pace:
  
![Skype for Business Hybrid configuration](../../sfbserver/media/4580f2c8-7008-4c6e-826c-020d0f2d1636.png)
  
For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Teams](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Skype for Business Online](configure-hybrid-connectivity.md).
  
## Take advantage of Phone System in Office 365 (Cloud PBX)
<a name="BKMK_CloudPBX"> </a>

 Phone System in Office 365 (Cloud PBX) is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud with Skype for Business Online. Phone System in Office 365 allows you to replace your existing PBX system with a set of features delivered from Office 365 and tightly integrated into Microsoft's cloud productivity experience.
  
In addition to two Phone System in Office 365 hybrid offerings, Microsoft offers Phone System in Office 365 with Calling Plan—a PSTN calling service—for an all-in-the-cloud solution that does not require an on-premises server deployment. To decide if Phone System in Office 365 with Calling Plan might be the right solution for your organization, see [Phone System in Office 365 solutions](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-your-phone-system-cloud-pbx-solution.md#BKMK_PBXOfferings).
  
There are two Phone System in Office 365 hybrid offerings: 
  
- [Phone System in Office 365 with on-premises connectivity provided by your Skype for Business Server deployment](hybrid-solutions.md#BKMK_Server)
    
- [Phone System in Office 365 with on-premises connectivity provided by Skype for Business Server Cloud Connector Edition](hybrid-solutions.md#BKMK_CCE)
    
### Phone System in Office 365 with on-premises connectivity provided by your Skype for Business Server deployment
<a name="BKMK_Server"> </a>

This configuration consists of a Skype for Business Server on-premises deployment modified for hybrid PSTN. Users in your organization who are homed in the cloud can receive PBX services from the Microsoft cloud, but PSTN connectivity is provided through Enterprise Voice on your on-premises Skype for Business Server deployment. 
  
![Cloud PBX with Skype for Business Server deployment](../../sfbserver/media/d4136bbc-b01e-469c-bf94-90ba59c61cda.png)
  
This configuration is best if: 
  
- Your PBX does not offer unique features that you need to retain.
    
- Calling Plan, the Office 365 PSTN calling service, is not available in your region.
    
- You have an existing Lync or Skype for Business Server deployment.
    
For more information, see [Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity.md) and [Enable users for Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-phone-system.md).
  
### Phone System in Office 365 with on-premises connectivity provided by Skype for Business Server Cloud Connector Edition
<a name="BKMK_CCE"> </a>

This configuration consists of a set of packaged Virtual Machines (VMs) that implement on-premises PSTN connectivity. By deploying a minimal Skype for Business Server topology in a virtualized environment, users in your organization who are homed in the cloud can receive PBX services from the Microsoft cloud, but PSTN connectivity is provided through the existing on-premises voice infrastructure. 
  
![CloudPBXCloudConnectorEdition](../../sfbserver/media/7a6ee221-bfe1-422b-ac44-6446db6b766c.png)
  
This configuration is best if:
  
- Your PBX does not offer unique features that you need to retain.
    
- Calling Plan, the Office 365 PSTN calling service, is not available in your region.
    
- You do not have an existing Lync or Skype for Business Server deployment.
    
For more information, see [Plan for Skype for Business Cloud Connector Edition](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition.md).
  
## Integrate with Exchange and SharePoint
<a name="BKMK_IntegratewExchangeSharePoint"> </a>

A Skype for Business hybrid configuration allows you to integrate with other Microsoft Office 365 applications, including Exchange Online and SharePoint Online.
  
### Skype for Business Server with Exchange Online and SharePoint Online

You can integrate Skype for Business Server with Exchange Online and SharePoint Online as shown in the following diagram:
  
![Skype for Business Server with Exchange Online and SharePoint Online](../../sfbserver/media/9f456ed2-8777-4a20-a519-c87dfc56b7f5.png)
  
Integrating Skype for Business Server with Exchange Online and SharePoint Online has several advantages. You can:
  
- Use the full feature set of Skype for Business Server.
    
- Leverage your existing on-premises phone equipment, such as PBXs.
    
- Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.
    
- Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.
    
- Use Skype for Business, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.
    
For more information, see [Plan to integrate Skype for Business and Exchange](../../SfbServer/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md).
  
### Exchange Server with Skype for Business Online

You can integrate Exchange Server with Skype for Business Online as shown in the following diagram:
  
![Integrate Exchange with Skype for Business Online](../../sfbserver/media/e8ca44ad-f47c-46a3-9cef-8fe7deafd615.png)
  
Integrating Exchange Server with Skype for Business Online has the following advantages:
  
- Leverage your existing Exchange infrastructure.
    
- Use Skype for Business Online for presence, IM, and conferencing capabilities. 
    
For more information, see [Plan to integrate Skype for Business and Exchange](../../SfbServer/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md).
  
## Tasks for planning and configuring a hybrid environment
<a name="BKMK_Tasks"> </a>

Skype for Business provides a rich set of capabilities no matter how you architect your deployment. The architecture you choose will determine which IT responsibilities you own, and which you pay Microsoft to support through your subscription. No matter which architecture is best for your organization, there are five core responsibilities that you will always own:
  
- **Networking and connectivity** - Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links by performing a network assessment or by contracting with a partner to do the assessment.
    
- **Data governance &amp; rights management** - Classify your sensitive data and ensure it is protected and monitored wherever it is stored and while it is in transit.
    
- **Client Endpoints** - Establish, measure, and enforce modern security standards on devices that are used to access your data and assets.
    
- **Account &amp; access management** - Establish a profile for "normal" account activity and alert on unusual activity.
    
- **Identity** - Use credentials secured by hardware or Multi-Factor Authentication (MFA) for all identities.
    
In addition to the architectural tasks you perform for your on-premises environment, you will need to:
  
- Plan and design identity management requirements, including integrating on-premises identities with Office 365.
    
- Ensure network capacity and availability.
    
- Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.
    
- Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).
    
- Determine how much feature integration with on-premises and online versions of Skype for Business, Exchange, and SharePoint is desired. 
    
- Determine which proxy server device will be used for requests from Office 365.
    
You will also need to perform the follow IT Pro tasks to implement your Skype for Business hybrid environment:
  
- Ensure you have a Microsoft Office 365 tenant with Skype for Business Online enabled.
    
- Implement the identity management plan. 
    
- Plan and implement internal and external DNS records and routing.
    
- Configure your proxy or firewall for Office 365 IP address and URL requirements.
    
- Administer user accounts and Skype for Business Online settings. 
    
- Configure the proxy server device, if required. 
    
- Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.
    
## For more information
<a name="BKMK_MoreInfo"> </a>

For more information, see the following resources:
  
- [Microsoft cloud IT architecture resources](https://aka.ms/clouditarch)
    
- [Microsoft cloud identity for enterprise architects](https://docs.microsoft.com/office365/enterprise/microsoft-cloud-it-architecture-resources#identity)
    
- [Get your organization ready for Office 365 Enterprise](https://aka.ms/O365EntPrep)
    
- [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Teams](plan-hybrid-connectivity.md)
    
- [Configure hybrid connectivity between Skype for Business Server and Skype for Business Online](configure-hybrid-connectivity.md)
    
- [Phone System in Office 365 solutions](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-your-phone-system-cloud-pbx-solution.md#BKMK_PBXOfferings)
    
- [Plan to integrate Skype for Business and Exchange](../../SfbServer/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md)
    
If you would like to download a poster version of this topic, go to:
  
- [Skype for Business Architectural Models (pdf)](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)
    
- [Skype for Business Architectural Models (Visio)](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)
    

### PLACEHOLDER TOPIC FOR HYBRID SOLUTIONS 

IN PROGRESS...


You might also be familiar with the term "hybrid voice"—which refers to on-premises voice trunks that provide functionality to users homed in the cloud. Hybrid voice enables migration to the cloud while preserving on-premises voice configuration. If you already have a Skype for Business Server deployment, the first step to enable hybrid voice is to configure a split domain environment. 
  
For example, assume your company has a large mobile field support organization that requires minimal PBX voice, but extensive smart phone use. You might choose to move these users to the cloud to take advantage of Microsoft's Phone System in Office 365 (Cloud PBX). If your company also has a large on-premises call center that requires advanced, complex contact center software as part of your on-premises PBX, you might choose to leave these users on premises. Users homed online and on premises both have PSTN connectivity through your on-premises deployment.
  
The following diagram shows a Skype for Business hybrid voice deployment:
  
![SfB split domain with Cloud PBX](../../sfbserver/media/5e755772-269e-45ce-8b48-2e06ababfe6c.png)
  
For more information about setting up a hybrid voice solution with your Skype for Business Server deployment, see [Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity.md). 
  
You can also configure hybrid deployments for integration with on-premises Exchange and SharePoint, or with Microsoft Office 365 applications, including Exchange Online and SharePoint Online. You can also configure a hybrid voice solution that does not require a full Skype for Business Server deployment by using Cloud Connector Edition. For more information about all Skype for Business hybrid solutions and planning your move to the cloud, see [Skype for Business hybrid solutions](hybrid-solutions.md).


## Exchange co-existence
<a name="BKMK_Exchange"> </a>

To support co-existence with Exchange, keep the following in mind:
  
- The best practice is to move the user's mailbox to Exchange Online before moving the user's Skype for Business home.
    
- Users with Exchange mailboxes on premises are supported with following known limitations:
    
  - Client sign on: Users may need to sign on twice during SfB client sign on
    
  - Server side conversation history, Archiving, Unified Contact Store, HighRes Photo requires Exchange 2013 or later, and you must enable OAuth Server to Server communication. For more information, see [Manage server-to-server authentication (OAuth) and partner applications in Skype for Business Server 2015](https://technet.microsoft.com/en-us/library/jj204817.aspx).
    
For details on co-existence with Exchange Server, including support criteria and limitations in various combinations of on-premises and online, see [Feature support](../../sfbserver/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support) in [Plan to integrate Skype for Business and Exchange](../../sfbserver/plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md).



**TERMINOLOGY**

ou'll learn more about Active Directory configuration in the sections that follow. But first, an overview of the terminology and acronyms used in the diagrams below, and in many of the hybrid connectivity topics:
  
- PSTN - Public Switched Telephone Network
    
- PBX - Private Branch Exchange phone system
    
- Phone System - Microsoft's Cloud PBX phone system offering
    
- Trunk - Telephony line that connects PBXs to the PSTN—A trunk might use Session Initiation Protocol (SIP)—A Voice over Internet Protocol (VoIP)—or the older Time-Division Multiplexing (TDM) technology 
    
- SBC - Session Border Controller - Device that serves as a firewall and router in telephony networks. For example, provides security, connectivity, interoperability, and Quality of Services. 
    
- PSTN gateway - A device that serves as a router in telephony networks, capable of doing most of what an SBC can do except security and NAT traversal.
    
The following diagram shows a Skype for Business "split domain" hybrid configuration. Users A and B are homed online but are discoverable by on-premises users; users C and D are homed on premises, but are discoverable by online users.
  

