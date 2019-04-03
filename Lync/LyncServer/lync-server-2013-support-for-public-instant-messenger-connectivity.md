---
title: Lync Server 2013 support for public instant messenger connectivity
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Support for public instant messenger connectivity
ms:assetid: 9c6eb500-647b-4ccd-a00e-2b8dd7c44a76
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn458579(v=OCS.15)
ms:contentKeyID: 59170234
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Support for public instant messenger connectivity in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

<div>

## Support for Public Instant Messenger Connectivity

This article provides information about support for Public IM Connectivity (PIC). PIC is a feature of Microsoft Lync that allows organizations to enable their Lync users to connect with users of certain public instant messaging (IM) services through their Lync clients and identities.

End-users benefit from being able to connect with customers, partners, and vendors on their terms. IT benefits from supporting a single real-time communications client while maintaining the control, compliance, and archiving features of Lync. Lync-Skype connectivity, [publicly available in May 2013](http://blogs.technet.com/b/lync/archive/2013/05/23/lync-skype-connectivity-available-today.aspx), relies on the legacy that Lync/Office Communications Server (OCS)/Live Communications Server (LCS) first established with PIC in connecting to MSN/Windows Live, AOL, and Yahoo.  For more information on Lync-Skype connectivity, see the [Lync-Skype connectivity](http://office.microsoft.com/en-us/lync/lync-skype-connectivity-fx103789635.aspx). Federation with Windows Live, AOL, and Yahoo are each on a path towards end-of-life. This page documents the status of each service.

To use PIC, customers have been required to activate the service for each public IM service provider. The requirements and details for how to do this are dependent upon the IM service provider and the customer's underlying licensing program.

<div>

## Windows Live Messenger

Microsoft brought Windows Live Messenger and Skype together. In April 2013, Messenger users were migrated to Skype upon sign-in. Lync customers who rely on federation with Messenger will continue to be able to communicate with their Messenger contacts, even after those contacts update to Skype. There is nothing that Lync administrators or Lync end-users need to do to maintain continuity of service, and management of this capability within Lync remains the same as it has been for communications with Messenger. 

When Messenger users sign into Skype using their Microsoft accounts (i.e., the same credentials used for Messenger) all of their Messenger contacts - including federated Lync contacts - follow them into Skype. Presence sharing and instant messaging between Skype and Lync for these contacts is available. 

Lync-Skype connectivity - contact adding, presence sharing, instant messaging, and audio calling between Lync and Skype users - is also now available to all Lync customers.

</div>

<div>

## Yahoo\! and AOL Instant Messenger

Federation with Yahoo\! and AOL are both on a path toward end-of-life for customers of Lync (and Office Communications Server). Microsoft’s ability to provide each of these services has been contingent upon support from Yahoo\! and AOL, and the underlying agreements of these are winding down. For both Yahoo\! and AOL, service will continue through June 2014.

  - **Yahoo** - Service will continue through June 2014, and customers continue to need to be licensed with the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”).  As of September 1st, 2012, the PIC USL, is no longer available for purchase for new or renewing agreements.  Customers with licenses purchased prior to this date will be able to continue to federate with Yahoo\! until the earlier of the service shut down date or their license expiration. Read [the announcement](http://blogs.technet.com/b/lync/archive/2012/11/26/lync-and-yahoo-federation-end-of-life.aspx) on the Lync Team Blog. Customers who have PIC licenses on agreements that extend past June 30, 2014 will receive a credit in proportion to the amount of the payments covering the time period following June 30, 2014.

  - **AOL** - On June 30, 2014, Lync's IM connectivity ("PIC") service will no longer be available. In order to limit customer disruption when the service ends, we have discontinued the provisioning of additional customer domains. Until June 30, 2014, customers do not need to do anything to continue to support federated communications with AIM. Beyond this date (or for customers that would like to provision additional domains in the meantime), a substitute service is available directly from AOL. For more information on AOL's new service, see [Establishing Direct Federation with AIM](http://aimenterprise.aol.com/pic.php)  (opens new page on AOL.com).  

</div>

<div>

## Public IM Provider Summary

The following table provides a summary of the Public IM service providers, federation capabilities with Lync, and licensing requirements.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Public IM Service Provider</th>
<th>Federated Capabilities</th>
<th>Licensing Requirements</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Skype</p></td>
<td><p>IM, Presence, Audio</p></td>
<td><p>Lync Server Client Access Licenses, Lync Online Plan 1/2/3</p></td>
</tr>
<tr class="even">
<td><p>Windows Live Messenger</p></td>
<td><p>IM, Presence, Audio/Video</p></td>
<td><p>Lync Server Client Access Licenses (supported as long as WLM is in market)</p></td>
</tr>
<tr class="odd">
<td><p>AOL</p></td>
<td><p>IM, Presence</p></td>
<td><p>Lync Server Client Access Licenses; supported through June 2014 for existing customers.</p></td>
</tr>
<tr class="even">
<td><p>Yahoo!</p></td>
<td><p>IM, Presence</p></td>
<td><p>Requires additional Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) in addition to Lync Server Client Access Licences. As of the September 2012 Price List, the PIC USL is no longer available for purchase. Customers with active licenses are able to continue to federate with Yahoo! Messenger until the service shut down date on June 30, 2014.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

