---
title: "Deployment process for mobility in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5a1cebda-c14b-4ff4-9c36-f7caa868160f

description: "This section describes the sequence of steps required to deploy the Lync Server 2013 mobility feature."
---

# Deployment process for mobility in Lync Server 2013
[]
```
Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013. It is noted accordingly.
```

This section describes the sequence of steps required to deploy the Lync Server 2013 mobility feature.
  
**Mobility Deployment Process**

|**Phase**|**Steps**|**Permissions**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Create Domain Name System (DNS) records  <br/> | Create an internal DNS CNAME or A (host, if IPv6, AAAA) record to resolve the internal Autodiscover Service URL.  <br/>  Create an external DNS CNAME or A (host, if IPv6, AAAA) record to resolve the external Autodiscover Service URL.  <br/> |Domain Admins  <br/> DnsAdmins  <br/> |[Creating DNS records for the Autodiscover Service in Lync Server 2013](creating-dns-records-for-the-autodiscover-service.md) <br/> |
|Modify certificates  <br/> | Add subject alternative name entries to the following certificates to support secure connections for mobile users:  <br/>  Director certificate  <br/>  Front End pool certificate  <br/>  Reverse proxy certificate  <br/> |Local administrator  <br/> |[Modifying certificates for mobility in Lync Server 2013](modifying-certificates-for-mobility.md) <br/> |
|Configure the reverse proxy  <br/> | Assign certificates updated with subject alternative names to the Secure Sockets Layer (SSL) Listener.  <br/>  Reconfigure the web publishing rule for the external Autodiscover Service URL.  <br/>  Be sure that a web publishing rule exists for the external Lync Server 2013 Web Services URL on your Front End pool.  <br/>  Or  <br/>  If you choose to use HTTP for the initial Autodiscover request and do not update subject alternative name lists on the certificates, configure a new web publishing rule or reconfigure an existing publishing rule for port 80 HTTP.  <br/> |Local administrator  <br/> |[Configuring the reverse proxy for mobility in Lync Server 2013](configuring-the-reverse-proxy-for-mobility.md) <br/> |
|Test your mobility deployment for Lync 2010 Mobile using the Mcx Mobility Service  <br/> |Run **Test-CsMcxP2PIM** to test sending an instant message from one person to another.  <br/> See the Lync Server Management Shell cmdlet documentation for [Test-CsMcxP2PIM](test-csmcxp2pim.md) for a complete list of options.  <br/> |CsAdministrator  <br/> |[Verifying your mobility deployment in Lync Server 2013](verifying-your-mobility-deployment.md) <br/> |
|Test your mobility deployment for Lync 2013 Mobile clients using the UCWA Web components  <br/> |Use the **Test-CsUcwaConference** cmdlet to test and verify that pre-defined test users or a pair of actual users can use UCWA to create and participate in a conference.  <br/> See the Lync Server Management Shell cmdlet documentation for [Test-CsUcwaConference](test-csucwaconference.md) for a complete list of options.  <br/> |CsAdministrator  <br/> |[Verifying your mobility deployment in Lync Server 2013](verifying-your-mobility-deployment.md) <br/> |
|Configure for push notifications  <br/> | For Lync Server 2013 Edge Servers, add a Lync Server online hosting provider and configure hosting provider federation.  <br/>  For Lync Server 2010 Edge Servers, add a Lync Server online hosting provider and configure hosting provider federation.  <br/>  For Office Communications Server 2007 R2 Edge Servers, add a federated partner.  <br/>  If you want to support push notifications over a Wi-Fi network, configure a firewall rule outbound for TCP port 5223.  <br/>  Use the **Set-CsPushNotificationConfiguration** cmdlet to enable push notifications to the Apple Push Notification Service (APNS) and Microsoft Push Notification Service (MPNS). This feature is disabled by default.  <br/>  Use the **Test-CsFederatedPartner** cmdlet to test the federation configuration and the **Test-CsMCXPushNotification** cmdlet to test push notifications.  <br/> > [!NOTE]>  Push notifications are used for Lync 2010 Mobile clients on Apple devices and Windows Phone >  Push notification is required for Lync 2013 Mobile clients on Windows Phone only           |RtcUniversalServerAdmins  <br/> |[Configuring for push notifications in Lync Server 2013](configuring-for-push-notifications.md) <br/> |
|Configure mobility policy  <br/> | Use the **Set-CsMobilityPolicy** cmdlet to allow or disallow:  <br/>  Call via Work  <br/>  Enable IP Audio and IP Video  <br/>  Require WiFi for IP Audio and/or IP Video  <br/> |CsAdministrator  <br/> |[Configuring mobility policy in Lync Server 2013](configuring-mobility-policy.md) <br/> |
   

