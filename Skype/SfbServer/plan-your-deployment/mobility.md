---
title: "Plan for Mobility for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
ms.date: 2/17/2018
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 7117eff5-6860-4673-b366-afe0756c4bb2
description: "Plan for your implementation of Mobility for Skype for Business Server."
---

# Plan for Mobility for Skype for Business Server
 
Plan for your implementation of Mobility for Skype for Business Server.
  
With Skype for Business Server, you can deploy the Mobility feature to provide Skype for Business Server functionality on mobile devices. This article provides details about the Mobility feature, and helps you plan for your deployment.
  
The Mobility feature for Skype for Business Server is able to support mobile clients for Skype for Business, as well as Lync clients going back to 2010. Once it's deployed, your users can connect to your Skype for Business Server deployment using supported iOS, Android and Windows Phone mobile devices to take advantage of several different features, including Enterprise Voice features. We've included a partial list below, and you can also check [Desktop client feature comparison for Skype for Business](clients-and-devices/desktop-feature-comparison.md) for more info:
  
- Send and receive messages
    
- View presence
    
- View contacts
    
- Click to join a conference
    
- Call via work
    
- Single number reach
    
- Voice mail
    
- Missed call notification
    
- Voice over IP (VoIP)
    
- Attendee video (H.264)
    
- Viewing meeting content (PowerPoint and desktop/application sharing)
    
All this is accomplished through the Unified Communications Web API, or UCWA. UCWA was first introduced in Lync Server 2013, and it's still in use for Skype for Business Server. There's an additional functionality for communicating with Lync 2010 clients, and that's Mobility Service (MCX). These are complimentary services, allowing for Lync Server 2010 and 2013 clients, as well as Skype for Business clients, to access Skype for Business Server deployments successfully.
  
> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
It's important to note that while all these features are available once Mobility has been implemented, they may work a little differently on some devices. We've got a website that discusses what features work on what devices, at [Mobile client feature comparison for Skype for Business](clients-and-devices/mobile-feature-comparison.md). We also have some great device and OS information at [Plan for clients and devices](clients-and-devices/clients-and-devices.md).
  
Mobility makes use of the Autodiscover feature, which allows clients to automatically locate Skype for Business Server web services without users needing to enter in any URLs (they won't even need to know them). If you need to do some troubleshooting, manual entry of URLs is still supported.
  
Push notifications are also supported, for when the Skype for Business app isn't running in the background (or for mobile devices that don't support applications running in the background). A push notification is sent to a mobile device about an event that occurs when the device or app is inactive. A good example is missing an IM message when your phone's not active, which would result in a push notification being sent (this is presented as a toast or notification, like when the app is running in the background). With push notifications, users won't miss IM or voice calls.
  
For more information, we have the following sections:
  
- [Mobility components](mobility.md#MobilityComponents)
    
- [Supported topologies](mobility.md#SupportedTopos)
    
- [Technical requirements](mobility.md#TechRequirements)
    
- [Defining your Mobility needs](mobility.md#MobilityNeeds)
    
## Mobility components
<a name="MobilityComponents"> </a>

There are four services that comprise Mobility for Skype for Business Server:
  
- **Unified Communications Web API (UCWA)**
    
    Provides services for real-time communications with mobile and web clients for Skype for Business Server. When Skype for Business Server is deployed, a UCWA virtual directory's created in the internal and external web services. A virtual component in this virtual directory that accepts calls from UCWA-enabled clients. The client apps communicate over a representational state transfer (REST) interface for:
    
  - presence
    
  - contacts
    
  - instant messaging (IM)
    
  - VoIP
    
  - video conferencing
    
  - collaboration
    
    UCWA uses a P-GET based channel to send events, such as an incoming call, incoming IM, or a message to the client app.
    
- **Mobility service (MCX)**
    
    Supports Skype for Business Server functionality, such as IM, presence, and contacts, on mobile devices. The Mobility service is installed on every Front End Server in each pool that's intended to support Skype for Business Server functionality on mobile devices. When you install Skype for Business Server 2015 a new virtual directory (Mcx) is created under both the internal and external websites on your Front End Servers.
    
    > [!NOTE]
    > MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
- **Autodiscover service**
    
    Identifies the location of the user and enables mobile devices and other Skype for Business clients to locate resources (such as the internal and external URLS for Skype for Business Server Web Services, the Mcx URL , or UCWA URL) regardless of network location. Automatic discovery uses hardcoded host names (lyncdiscoverinternal for users inside the network, lyncdiscover for users outside the network), and the SIP domain of the user. It supports client connections that use either HTTP or HTTPS. 
    
    The Autodiscover service is installed on every Front End Server and on every Director in each pool that's intended to support Skype for Business Server functionality on mobile devices. When you install the service, a new virtual directory (Autodiscover) is created under both the internal and external websites on your Front End Servers and Directors.
    
- **Push notification service**
    
    A cloud-based service that's located in your Skype for Business Online data center. On phones that don't have Skype for Business client running in the background, when a new event happens, notification of a missed event (called a push notification) gets sent to the mobile device instead. The Mobility service sends a notification to the push notification service (MPNS), which then sends it to the mobile device. The user can then respond to the notification on their mobile device to activate the app. An Edge Server is required for this functionality.
    
## Supported topologies
<a name="SupportedTopos"> </a>

We have the following supported Skype for Business Server applications for your topology planning:
  
- Mobility Standard Edition
    
- Mobility Enterprise Edition
    
You should be able to use this functionality with Skype for Business Server Edge Servers or Lync Server 2013 Edge Servers.
  
The Mobility service is supported on Front End Servers when collocated with the Mediation Server role, with two network interfaces, but you need to take appropriate steps to configure those interfaces. You'll need to assign IP addresses to the specific interface that will communicate as the Mediation Server, and the network IP interface that will communicate as the Front End Server. You can do this in Topology Builder by selecting the correct IP address for each service, instead of using the default **Use all configured IP addresses** selection.
  
## Technical requirements
<a name="TechRequirements"> </a>

It's important to plan for the various mobile application scenarios your mobile users may encounter. For example, someone might start using a mobile app outside of work by connecting through a 3G network, then switch to the corporate Wi-Fi network when they reach work. They may switch to 4G when leaving their building. Planning now will allow you to support these network transitions and guarantee a consistent user experience.
  
### DNS configuration

The Mobility services Mcx and UCWA use DNS in the same way. With Automatic Discovery, mobile devices use DNS to locate resources. During DNS lookup, a connection's attempted to the FQDN that's associated with the internal DNS record (lyncdiscoverinternal.[internal domain name]). If the internal DNS record can't be used to make that connection, a second connection is attempted, this time to the external DNS record (lyncdiscover.[sipdomain]). So why have two? A mobile device that's internal to your network will be able to use the internal Autodiscover URL. External mobile devices will use the external Autodiscover URL. In either case, the Autodiscover service will return all Web service URLs for the user's home pool, which includes the Mobility service (Mcx and UCWA).
  
It's expected that the external Autodiscover requests will go through the reverse proxy you've configured for Skype for Business Server. However, both the internal Mobility service URL and the external Mobility service URL are associated with the external Web Services FQDN. Therefore, regardless of whether a mobile device is internal or external to your network, the device always connects to the Skype for Business Server Mobility service externally, through your reverse proxy.
  
> [!NOTE]
> As we just noted, all Mobility service traffic (internal and external) will go through your reverse proxy. But sometimes an issue comes up when the internal traffic leaves through an interface, only to then try and come back in on the same interface. This can violate your spoofing (formally it's called TCP packet spoofing) security rules. You'll need to allow **Hair Pinning** to have Mobility function.
  
> [!NOTE]
> If you're ready to do this, you can also choose to use a reverse proxy that's separate from your firewall (for security purposes, spoofing prevention should always be enforced at your firewall). This way, the hairpin can happen at the external interface of your reverse proxy, rather than your firewall's external interface. This allows you to detect the spoofing properly at your firewall while you relax the rule at your reverse proxy, and you get your Mobility functionality. 
  
> [!NOTE]
> If you go this route, be sure to use the DNS host or CNAME records to define the reverse proxy for the hairpin behavior (not the firewall), if possible. 
  
There are some things you'll need to configure to support users inside and outside your corporate network.
  
These are the rules for internal and external web FQDNs:
  
- New CNAME or A (host, if IPv6, AAAA) DNS records, for automatic discovery.
    
- New firewall rule, if you want to support push notifications through your Wi-Fi network.
    
- Subject alternative names on internal server certificates and reverse proxy certificates, for automatic discovery.
    
- Front End Server hardware load balanced configuration changes source affinity.
    
These are the topology requirements needed to support the Mobility Service and Autodiscover Service:
  
- The Front End pool internal web FQDN must be distinct from the Front End pool external web FQDN.
    
- The internal web FQDN must only resolve to, and be accessible from, inside the corporate network.
    
- The external web FQDN must only resolve to, and be accessible from, the internet.
    
- For a user inside the corporate network, the Mobility service URL must be addressed to the external web FQDN. This requirement is for the Mobility service, and applies only to this URL.
    
- For a user outside the corporate network, the request must go to the external web FQDN of the Front End pool or Director.
    
If you support automatic discovery, you'll need to make the following DNS records for each SIP domain:
  
- An internal DNS record to support mobile users who connect from inside your organization's network.
    
- An external, or public, DNS record to support mobile users who connect from the internet.
    
The internal automatic discovery URL shouldn't be addressable from outside your internal network. The external automatic discovery URL shouldn't be addressable from within your network. But if this isn't possible for the external URL, your mobile client functionality probably won't be affected, because the internal URL will always be tried first.
  
### Port and Firewall requirements

We've covered most of this in our other documentation, but specifically for Mobility, you're going to want to have the following ports open on your enterprise Wi-Fi network if you have any users homed on a Survivable Branch Appliance (SBA):
  
- UcwaSipExternalListeningPort requires 5088.
    
- UcwaSipPrimaryListeningPort requires 5089.
    
### Certificate requirements

If you're using automatic discovery for your Skype for Business mobile clients, you'll need to modify the SAN (subject alternative name) lists on your certificates to support secure connections from your mobile clients. If you already have certificates in-place, you'll need to request and assign new certificates with the SAN entries described here. This will need to be done for each Front End Server and Director (if in your environment) that runs the Autodiscover service. We'd also recommend modifying the SAN lists on your reverse proxy certificates, adding SAN entries for every SIP domain in your organization.
  
This should be a straightforward process if you're requesting the new certs off an internal CA (certificate authority), but public certificates are more complex, and potentially a lot more expensive to re-request, not to mention it may be costly to add a lot of SIP domains to a new public cert. In that situation, there is an approach that's supported, but **not recommended**. You can configure your reverse proxy to make the initial Autodiscover service request over port 80, which will use HTTP, rather than port 443, which is HTTPS (and 443 is the default configuration). That incoming request will be redirected to port 8080 on your Front End pool or Director. By doing this, you won't need to make any certificate changes, because this traffic isn't using HTTPS for requests. But again, we don't recommend this, although it will work for you.
  
### Windows and IIS requirements

You should have a supported Windows Server version for your Skype for Business Server environment. As a result, you should also have IIS 8 or IIS 8.5 for your mobility needs. There will need to be some changes to the default ASP.NET settings, but the Mobility service installer will do that automatically.
  
### HLB requirements

If you're using a topology for Skype for Business Server that includes an HLB for your Front End pool (which would be any topology that includes more than one Front End Server), the external Web Services virtual IPs (VIPs) for Web Services traffic need to be configured for source. Source affinity helps to ensure that multiple connections from a single client are sent to the same server to maintain session state.
  
If you plan to support Skype for Business mobile clients only over your internal Wi-Fi network, you should configure your internal Web Services VIPs for source as described for external Web Services VIPs. In this situation, you should use source_addr (or TCP) affinity for the internal Web Services VIPs on the HLB.
  
For details on all this, please review the [Load balancing requirements for Skype for Business](network-requirements/load-balancing.md) documentation.
  
### Reverse Proxy requirements

In order to support automatic discovery for Skype for Business mobile clients, you'll need to update the current publishing rule as follows:
  
- If you decide to update the SAN lists on your reverse proxy certificates, and you're using HTTPS for the initial Autodiscover service request, you need to update the web publishing rule for lyncdiscover.\<sipdomain\>. This is typically combined with the publishing rul for the external Web Services URL on the Front End pool.
    
- If you've decided to use HTTP for the initial Autodiscover service request to avoid having to update the SAN list for your reverse proxy certificates (which we don't recommend), you'll need to create a new web publishing rule for port HTTP/TCP 80, if there isn't one already. If that rule exists, update it to include a lyncdiscover.\<sipdomain\> entry.
    
## Defining your Mobility needs
<a name="MobilityNeeds"> </a>

Now that we've reviewed the topologies, components and technical requirements, let's look at what your organization may need in terms of a Mobility implementation.
  
### Do you want to use automatic discovery for Skype for Business mobile clients?

We do strongly recommend that you do use automatic discovery. It will require the creation of new internal and external DNS records, as documented in the Technical Requirements section above. With automatic discovery, the Skype for Business clients can automatically locate Skype for Business Server Web Services from any location, without needing a URL to be entered in manually.
  
You can use manual settings if you need to. These URLs will need to be entered by users into their mobile devices:
  
- **https://\<ExtPoolFQDN\>/Autodiscover/autodiscoverservice.svc/Root** for external access.
    
- **https://\<IntPoolFQDN\>/Autodiscover/autodiscoverservice.svc/Root** for internal access.
    
Again, we do recommend using automatic discovery. You may find manual settings useful for troubleshooting purposes.
  
### Are you going to support push notifications?

Push notifications are used for mobile applications that support this functionality to notify a user of events while the app's not active. Your Edge Server will need to have a federation relationship with your cloud-based Skype for Business Server Push Notification Service, which is found on the Skype for Business Online datacenter. You'll need to run a cmdlet to enable push notifications.
  
> [!NOTE]
> If you have anyone still using Lync Server 2010 clients, they will need TCP port 5223 open outbound on your enterprise WiFi network. 
  
### Do you want all your users accessing all Mobility features, or do you want to specify the users who can access these features instead?

We have a table to help with some of the features that are available to all users, and whether they're set that way or not by default. For a complete list, please review [New-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/new-csmobilitypolicy?view=skype-ps).
  
> [!NOTE]
> The scopes for all these features are Global/Site/User. 
  
|**Feature**|**Parameter Name**|**Description**|**Default Setting**|
|:-----|:-----|:-----|:-----|
|Enable Mobility  <br/> |EnableMobility  <br/> |Controls users in a given scope who have Skype for Business mobile client installed. If the policy is set to False, your users won't be able to sign in with their client.  <br/> |True  <br/> |
|Outside Voice  <br/> |EnableOutsideVoice  <br/> |Enables a user's ability to use Call Via Work, which lets users send and receive calls by using their work number instead of their mobile number. If it's set to False, your users won't be able to make or receive calls on their mobile phone when using their work phone number.  <br/> |True  <br/> |
|Enable IP Audio and Video  <br/> |EnableIPAudioVideo  <br/> |Set to the default, it allows a user to use VoIP to make or receive phone or video calls on their mobile device. When set to False, your users won't be able to use their mobile device to do either of those things.  <br/> |True  <br/> |
|Require WiFi for IP Audio  <br/> |RequireWiFiForIPAudio  <br/> |Defines whether a client will need to make and receive calls over VoIP on WiFi instead of a cellular data network. If it's set to True, your users will only be able to make and receive VoIP calls when they're connected via WiFi.  <br/> |False  <br/> |
|Require WiFi for IP Video  <br/> |RequireWiFiForIPVideo  <br/> |Defines whether a client will need to make and receive video calls on WiFi instead of a cellular data network. If it's set to True, your users will only be able to make and receive VoIP calls when they're connected via WiFi.  <br/> |False  <br/> |
   
### Should users who aren't enabled for Enterprise Voice be able to use Click to Join to join conferences?

For users to have access to Mobility features and Call via Work, they need to be enabled for Enterprise Voice. But even if they aren't enabled, they can still join conferences by clicking on a link on their mobile device, but only if they have an appropriate Voice policy assigned to them. You can either:
  
- assign a specific Voice policy to these users, or,
    
- make sure that a global policy or site-level policy exists and applies to them.
    
Either way, the Voice policy you assign needs to have public switched telephone network (PSTN) usage records and routes that will define where your users will be able to dial out to join conferences.
  
> [!NOTE]
> Mobile users who want to use Click to Join require a Voice policy, along with the related PSTN usage records and voice routes, because when they click on that link on their mobile devices, an outbound call from Skype for Business Server will be the result. 
  

