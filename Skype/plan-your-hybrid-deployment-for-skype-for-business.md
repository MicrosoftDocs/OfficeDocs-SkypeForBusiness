---
title: Plan your hybrid deployment for Skype for Business
ms.prod: SKYPEFORBUSINESS
ms.assetid: 0b038686-ed36-4867-9653-14cc08c919cb
---


# Plan your hybrid deployment for Skype for Business
[]Find information on planning a Skype for Business hybrid deployment. 
This topic introduces you to several hybrid configurations to help you determine which configuration is best for your business. You can then read more about the configuration you're interested in by following the links in this topic. This topic contains the following sections:
  
    
    


-  [Skype for Business hybrid configurations](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_HybridConfigurations)
    
  
-  [Add Skype for Business Online into your existing on-premises Skype for Business environment](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_HybridConnectivity)
    
  
-  [Take advantage of Cloud PBX](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_CloudPBX)
    
  
-  [Integrate with Exchange and SharePoint](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_IntegratewExchangeSharePoint)
    
  
-  [Tasks for planning and configuring a hybrid environment](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_Tasks)
    
  
-  [For more information](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_MoreInfo)
    
  

## Skype for Business hybrid configurations
<a name="BKMK_HybridConfigurations"> </a>

Skype for Business supports several hybrid configurations. You can add Skype for Business Online into your existing on-premises Skype for Business environment, integrate your Skype for Business deployment with Exchange Online and SharePoint Online, and take advantage of Cloud PBX—Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud with Skype for Business Online. 
  
    
    
With a Skype for Business hybrid deployment, you combine a Skype for Business Online subscription with your on-premises Skype for Business offering. You can start building software-as-a-service management skills in your organization, and move your Skype for Business users to the cloud at your own pace. Your users who are homed in the cloud can take advantage of Cloud PBX while retaining your on-premises Public Switched Telephone Network (PSTN) connectivity.
  
    
    

  
    
    
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
  
    
    

  
    
    
![Skype for Business Hybrid configuration](images/4580f2c8-7008-4c6e-826c-020d0f2d1636.png)
  
    
    

  
    
    
For more information, see  [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](plan-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busines.md) and [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](deploy-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busin.md).
  
    
    

## Take advantage of Cloud PBX
<a name="BKMK_CloudPBX"> </a>

Skype for Business Cloud PBX is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud with Skype for Business Online. Cloud PBX allows you to replace your existing PBX system with a set of features delivered from Office 365 and tightly integrated into Microsoft's cloud productivity experience. 
  
    
    
In addition to two Cloud PBX hybrid offerings, Microsoft offers Cloud PBX with PSTN Calling service, an all-in-the-cloud solution that does not require an on-premises server deployment. To decide if Cloud PBX with PSTN Calling service might be the right solution for your organization, see  [Cloud PBX solutions](plan-your-cloud-pbx-solution-in-skype-for-business.md#BKMK_PBXOfferings).
  
    
    
There are two Cloud PBX hybrid offerings: 
  
    
    

-  [Cloud PBX with on-premises connectivity provided by your Skype for Business Server deployment](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_Server)
    
  
-  [Cloud PBX with on-premises connectivity provided by Skype for Business Server Cloud Connector Edition](plan-your-hybrid-deployment-for-skype-for-business.md#BKMK_CCE)
    
  

### Cloud PBX with on-premises connectivity provided by your Skype for Business Server deployment
<a name="BKMK_Server"> </a>

This configuration consists of a Skype for Business Server on-premises deployment modified for hybrid PSTN. Users in your organization who are homed in the cloud can receive PBX services from the Microsoft cloud, but PSTN connectivity is provided through Enterprise Voice on your on-premises Skype for Business Server deployment. 
  
    
    

  
    
    
![Cloud PBX with Skype for Business Server deployment](images/d4136bbc-b01e-469c-bf94-90ba59c61cda.png)
  
    
    

  
    
    
This configuration is best if: 
  
    
    

- Your PBX does not offer unique features that you need to retain.
    
  
- PSTN Calling service is not available in your region.
    
  
- You have an existing Lync or Skype for Business Server deployment.
    
  
For more information, see  [Plan Cloud PBX with on-premises PSTN connectivity in Skype for Business Server 2015 or Lync Server 2013](plan-cloud-pbx-with-on-premises-pstn-connectivity-in-skype-for-business-server-2.md) and [Deploy Cloud PBX with on-premises PSTN connectivity in Skype for Business Server 2015 or Lync Server 2013](deploy-cloud-pbx-with-on-premises-pstn-connectivity-in-skype-for-business-server.md).
  
    
    

### Cloud PBX with on-premises connectivity provided by Skype for Business Server Cloud Connector Edition
<a name="BKMK_CCE"> </a>

This configuration consists of a set of packaged Virtual Machines (VMs) that implement on-premises PSTN connectivity. By deploying a minimal Skype for Business Server topology in a virtualized environment, users in your organization who are homed in the cloud can receive PBX services from the Microsoft cloud, but PSTN connectivity is provided through the existing on-premises voice infrastructure. 
  
    
    

  
    
    
![CloudPBXCloudConnectorEdition](images/7a6ee221-bfe1-422b-ac44-6446db6b766c.png)
  
    
    

  
    
    
This configuration is best if:
  
    
    

- Your PBX does not offer unique features that you need to retain.
    
  
- PSTN Calling service is not available in your region.
    
  
- You do not have an existing Lync or Skype for Business Server deployment.
    
  
For more information, see  [Plan for Skype for Business Cloud Connector Edition](plan-for-skype-for-business-cloud-connector-edition.md).
  
    
    

## Integrate with Exchange and SharePoint
<a name="BKMK_IntegratewExchangeSharePoint"> </a>

A Skype for Business hybrid configuration allows you to integrate with other Microsoft Office 365 applications, including Exchange Online and SharePoint Online.
  
    
    

### Skype for Business Server with Exchange Online and SharePoint Online

You can integrate Skype for Business Server with Exchange Online and SharePoint Online as shown in the following diagram:
  
    
    

  
    
    
![Skype for Business Server with Exchange Online and SharePoint Online](images/9f456ed2-8777-4a20-a519-c87dfc56b7f5.png)
  
    
    

  
    
    
Integrating Skype for Business Server with Exchange Online and SharePoint Online has several advantages. You can:
  
    
    

- Use the full feature set of Skype for Business Server.
    
  
- Leverage your existing on-premises phone equipment, such as PBXs.
    
  
- Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.
    
  
- Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.
    
  
- Use Skype for Business, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.
    
  
For more information, see  [Plan to integrate Skype for Business and Exchange](plan-to-integrate-skype-for-business-and-exchange.md).
  
    
    

### Exchange Server with Skype for Business Online

You can integrate Exchange Server with Skype for Business Online as shown in the following diagram:
  
    
    

  
    
    
![Integrate Exchange with Skype for Business Online](images/e8ca44ad-f47c-46a3-9cef-8fe7deafd615.png)
  
    
    

  
    
    
Integrating Exchange Server with Skype for Business Online has the following advantages:
  
    
    

- Leverage your existing Exchange infrastructure.
    
  
- Use Skype for Business Online for presence, IM, and conferencing capabilities. 
    
  
For more information, see  [Plan to integrate Skype for Business and Exchange](plan-to-integrate-skype-for-business-and-exchange.md).
  
    
    

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
  
    
    

-  [Microsoft cloud IT architecture resources](https://aka.ms/clouditarch)
    
  
-  [Microsoft cloud identity for enterprise architects](https://aka.ms/cloudidarch)
    
  
-  [Get your organization ready for Office 365 Enterprise](https://aka.ms/O365EntPrep)
    
  
-  [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](plan-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busines.md)
    
  
-  [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](deploy-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busin.md)
    
  
-  [Cloud PBX solutions](plan-your-cloud-pbx-solution-in-skype-for-business.md#BKMK_PBXOfferings)
    
  
-  [Plan to integrate Skype for Business and Exchange](plan-to-integrate-skype-for-business-and-exchange.md)
    
  
If you would like to download a poster version of this topic, go to:
  
    
    

-  [Skype for Business Architectural Models (pdf)](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype for Business Architectural Models.pdf)
    
  
-  [Skype for Business Architectural Models (Visio)](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype for Business Architectural Models.vsd)
    
  

