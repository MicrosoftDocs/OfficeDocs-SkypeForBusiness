---
title: 'Lync Server 2013: Understanding Autodiscover'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Understanding Autodiscover
ms:assetid: d70a15b7-750b-4e0f-9a7f-0254d6d486c3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945654(v=OCS.15)
ms:contentKeyID: 51541522
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Understanding Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-06-03_

The Lync Server 2013 Autodiscover Service is a feature that was originally introduced in Microsoft Lync Server 2010 as part of the Cumulative Update for Lync Server 2010: November 2011. In addition to fixes, this cumulative update delivered support for Lync Mobile and Lync 2013 clients.

In Lync Server 2013, the Autodiscover Service is an integral part of the operation of external and internal mobile clients, and Autodiscover is also extended to new clients, such as the recently introduced Lync Windows Store app for Windows 8. Autodiscover is also used by the Lync 2013 desktop clients. Autodiscover is recognized in Lync Server by the required domain name system (DNS) records **lyncdiscover.\<domain\>** and **lyncdiscoverinternal.\<domain\>**. Additionally, newer versions of the Lync 2010 and Lync 2013 desktop client prefer Autodiscover over the domain name system (DNS) SRV records, using DNS SRV records only if lyncdiscover.\<domain\> or lyncdiscoverinternal.\<domain\> does not respond or does not resolve. The Lync Windows Store app for Windows 8 and Lync Mobile uses Autodiscover exclusively and will not refer to the traditional DNS SRV records.

In Lync Server 2013, Autodiscover is expanded to communicate to the client which elements, features, and communication methods are available to the client. The information is communicated through a request that is sent from the client, and the Lync Server web services responds with a clearly defined response that names what is available to the client, and how to contact those features in the format of the Autodiscover Response document.

The best way to understand the Autodiscover response document, including how the web services communicate features to clients through this document, is to dissect and define each line in a typical response from the Lync web service Autodiscover response document.

<div class="">


> [!NOTE]  
> In the details that follow, the user has already authenticated to the home server by responding to an authentication request.



</div>

<div class="">


> [!NOTE]  
> The Lync Autodiscover Web Service is defined in the <STRONG>Microsoft Office Protocols</STRONG> in the <STRONG>Open Specifications</STRONG> section of the <STRONG>Microsoft Developer Network</STRONG> (MSDN) library. For details, see the full specification document, "Lync Autodiscover Web Service Protocol," at: <A href="http://go.microsoft.com/fwlink/?linkid=273839">http://go.microsoft.com/fwlink/?LinkId=273839</A>. For details about authentication, see "OC Authentication Web Service Protocol" at <A href="http://go.microsoft.com/fwlink/?linkid=279015">http://go.microsoft.com/fwlink/?LinkId=279015</A>.



</div>

<div>

## The Lync Server Web Service Autodiscover Response

The response returned when the Autodiscover request is sent is the same for an internal or an external client. Some parameters that are location–aware may change. If a client request is received, but the actual pool is other than the one that has been contacted, the user’s home pool will be set for that user. A colleague whose user account is on a different pool, but logging in from the same office, would get a slightly different response. The response indicates the correct Front End Server or Front End pool for that user.

An example of an Autodiscover Response document:

    <AutodiscoverResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" AccessLocation="External">
       <User>
          <SipServerInternalAccess fqdn="pool01.contoso.com" port="5061"/>
          <SipClientInternalAccess fqdn=" pool01.contoso.com" port="443"/>
          <SipServerExternalAccess fqdn="sip.contoso.com" port="5061"/>
          <SipClientExternalAccess fqdn="sip.contoso.com " port="443"/>
          <Link token ="External/Autodiscover" href="https://webexternal.contoso.com/Autodiscover/AutodiscoverService.svc/root"/>
          <Link token="Internal/Autodiscover" href="https://webinternal.contoso.net/Autodiscover/AutodiscoverService.svc/root"/>
          <Link token="External/AuthBroker" href="https://webexternal.contoso.com/Reach/sip.svc"/>
          <Link token="Internal/AuthBroker" href="https://webinternal.contoso.net/Reach/sip.svc"/>
          <Link token="External/WebScheduler" href="https://webexternal.contoso.com/Scheduler"/>
          <Link token="Internal/WebScheduler" href="https://webinternal.contoso.net/Scheduler"/>
          <Link token="External/Mcx" href="https://webexternal.contoso.com/Mcx/McxService.svc"/>
          <Link token="Internal/Mcx" href="https://webexternal.contoso.net/Mcx/McxService.svc"/>
          <Link token="External/Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
          <Link token="Internal/Ucwa" href="https://webinternal.contoso.net/ucwa/v1/applications"/>
          <Link token="Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
          <Link token="External/XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
          <Link token="Internal/XFrame" href="https://webinternal.contoso.net/Autodiscover/XFrame/XFrame.html"/>
          <Link token="XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
          <Link token="Self" href="https://webexternal.contoso.net/Autodiscover/AutodiscoverService.svc/root/user"/>
       </User>
    </AutodiscoverResponse>

<div>

## Autodiscover Response Document Details

The Autodiscover Response document can be in one of two formats. The default format is a JavaScript Object Notation (JSON). The other format is extensible markup language (XML) document. The XML is used for this example. The request and response are predictable because the document has a defined schema that determines the format. The line in the document that describes the schema used is the first line in the request or response:

    <AutodiscoverResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" AccessLocation="External">

The definition of **AccessLocation=”External”** indicates that the request was made from an external user.

    <SipServerInternalAccess fqdn="pool01.contoso.com" port="5061"/>

&nbsp;

    <SipServerExternalAccess fqdn="sip.contoso.com" port="5061"/>

SipServerInternalAccess and SipServerExternalAccess are currently not used. These entries are reserved for future use.

    <SipClientInternalAccess fqdn=" pool01.contoso.com" port="443"/>

&nbsp;

    <SipClientExternalAccess fqdn="sip.contoso.com " port="443"/>

SipClientInternalAccess and SipClientExternalAccess describe the fully qualified domain name and port that an internal or external client will use to access the defined SIP Server. The Lync desktop client and the Lync Windows Store app use these entries, based on their location (internal or external) to find the Director or Front End Server.

    <Link token="Internal/Autodiscover" href="https://webinternal.contoso.net/Autodiscover/AutodiscoverService.svc/root"/>

&nbsp;

    <Link token ="External/Autodiscover" href="https://webexternal.contoso.com/Autodiscover/AutodiscoverService.svc/root"/>

The `Autodiscover` references contain the service entry points for the Autodiscover service. The token attribute contains the name of the service, and the href is a URL that defines for the client where the service can be found. Clients on an external network use the `External/Autodiscover`. The Autodiscover service is installed as part of the deployment process. `Internal/Autodiscover` is not currently used, and is reserved for future use.

    <Link token="Internal/AuthBroker" href="https://webinternal.contoso.net/Reach/sip.svc"/>

&nbsp;

    <Link token="External/AuthBroker" href="https://webexternal.contoso.com/Reach/sip.svc"/>

The `AuthBroker` references contain the service entry points for the internal and the external authentication broker service, in this case, sip.svc. The token attribute contains the name of the service, and the href is a URL that defines for the client where the service can be found. Clients on the internal network with use `Internal/AuthBroker`. Clients on an external network use the `External/AuthBroker`. The AuthBroker service is installed as part of the deployment process of your internal Lync Server 2013 deployment web services.

    <Link token="Internal/WebScheduler" href="https://webinternal.contoso.net/Scheduler"/>

&nbsp;

    <Link token="External/WebScheduler" href="https://webexternal.contoso.com/Scheduler"/>

The `WebScheduler` token references the URLs for client access to the web-based scheduling for Lync Server conferences. Currently, only the `External/WebScheduler` is used. The WebScheduler is installed as part of the deployment process of your internal Lync Server 2013 deployment web services.

    <Link token="Internal/Mcx" href="https://webexternal.contoso.net/Mcx/McxService.svc"/>

&nbsp;

    <Link token="External/Mcx" href="https://webexternal.contoso.com/Mcx/McxService.svc"/>

`Internal/Mcx` and `External/Mcx` are the locations of the Mobility services, introduced in Cumulative Update for Lync Server 2010: November 2011. These references will continue to be used by Lync 2010 Mobile on all supported devices. The Mcx service is installed as part of the deployment process of your internal Lync Server 2013 deployment web services.

    <Link token="Internal/Ucwa" href="https://webinternal.contoso.net/ucwa/v1/applications"/>

&nbsp;

    <Link token="External/Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>

&nbsp;

    <Link token="Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>

**Internal/Ucwa**, **External/Ucwa** and **Ucwa** provide a means for clients to access the Unified Communications Web Application Programming Interface (UCWA API, or simply UCWA). `Internal/Ucwa` and `External/Ucwa` virtual directories are access points reserved for future feature enhancement, and are not used. The `Ucwa` virtual directory is used for Microsoft Lync Mobile (introduced with Lync Server 2013) on all supported devices. The UCWA service is installed as part of the deployment process of your internal Lync Server 2013 deployment web services.

    <Link token="Internal/XFrame" href="https://webinternal.contoso.net/Autodiscover/XFrame/XFrame.html"/>

&nbsp;

    <Link token="External/XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>

&nbsp;

    <Link token="XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>

`Internal/XFrame`, **External/XFrame** and **XFrame** provide access for UCWA-based server applications. XFrame is installed as part of the deployment process of your internal Lync Server 2013 deployment web services.

    <Link token="Self" href="https://webexternal.contoso.net/Autodiscover/AutodiscoverService.svc/root/user"/>

The `Self` token refers to information specific to the client (user response type) that is making the request. The client that made this request was external, and this Autodiscover reference is to the user portion of the Autodiscover service.

</div>

</div>

<div>

## See Also


[System requirements for external user access components for Lync Server 2013](lync-server-2013-system-requirements-for-external-user-access-components.md)  
[Planning for Autodiscover in Lync Server 2013](lync-server-2013-planning-for-autodiscover.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

