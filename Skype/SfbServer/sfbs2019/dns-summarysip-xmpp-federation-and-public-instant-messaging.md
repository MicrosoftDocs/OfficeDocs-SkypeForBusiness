---
title: "DNS summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1ed24fb8-a849-44c0-a52e-7aef7527e644

description: "The Domain Name System (DNS) records that will be required for defining a federation with Office Communications Server or Lync Server partners is determined by your decision to either allow automatic DNS discovery of your domain by other perspective partners. If you publish the _sipfederationtls._tcp. \<SIP domain name\> SRV record, any other SIP federated domain will be able todiscoveryour federation. You can control which federated domains can communicate with you by using the Allows domains and Blocked Domains settings in the Lync Server Control Panel, or by setting the allowed or blocked domains configuration using the Lync Server Management Shell and the Get, Set, New, Remove-CsAllowedDomain and -CsBlockedDomain PowerShell cmdlets. For additional information on how to configure theses settings and the use of the PowerShell cmdlets, see Related Topics at the end of this topic."
---

# DNS summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013
[]
The Domain Name System (DNS) records that will be required for defining a federation with Office Communications Server or Lync Server partners is determined by your decision to either allow automatic DNS discovery of your domain by other perspective partners. If you publish the _sipfederationtls._tcp.  _\<SIP domain name\>_ SRV record, any other SIP federated domain will be able to "discover" your federation. You can control which federated domains can communicate with you by using the Allows domains and Blocked Domains settings in the Lync Server Control Panel, or by setting the allowed or blocked domains configuration using the Lync Server Management Shell and the **Get**, **Set**, **New**, **Remove-CsAllowedDomain** and **-CsBlockedDomain** PowerShell cmdlets. For additional information on how to configure theses settings and the use of the PowerShell cmdlets, see **Related Topics** at the end of this topic. 
  
The DNS records summary table depicts the required entries for an open, or discoverable, federation. If you do not want to implement Federation Discovery, You can decide to not configure the _sipfederationtls._tcp.  _\<SIP domain name\>_ record. 
  
> [!IMPORTANT]
> There are specific scenarios in which you must have the _sipfederationtls._tcp.  _\<SIP domain name\>_ SRV record, but you do not want to have a discoverable federation. One such instance is where you have deployed mobility for your users. The mobility push notification clearinghouse (PNCH) is a special type of federation that is used for Microsoft Lync Mobile clients on Apple iPhone or iPad using the Lync 2010 Mobile client or Windows Phone using the Lync 2010 Mobile or Lync 2013 Mobile clients. The _sipfederationtls._tcp.  _\<SIP domain name\>_ SRV record is used in the case of mobility and push notification. To mitigate this issue and control your discoverability, clear the setting **Enable partner domain discovery** to turn off discovery. 
  
To configure extensible messaging and presence protocol (XMPP) for your deployment, you create two domain name system (DNS) records in an external DNS server that will resolve the records to the Access Edge service of your Edge Server or Edge pool.
  
When you configure domain name system (DNS) for public instant messaging connectivity, you will find that the configuration that supports external users will support public IM connectivity. If you have already configured your Edge Server or Edge pool, you should have the DNS records necessary to support public IM connectivity.
  
## DNS Summary - SIP Federation including Public Instant Messaging Connectivity

|**Location/TYPE/Port**|**FQDN**|**IP address/FQDN host record**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|External DNS/SRV/5061  <br/> |_sipfederationtls._tcp.contoso.com  <br/> |sip.contoso.com  <br/> |Access Edge service external interface Required for automatic DNS discovery of your federation to other potential federation partners, and is known as "Allowed SIP Domains" (called enhanced federation in previous releases).Repeat as necessary for all SIP domains with Lync enabled users  <br/> > [!IMPORTANT]> This SRV record is required for mobility and the push notification clearing house. In cases where there is more than one SIP domain, create and publish an SRV record for each domain that will have Lync Mobile clients. The Push Notification Service and Apple Push Notification service may not operate as expected if there is not an explicit SRV record for each SIP domain that the deployment supports.           |
   
## DNS Summary - Extensible Messaging and Presence Protocol (XMPP)

|**Location/TYPE/Port**|**FQDN**|**IP address/FQDN host record**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|External DNS/SRV/5269  <br/> |_xmpp-server._tcp.contoso.com  <br/> |xmpp.contoso.com  <br/> |XMPP proxy external interface on the Access Edge service or Edge pool.Repeat as necessary for all internal SIP domains with Lync enabled users where contact with XMPP contacts is allowed through the configuration of the External Access Policy through a global policy, site policy where the user is located, or user policy applied to the Lync-enabled user. An allowed XMPP domain must also be configured in the XMPP Federated Partners policy. See topics in **See Also** for additional details  <br/> |
|External DNS/A  <br/> |xmpp.contoso.com (for example)  <br/> |IP address of Access Edge service on your Edge Server or Edge pool hosting XMPP proxy  <br/> |Points to the Access Edge service or Edge pool that hosts the XMPP proxy service. Typically, the SRV record that you create will point to this host (A or AAAA) record  <br/> |
   
## See also

#### 

[Setting up XMPP federation in Lync Server 2013](setting-up-xmpp-federation.md)
  
[Configuring for push notifications in Lync Server 2013](configuring-for-push-notifications.md)
  
[Enable or disable discovery of federation partners in Lync Server 2013](enable-or-disable-discovery-of-federation-partners.md)
#### 

[Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md)
  
[Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md)
#### 

[Manage SIP federated domains for your organization in Lync Server 2013](manage-sip-federated-domains-for-your-organization.md)

