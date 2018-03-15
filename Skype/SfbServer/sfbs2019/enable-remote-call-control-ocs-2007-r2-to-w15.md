---
title: "Enable remote call control [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0b91d418-e6ed-4556-97af-e8523e01f249
description: "Remote call control enables users to control their desktop private branch exchange (PBX) phones by using Lync Server 2013. If you deployed remote call control in your legacy environment and want to migrate it Lync Server 2013, you need to perform the following tasks:"
---

# Enable remote call control [OCS 2007 R2 to W15]
[]
Remote call control enables users to control their desktop private branch exchange (PBX) phones by using Lync Server 2013. If you deployed remote call control in your legacy environment and want to migrate it Lync Server 2013, you need to perform the following tasks:
  
1. Install a SIP/CSTA gateway and configure it to communicate with your PBX. You need to do this step when you deploy your Lync Server 2013 pilot pool.
    
2. After you merge your topology and migrate your policies and settings, configure Lync Server 2013 to route CSTA requests to the SIP/CSTA gateway. This step is a manual step that follows the automated migration. To configure routing for CSTA requests, do the following:
    
  - Remove legacy authorized host entries (known as  *trusted server entries*  in Lync Server 2013). If you are migrating users from your legacy deployment, ensure that you remove all existing authorized host entries that you created for the SIP/CSTA gateway before you configure new trusted application entries on the Lync Server 2013 pilot pool. For details about how to remove legacy authorized host entries, see [Remove an authorized host entry [OCS 2007 R2 to W15]](remove-an-authorized-host-entry-ocs-2007-r2-to-w15.md).
    
  - Configure a static route for remote call control. You can configure a static route for individual pools that you want to support remote call control, or you can configure a global static route so that each pool that is not configured with a pool-level static route uses the global static route. For details about how to configure the static route, see [Configure a static route for remote call control in Lync Server 2013](configure-a-static-route-for-remote-call-control.md) in the Deployment documentation. 
    
  - Configure a trusted application entry for remote call control on each pool for which you want to support remote call control. For details about how to configure a trusted application entry, see [Configure a trusted application entry for remote call control in Lync Server 2013](configure-a-trusted-application-entry-for-remote-call-control.md) in the Deployment documentation. 
    
3. If you deployed a SIP/CSTA gateway that uses Transmission Control Protocol (TCP) to connect to Lync Server 2013, define the IP address of the gateway in Topology Builder. For details about defining the IP address, see [Define a SIP/CSTA gateway IP address in Lync Server 2013](define-a-sip-csta-gateway-ip-address.md) in the Deployment documentation. 
    
4. Configure Lync 2013 users for remote call control by enabling remote call control and assigning a line server Uniform Resource Identifier (URI) and a line URI. When you migrate users from your legacy deployment to Lync Server 2013, the remote call control settings are migrated along with the other user settings. 
    
5. If you customized Address Book phone number normalization rules in your legacy deployment, you need to perform some manual tasks after the automated migration of policies and settings is complete to migrate the customized normalization rules. If you did not customize normalization rules, Address Book is migrated along with the rest of your topology. For details about manually migrating customized normalization rules, see [Migrate Address Book [OCS 2007 R2 to W15]](migrate-address-book-ocs-2007-r2-to-w15.md).
    

