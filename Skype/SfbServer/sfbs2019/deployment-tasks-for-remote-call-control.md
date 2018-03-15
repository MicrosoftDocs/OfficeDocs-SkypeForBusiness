---
title: "Deployment tasks for remote call control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 20218871-4f27-4611-9b7e-c0ca55908284
description: "In this articleStep 1: Install and Configure the SIP/CSTA Gateway to Communicate with Your PBXStep 2: Configure Lync Server to Route CSTA Requests to the SIP/CSTA GatewayStep 3: Configure Lync Users for Remote Call ControlStep 4: Define the Lync Server Phone Number Normalization Rules"
---

# Deployment tasks for remote call control in Lync Server 2013
[]
 **In this article**
  
[Step 1: Install and Configure the SIP/CSTA Gateway to Communicate with Your PBX](#sectionSection0)
  
[Step 2: Configure Lync Server to Route CSTA Requests to the SIP/CSTA Gateway](#sectionSection1)
  
[Step 3: Configure Lync Users for Remote Call Control](#sectionSection2)
  
[Step 4: Define the Lync Server Phone Number Normalization Rules](#sectionSection3)
  
This topic describes the deployment tasks that you must perform to enable remote call control for users in your Lync Server environment.
  
> [!NOTE]
> If you are migrating users previously enabled for remote call control in Microsoft Office Communicator 2007 R2, you must perform an additional deployment task before you begin performing the remote call control deployment tasks described in this topic. During the migration process to Lync Server, trusted application entries (previously known as authorized host entries) must be removed by using the Office Communications Server 2007 R2 administrative tools, as appropriate. > For details about removing authorized hosts, see [Remove a legacy authorized host in Lync Server 2013 (optional)](remove-a-legacy-authorized-host-optional.md). 
  
## Step 1: Install and Configure the SIP/CSTA Gateway to Communicate with Your PBX
<a name="sectionSection0"> </a>

You need to install at least one SIP/CSTA gateway that can connect to both Lync Server and the existing private branch exchange (PBX) in your environment in order to provide remote call control features to your users. A SIP/CSTA gateway is a gateway between SIP and a computer-supported telecommunications application (CSTA). Whether you install multiple gateways or just one, each user can be configured with only one gateway or PBX. If your existing PBX does not have a SIP/CSTA interface, ensure you deploy a SIP/CSTA gateway that can support the PBX, including support for proprietary PBX vendor-specific signaling protocols. For details about capabilities, consult each vendor directly.
  
When you are ready to deploy a SIP/CSTA gateway that can integrate with Lync Server for remote call control, also consult with your gateway vendor or the vendor's gateway documentation regarding the syntax required by the gateway for the following information:
  
- Line server URI of the gateway
    
- Line URI for users that will be assigned to the gateway
    
The preceding settings are required during user configuration and must be specified as expected by the gateway to route and connect to the PBX properly.
  
You can refer to vendors on the Microsoft Unified Communications Open Interoperability Program website at [https://go.microsoft.com/fwlink/p/?linkId=203309](https://go.microsoft.com/fwlink/p/?linkId=203309).
  
## Step 2: Configure Lync Server to Route CSTA Requests to the SIP/CSTA Gateway
<a name="sectionSection1"> </a>

You must create static routes on Lync Server pools to the destination address (server URI) of all SIP/CSTA gateways in your deployment to which you intend to route remote call control requests. You must also create a trusted application entry that corresponds to each destination address. When you designate the gateway as a trusted application, it is given trusted status to run as part of the Lync Server environment even though it is developed by a third party (and runs what is referred to as an external service because it is a service that is not a built-in part of the product). Finally, if Lync Server will connect to the SIP/CSTA gateway using a Transmission Control Protocol (TCP) connection instead of a Transport Layer Security (TLS) connection, you must also define the gateway IP address by using Topology Builder. 
  
For details about configuring static routes, see [Configure a static route for remote call control in Lync Server 2013](configure-a-static-route-for-remote-call-control.md).
  
For details about configuring trusted application entries, see [Configure a trusted application entry for remote call control in Lync Server 2013](configure-a-trusted-application-entry-for-remote-call-control.md).
  
For details about defining a SIP/CSTA gateway IP address in Topology Builder, see [Define a SIP/CSTA gateway IP address in Lync Server 2013](define-a-sip-csta-gateway-ip-address.md).
  
## Step 3: Configure Lync Users for Remote Call Control
<a name="sectionSection2"> </a>

After users have been enabled for Lync Server, you can use Lync Server Control Panel or Lync Server Management Shell to enable them for remote call control. It is during this deployment step that you assign each user a line server URI and a line URI. The line server URI is the SIP URI of the SIP/CSTA gateway that you plan to assign to the user. The line URI is the unique phone number assigned to the user.
  
For details about configuring users for remote call control, see [Enable Lync users for remote call control in Lync Server 2013](enable-lync-users-for-remote-call-control.md).
  
## Step 4: Define the Lync Server Phone Number Normalization Rules
<a name="sectionSection3"> </a>

In remote call control scenarios, Lync Server uses phone number normalization rules to convert phone numbers it receives from the SIP/CSTA gateway to E.164 format. Phone numbers must be in this standardized format for certain remote call control features to function properly. Remote call control uses the same phone number normalization rules that you configure for Address Book Service phone number normalization, which are different from the phone number normalization rules used for Enterprise Voice.
  
For details about how remote call control uses phone number normalization rules, see [Remote call control and phone number normalization in Lync Server 2013](remote-call-control-and-phone-number-normalization.md). For details about phone number normalization rules for Address Book Service, see [Administering the Address Book Service in Lync Server 2013](administering-the-address-book-service.md) topic in the Operations documentation. 
  

