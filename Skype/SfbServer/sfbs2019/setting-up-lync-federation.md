---
title: "Setting up Lync federation in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 374ddc43-26f9-499d-be68-a5158adfa49c

description: "If you have already deployed you Edge server or servers, adding the federated scenarios features is straight forward. If you have not set up Edge Servers, you must do that first. For details, see: Planning for external user access in Lync Server 2013 in the Planning documentation and Deploying external user access in Lync Server 2013 in the Deployment documentation."
---

# Setting up Lync federation in Lync Server 2013
[]
If you have already deployed you Edge server or servers, adding the federated scenarios features is straight forward. If you have not set up Edge Servers, you must do that first. For details, see: [Planning for external user access in Lync Server 2013](planning-for-external-user-access.md) in the Planning documentation and [Deploying external user access in Lync Server 2013](deploying-external-user-access.md) in the Deployment documentation. 
  
> [!NOTE]
> If you intend to setup any combination of XMPP federation, Lync Federation, or public instant messaging connectivity, you can deploy them concurrently or one at a time. If you configure the options through the Topology Builder and the Lync Server Management shell, then run the Deployment Wizard at the Edge server after configuring the options for one, two or all three federation types, you can reduce the number of steps required. 
  
### Setting Up Lync Federation in Topology Builder and the Deployment Wizard

1. On a Front End server, open Topology Builder. Expand Edge pools, then right click your Edge server or Edge server pool. Select Edit properties.
    
2. In Edit Properties under General, select Enable federation for this Edge pool (Port 5061). Click OK.
    
3. Click Action, select Topology, select Publish. When prompted on Publish the topology, click Next. When the Publish is finished, click Finish.
    
4. On the Edge server, open the Lync Server Deployment wizard. Click Install or Update Lync Server System, then click Setup or Remove Lync Server Components. Click Run Again.
    
5. At Setup Lync Server components, click Next. The summary screen will show actions as they are executed. Once the deployment is done, click View Log to view available log files. Click Finish to complete the deployment.
    
    > [!IMPORTANT]
    > You can select this option, but only one Edge pool or Edge Server in your organization can be published externally for federation. All access by federated users, including public instant messaging (IM) users, go through the same Edge pool or single Edge Server. For example, if your deployment includes an Edge pool or single Edge Server deployed in New York and one deployed in London and you enable federation support on the New York Edge pool or single Edge Server, signal traffic for federated users will go through the New York Edge pool or single Edge Server. This is true even for communications with London users, although a London internal user calling a London federated user uses the London pool or Edge Server for A/V traffic. 
  
### Configuring Federation with Partners

1. To setup a successful federation with another Microsoft Lync Server 2013, Lync Server 2010, Office Communications Server 2007 R2, or Office Communicator 2007, select the type of federation from the following table and define DNS SRV records, DNS host (A or AAAA for IPv6) and configure policies applicable to the type of federation:
    
|**Federation type**|**DNS Records**|**Policy Definition**|**Notes**|
|:-----|:-----|:-----|:-----|
|Discovered Partner Domain  <br/> |Configure SRV record of the format _sipfederationtls._tcp.<external domain name>Where the port value for the SRV record is TCP 5061 and the **Host offering this service** is defined as sip. <external domain name> - the FQDN of your Access Edge service. See [Configure DNS for edge support in Lync Server 2013](configure-dns-for-edge-support.md) for details on creating the SRV record  <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> [Enable or disable discovery of federation partners in Lync Server 2013](enable-or-disable-discovery-of-federation-partners.md) <br/> |Previous versions referred to this type of federation as **Open Enhanced Federation**. The creation of the SRV record is required for this type of federation and is to allow other partners to discover your federation.  <br/> |
|Allowed Partner Domain  <br/> |Configure SRV record of the format _sipfederationtls._tcp.<external domain name>Where the port value for the SRV record is TCP 5061 and the **Host offering this service** is defined as sip. <external domain name> - the FQDN of your Access Edge service. See [Configure DNS for edge support in Lync Server 2013](configure-dns-for-edge-support.md) for details on creating the SRV record  <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> |Previous versions referred to this type of federation as ** Enhanced Federation **. The creation of the SRV record is optional for this type of federation and is to allow other partners to discover your federation. Of course, this is then an **Open Enhanced Federation**, or **Discovered Partner Domain** <br/> |
|Allowed Partner Server  <br/> |Configure the SIP domain name and the partner Edge Server FQDN as a federation partner in Policies  <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> [Configure support for allowed external domains in Lync Server 2013](configure-support-for-allowed-external-domains.md) <br/> [Configure support for blocked external domains in Lync Server 2013](configure-support-for-blocked-external-domains.md) <br/> |This federation type is the definition of a one to one relationship and does not allow for discovery of other federation partners. Each federation partner is configured explicitly. In previous versions, this was known as **Direct Federation** <br/> |
|Hosting Provider and Public IM Provider  <br/> |No specific DNS requirements are defined for this type of federation  <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> [Create or edit public SIP federated providers in Lync Server 2013](create-or-edit-public-sip-federated-providers.md) <br/> [Create or edit hosted SIP federated providers Lync Server 2013](create-or-edit-hosted-sip-federated-providers.md) <br/> |This federation type defines services and hosting providers that you want to configure for your users. Typical uses include configuration for public IM providers like Windows Live Messenger, Yahoo! and AOL, as well as hosting providers such as Skype for Business Online and Office 365  <br/> > [!IMPORTANT]>  As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL") is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see [Support for public instant messenger connectivity in Lync Server 2013](support-for-public-instant-messenger-connectivity.md). >  The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down. >  More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.           |
   
2. Define and configure any required DNS host (A or AAAA for IPv6) and DNS SRV records
    
3. Define and configure any policies using the Lync Server Control Panel or by using the Lync Server Management Shell and the appropriate cmdlets. For details on the Lync Server Management Shell cmdlets, see [Federation and external access cmdlets in Lync Server 2013](federation-and-external-access-cmdlets.md)
    
    > [!NOTE]
    > Lync Room System (LRS) does not show join button for meetings sent by organizers in federated Lync partners. For a meeting join link to appear on LRS, the sending organization must enable TNEF by using the following cmdlet: > >  `New-RemoteDomain -DomainName Contoso.com -Name Contoso`>  `Set-RemoteDomain -Identity Contoso -TNEFEnabled $true`> Note that this is not LRS specific. Outlook and Lync would also not show Join links in this case as MAPI properties are not transported, but in the Outlook case, the user can open up the meeting invite and click on the meeting URL. When TNEFEnabled is set to true Exchange 2013 does not strip MAPI properties including OnlineMeetingExternalLink and the Join button will be shown on the reminder. 
  
## See also

#### 

[Planning for SIP, XMPP federation, and public instant messaging in Lync Server 2013](planning-for-sip-xmpp-federation-and-public-instant-messaging.md)
  
[Managing federation and external access to Lync Server 2013](managing-federation-and-external-access-to-lync-server-2013.md)

