---
title: "Configuring SIP federation, XMPP federation and public instant messaging in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a6d04f0b-5cb8-4084-a3a2-d501938971f9

description: "Federation, public instant messaging connectivity and Extensible Messaging and Presence Protocol (XMPP) define a different class of external users - Federated users. Users of a federated Lync Server deployment or XMPP deployment have access to a limited set of services and are authenticated by the external deployment. Remote users are members of your Lync Server deployment and have access to all services offered by your deployment."
---

# Configuring SIP federation, XMPP federation and public instant messaging in Lync Server 2013
[]
Federation, public instant messaging connectivity and Extensible Messaging and Presence Protocol (XMPP) define a different class of external users - Federated users. Users of a federated Lync Server deployment or XMPP deployment have access to a limited set of services and are authenticated by the external deployment. Remote users are members of your Lync Server deployment and have access to all services offered by your deployment.
  
> [!NOTE]
> An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see [Support for public instant messenger connectivity in Lync Server 2013](support-for-public-instant-messenger-connectivity.md). 
  
Public instant messaging connectivity is a special type of federation that allows a Lync Server client to access configured public Instant Messaging partners using the Lync 2013. The current public instant messaging connectivity partners are:
  
> America Online
    
>  Windows Live 
    
> Yahoo!
    
A public instant messaging connectivity configuration allows Lync users access to public instant messaging connectivity users by:
  
- IM and Presence
    
- Visibility of public instant messaging connectivity contacts in Lync client
    
- Person to person IM conversations with contacts
    
- Audio and video calls with Windows Live users
    
Lync Server federation defines an agreement between your Lync Server deployment and other Office Communications Server 2007 R2 or Lync Server deployments. A Lync Server federated configuration allows Lync users access to federated users by:
  
- IM and Presence
    
- Creation of federated contacts in the Lync client
    
XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol. An XMPP configuration allows Lync users access to allowed XMPP domain users by:
  
- IM and Presence - person to person only
    
- Creation of XMPP federated contacts in the Lync client
    
> [!IMPORTANT]
> The XMPP capability of Lync Server 2013 is tested and supported by Microsoft for instant messaging federation with Google Talk. For any other XMPP systems contact the third-party vendor to verify that they support federation with Lync Server 2013, and for any deployment or troubleshooting recommendations. 
  
## Edge Server External Federation, Public Instant Messaging Connectivity and XMPP Users Deployment Process

|**Phase**|**Steps**|**Permissions**|**Documentation**|
|:-----|:-----|:-----|:-----|
|Determine the options to add to the existing Edge deployment  <br/> |Run Topology Builder to edit Edge Server settings and create and publish the topology. Your existing Edge topology will replicate changes from the Central Management store to the Edge Server.  <br/> |Domain Admins group and RTCUniversalServerAdmins group  <br/> > [!NOTE]> You can edit a topology using an account that is a member of the local users group, but publishing a topology requires an account that is a member of the Domain Admins group and the RTCUniversalServerAdmins group           |[Building an edge and Director topology in Lync Server 2013](building-an-edge-and-director-topology.md) <br/> |
|Prepare for setup  <br/> | Ensure that system prerequisites are met.  <br/>  Configure internal and external DNS records, to support public instant messaging connectivity, Lync Federation and XMPP Federation  <br/>  Configure ports and protocols at the firewall to support the types of federation that you are deploying  <br/>  Obtain and install public certificates. The time required to obtain certificates depends on which certification authority (CA) issues the certificate. This step is optional at this point in the deployment. If you do not perform this step at this point, you must do it during Edge Server configuration. The Edge Server service cannot be started until certificates are obtained  <br/> |As appropriate to your organization, as these roles are typically split amongst numerous work groups  <br/> |[Planning for SIP, XMPP federation, and public instant messaging in Lync Server 2013](planning-for-sip-xmpp-federation-and-public-instant-messaging.md) <br/> |
|Set up Edge Servers for Federation Scenarios  <br/> | Transport the exported topology configuration file to each Edge Server or allow replication to complete  <br/>  Re-Run the Deployment Wizard to install supporting components for Federation  <br/>  Configure the Edge Servers  <br/>  Request and install certificates for each Edge Server  <br/>  Restart the Edge Server services  <br/> |Administrators group  <br/> |[Setting up Lync federation in Lync Server 2013](setting-up-lync-federation.md) <br/> [Setting up public instant messaging connectivity in Lync Server 2013](setting-up-public-instant-messaging-connectivity.md) <br/> [Setting up XMPP federation in Lync Server 2013](setting-up-xmpp-federation.md) <br/> |
|Configure support for external user access.  <br/> | Use the Lync Server Control Panel External User Access  <br/>  Configure External Access Policy to enable Communications with federated users or public users  <br/>  Configure SIP Federated Domains to Allow or Block domains  <br/>  Enable SIP Federated Providers for public instant messaging connectivity providers  <br/>  Configure XMPP Federated Partners per XMPP domain  <br/> |RTCUniversalServerAdmins group or user account that is assigned to the CSAdministrator role  <br/> |[Configuring support for external user access in Lync Server 2013](configuring-support-for-external-user-access.md) <br/> [Configure media encryption for public providers in Lync Server 2013](configure-media-encryption-for-public-providers.md) <br/> |
|Verify your Edge Server configuration  <br/> |Verify server connectivity and replication of configuration data from internal servers  <br/> |For verification of replication, RTCUniversalServerAdmins group or user account that is assigned to the CSAdministrator roleFor verification of user connectivity, a user for each type of Federated user  <br/> |[Verifying your edge deployment in Lync Server 2013](verifying-your-edge-deployment.md) <br/> [Example XMPP configuration in Lync Server 2013 - XMPP federation with Google Talk](example-xmpp-configuration-–-xmpp-federation-with-google-talk.md) <br/> |
   

