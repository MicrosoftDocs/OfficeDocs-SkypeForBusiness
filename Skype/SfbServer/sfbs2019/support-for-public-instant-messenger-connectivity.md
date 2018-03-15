---
title: "Support for public instant messenger connectivity in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9c6eb500-647b-4ccd-a00e-2b8dd7c44a76

---

# Support for public instant messenger connectivity in Lync Server 2013
[]
## Support for Public Instant Messenger Connectivity

This article provides information about support for Public IM Connectivity (PIC). PIC is a feature of Microsoft Lync that allows organizations to enable their Lync users to connect with users of certain public instant messaging (IM) services through their Lync clients and identities.
  
End-users benefit from being able to connect with customers, partners, and vendors on their terms. IT benefits from supporting a single real-time communications client while maintaining the control, compliance, and archiving features of Lync. Lync-Skype connectivity, [publicly available in May 2013](https://blogs.technet.com/b/lync/archive/2013/05/23/lync-skype-connectivity-available-today.aspx), relies on the legacy that Lync/Office Communications Server (OCS)/Live Communications Server (LCS) first established with PIC in connecting to MSN/Windows Live, AOL, and Yahoo. For more information on Lync-Skype connectivity, see the [Lync-Skype connectivity](https://office.microsoft.com/en-us/lync/lync-skype-connectivity-FX103789635.aspx). Federation with Windows Live, AOL, and Yahoo are each on a path towards end-of-life. This page documents the status of each service.
  
To use PIC, customers have been required to activate the service for each public IM service provider. The requirements and details for how to do this are dependent upon the IM service provider and the customer's underlying licensing program.
  
### Windows Live Messenger

Microsoft brought Windows Live Messenger and Skype together. In April 2013, Messenger users were migrated to Skype upon sign-in. Lync customers who rely on federation with Messenger will continue to be able to communicate with their Messenger contacts, even after those contacts update to Skype. There is nothing that Lync administrators or Lync end-users need to do to maintain continuity of service, and management of this capability within Lync remains the same as it has been for communications with Messenger. 
  
When Messenger users sign into Skype using their Microsoft accounts (i.e., the same credentials used for Messenger) all of their Messenger contacts - including federated Lync contacts - follow them into Skype. Presence sharing and instant messaging between Skype and Lync for these contacts is available. 
  
Lync-Skype connectivity - contact adding, presence sharing, instant messaging, and audio calling between Lync and Skype users - is also now available to all Lync customers.
  
### Yahoo! and AOL Instant Messenger

Federation with Yahoo! and AOL are both on a path toward end-of-life for customers of Lync (and Office Communications Server). Microsoft's ability to provide each of these services has been contingent upon support from Yahoo! and AOL, and the underlying agreements of these are winding down. For both Yahoo! and AOL, service will continue through June 2014.
  
- **Yahoo** - Service will continue through June 2014, and customers continue to need to be licensed with the Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL"). As of September 1st, 2012, the PIC USL, is no longer available for purchase for new or renewing agreements. Customers with licenses purchased prior to this date will be able to continue to federate with Yahoo! until the earlier of the service shut down date or their license expiration. Read [the announcement](https://blogs.technet.com/b/lync/archive/2012/11/26/lync-and-yahoo-federation-end-of-life.aspx) on the Lync Team Blog. Customers who have PIC licenses on agreements that extend past June 30, 2014 will receive a credit in proportion to the amount of the payments covering the time period following June 30, 2014. 
    
- **AOL** - On June 30, 2014, Lync's IM connectivity ("PIC") service will no longer be available. In order to limit customer disruption when the service ends, we have discontinued the provisioning of additional customer domains. Until June 30, 2014, customers do not need to do anything to continue to support federated communications with AIM. Beyond this date (or for customers that would like to provision additional domains in the meantime), a substitute service is available directly from AOL. For more information on AOL's new service, see [Establishing Direct Federation with AIM](http://aimenterprise.aol.com/pic.php) (opens new page on AOL.com). 
    
### Public IM Provider Summary

The following table provides a summary of the Public IM service providers, federation capabilities with Lync, and licensing requirements.
  
****

|**Public IM Service Provider**|**Federated Capabilities**|**Licensing Requirements**|
|:-----|:-----|:-----|
|Skype  <br/> |IM, Presence, Audio  <br/> |Lync Server Client Access Licenses, Lync Online Plan 1/2/3  <br/> |
|Windows Live Messenger  <br/> |IM, Presence, Audio/Video  <br/> |Lync Server Client Access Licenses (supported as long as WLM is in market)  <br/> |
|AOL  <br/> |IM, Presence  <br/> |Lync Server Client Access Licenses; supported through June 2014 for existing customers.  <br/> |
|Yahoo!  <br/> |IM, Presence  <br/> |Requires additional Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL") in addition to Lync Server Client Access Licences. As of the September 2012 Price List, the PIC USL is no longer available for purchase. Customers with active licenses are able to continue to federate with Yahoo! Messenger until the service shut down date on June 30, 2014.  <br/> |
   

