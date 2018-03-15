---
title: "Topologies and components for mobility in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: be3cae7a-095d-4785-91ba-6fac99eba92a
description: "To support Lync mobile applications on mobile devices, Lync Server 2013 provides three services: Lync Server 2013 Mcx Mobility Service, Lync Server 2013 Autodiscover Service, and Lync Server 2013 Push Notification Service. The Cumulative Updates for Lync Server 2013: February 2013 adds a complimentary, but advanced, service for Lync 2013 Mobile clients—mobility support through the use of the Unified Communications Web API, or UCWA. This section briefly describes these components and identifies the Lync Server 2013 topologies that support mobility."
---

# Topologies and components for mobility in Lync Server 2013
[]
```
The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.
```

To support Lync mobile applications on mobile devices, Lync Server 2013 provides three services: Lync Server 2013 Mcx Mobility Service, Lync Server 2013 Autodiscover Service, and Lync Server 2013 Push Notification Service. The Cumulative Updates for Lync Server 2013: February 2013 adds a complimentary, but advanced, service for Lync 2013 Mobile clients—mobility support through the use of the Unified Communications Web API, or UCWA. This section briefly describes these components and identifies the Lync Server 2013 topologies that support mobility.
  
> [!NOTE]
> Mobility services are also available in hybrid deployments. You are not required to deploy services for supporting mobility if your users are homed online. You do need to define a setting for the Autodiscover Service to enable mobile users to find their online identity. 
  
> [!IMPORTANT]
> If you are planning any external user connectivity (for example, federation, external user access, or mobility features), you must use Edge Servers with Standard Edition server and the Front End Server or Front End pool. The Standard Edition server and the Front End Server or Front End pool do not have the necessary components to enable external users to access your internal deployment, or for the internal deployment to communicate with your external users. For all scenarios that include external users collaborating or communicating with internal users, including mobility, you must deploy at least one Edge Server and one reverse proxy. > Push notification uses a type of federation to the Lync Online services, which hosts the Push Notification Clearing House (PNCH). Push notification refers to the sound alerts, on-screen alerts (text), and badges that are pushed by applications to the Apple iPhone, iPad, and Windows Phone, when the mobile device is inactive. PNCH receives push notifications from Lync Server. When PNCH receives a notification of a message, PNCH forwards a notification to mobile clients through either the Apple Push Notification Services or Lync Server 2013 Push Notification Service, based on the mobile client that the message is intended for. PNCH is a required service for these mobile clients. To federate to Lync Online, PNCH uses Edge Servers and certificates to ensure confidentiality and authentication, policies, and correctly configured domain name system (DNS) records. Nokia Symbian and Android-based Lync Mobile clients do not use PNCH. For details about planning and deploying Edge Servers, see [Planning for external user access in Lync Server 2013](planning-for-external-user-access.md) and [Deploying external user access in Lync Server 2013](deploying-external-user-access.md). > The Lync 2013 Mobile clients for Apple devices introduced with the Cumulative Updates for Lync Server 2013: February 2013 no longer use push notification or the push notification clearing house (PNCH). Lync 2013 Mobile clients on Windows Phone still use push notification and the (PNCH). 
  
## Mobility Components

The services that support mobility are as follows:
  
- **Lync Server 2013 Unified Communications Web API (UCWA)** Provides services for real-time communications with mobile and web clients in Lync Server 2013. When you deploy the Cumulative Updates for Lync Server 2013: February 2013 to the Front End Server and Director, the installation creates a virtual directory in the internal and external web services (Ucwa). A web component that is part of the Ucwa virtual directory accepts calls from UCWA-enabled clients. The client apps communicate over a REST interface for presence, contacts, instant messaging, VoIP, video conferencing, and collaboration. UCWA uses a P-GET based channel to send events, such as an incoming call, incoming instant message, or a message to the client app. 
    
    > [!NOTE]
    > REST or representational state transfer, is a software architectural style for distributed systems that has been widely adopted in many forms and is well suited to the requirements of Web services in general. 
  
- **Lync Server 2013 Mobility Service (Mcx)** This service supports Lync functionality, such as instant messaging (IM), presence, and contacts, on mobile devices. The Mobility Service is installed on every Front End Server in each pool that is to support Lync functionality on mobile devices. When you install Lync Server 2013, a new virtual directory (Mcx) is created under both the internal website and the external website on your Front End Servers. 
    
    > [!IMPORTANT]
    > Lync Server 2013 with the Cumulative Updates for Lync Server 2013: February 2013 supports both the Mobility service introduced in the Cumulative Update for Lync Server 2010: November 2011, commonly known as Mcx, and the UCWA web component. The combination of these two mobility services provides interoperability and use by users with Lync 2010 Mobile and Lync 2013 Mobile clients on Lync Server 2013. 
  
- **Lync Server 2013 Autodiscover Service** This service identifies the location of the user and enables mobile devices and other Lync clients to locate resources—such as the internal and external URLs for Lync Server 2013 Web Services, and the URL for the Mcx or UCWA—regardless of network location. Automatic discovery uses hardcoded host names (lyncdiscoverinternal for users inside the network; lyncdiscover for users outside the network) and the SIP domain of the user. It supports client connections that use either HTTP or HTTPS. 
    
    The Autodiscover Service is installed on every Front End Server and on every Director in each pool that is to support Lync functionality on mobile devices. When you install the Autodiscover Service, a new virtual directory (Autodiscover) is created under both the internal website and the external website, on both Front End Servers and Directors.
    
    > [!NOTE]
    > The Autodiscover Service is listed here because it remains a critical component when providing mobile client services. The role of Autodiscover in Lync Server 2013 has been expanded to provide services for all clients. For details about planning for the Autodiscover Service, see [Planning for Autodiscover in Lync Server 2013](planning-for-autodiscover.md). 
  
- **Push Notification Service** This service is a cloud-based service that is located in the Skype for Business Online data center. When the Lync mobile application on a supported Apple iOS device or Windows Phone is inactive, it cannot respond to new events, such as a new instant messaging (IM) invitation, a missed instant message, a missed call, or voice mail, because these devices do not support mobile applications running in the background. In these cases, a notification of the new event—called a push notification—is sent to the mobile device. The Mobility Service sends the notification to the cloud-based Push Notification Service, which then sends the notification either to the Apple Push Notification Service (APNS) (for supported Apple iOS devices) or to the Microsoft Push Notification Service (MPNS) (for Windows Phone), which then sends it on to the mobile device. The user can then respond to the notification on the mobile device to activate the application.
    
    The Lync 2010 Mobile on Apple and Windows Phone devices use push notifications. The Lync 2013 Mobile client for Apple devices introduced with the Cumulative Updates for Lync Server 2013: February 2013 no longer uses push notification or the push notification clearing house (PNCH).
    
The following diagram illustrates how the Push Notification Service fits within a Lync Server 2013 topology that uses UCWA and Lync 2013 Mobile clients.
  
![Push Notification Services UCWA](media/Plan_LyncServer_Mobility_PNCHComponentsUCWA.jpg)
  
Introduced in Cumulative Update for Lync Server 2010: November 2011, the Mcx service provides services to Lync 2010 Mobile clients. The following diagram illustrates the Push Notification Service as it applies to a topology using Mcx and Lync 2010 Mobile clients.
  
![Push Notification Services MCX](media/Plan_LyncServer_Mobility_PNCHComponentsMCX.jpg)
  
## Supported Topologies

Applying the Cumulative Updates for Lync Server 2013: February 2013 adds the UCWA web components to support mobility for Lync 2013 Mobile client features in the following topologies:
  
- Lync Server 2013 Standard Edition
    
- Lync Server 2013 Enterprise Edition
    
The Edge Server can be a Lync Server 2010 Edge Server.
  
A Lync Server 2013 deployment without the Cumulative Updates for Lync Server 2013: February 2013 will use the Mcx Mobility Service and can provide services only for Lync 2010 Mobile.
  
> [!IMPORTANT]
> The Mobility Service is supported on Front End Servers that is collocated with the Mediation Server role with two network interfaces, but you must take appropriate steps to configure the interfaces. You must assign the IP addresses to the specific interface that will communicate as the Mediation Server, and the network interface IP that will communicate as the Front End Server. You can do this in Topology Builder by selecting the correct IP address for each service, instead of using the default **Use all configured IP addresses**. 
  
## See also

#### 

[Planning for external user access in Lync Server 2013](planning-for-external-user-access.md)
  
[Deploying external user access in Lync Server 2013](deploying-external-user-access.md)
  
[Planning for Autodiscover in Lync Server 2013](planning-for-autodiscover.md)

