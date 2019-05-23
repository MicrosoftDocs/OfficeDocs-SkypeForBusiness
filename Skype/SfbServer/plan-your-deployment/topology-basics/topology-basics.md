---
title: "Topology Basics for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 113e8c3f-71de-435c-bc4a-918ac7b50008
description: "Summary: Choose your topology for Skype for Business Server. Learn about server collocation for Skype for Business Server."
---

# Topology Basics for Skype for Business Server

**Summary:** Choose your topology for Skype for Business Server. Learn about server collocation for Skype for Business Server.

Before preparing anything else, you'll want to know you're planning for the right topology for your deployment of Skype for Business Server. The first thing you need to decide is if you're going to have an on-premises deployment of Skype for Business Server, or if you're going to combine this with a Skype for Business Server Online deployment in a Hybrid deployment. Either way, you're going to want to read further, as we'll detail the on-premises topologies here, but the Hybrid details are documented in their own section.

You can also see some example topologies in [Reference topologies for Skype for Business Server](reference-topologies.md).

## Sites

In Skype for Business Server, you define sites on your network that contain Skype for Business Server components. A site is a set of computers that is well-connected by a high-speed, low-latency network, such as a single local area network (LAN) or two networks connected by a high-speed fiber optic network. Note that Skype for Business Server sites are a separate concept from Active Directory Domain Services sites and Microsoft Exchange Server sites. Your Skype for Business Server sites do not need to correspond to your Active Directory sites.

Skype for Business Server supports on-premises deployment of one or more sites that can be scaled according to your high availability and location requirements.

Your deployment will have at least one central site (also called a datacenter, this is a datacenter for all the servers located in it), and each central site in your deployment will have one Standard Edition server, or at least one Enterprise Edition Front End pool. You can see the differences in each option below:

- Standard Edition server includes a collocated SQL Server Express database.

- Enterprise Edition Front End pool includes:

  - One or more Front End Servers (Ideally at least three, for scalability), with a maximum of twelve. Load-balancing would be required for more than one server.

  - A separate Back End Server.

You can learn more about the various server roles a little later in this section.

In addition to your central sites, you may also end up having one or more branch sites associated with your central site. They depend on the central site for almost all their functionality, so what are they made up of, exactly?

- Survivable Branch Appliance, which combines a public switched telephone network (PSTN) gateway, with some Skype for Business Server functionality.

- Survivable Branch Server, it's a server running Windows Server that has Skype for Business Server Registrar and Mediation Server software installed.

- Stand-alone PSTN gateway (which isn't part of the Survivable Branch Appliance).

- Stand-alone Mediation Server or stand-alone Mediation Server pool (if you don't want to collocate this role with the Survivable Branch Appliance).

## What's in a Skype for Business Server site?

To get into more detail, a central site can also have:

- Multiple Front End pools, in the same domain or different domains (remember in planning that all the Front End Servers in a Front End pool, along with the Back End Servers for the pool, do have to be in the same domain).

- Multiple Standard Edition servers.

- Office Web Apps Server, which is used with Office Web Apps in Skype for Business Server for sharing and rendering of PowerPoint presentations.

- Edge Server or Edge pool (in a perimeter network). Needed if you want your deployment to support federated partners, public IM connectivity, extensible messaging and presence protocol (XMPP) gateway, and remote user access. More details can be found in the Edge Server Planning documentation.

- Persistent Chat Server. Useful if you want users to be able to take part in multiparty, topic-based conversations that persist over time. There's more information at the Planning for Persistent Chat Server topic.

- Monitoring. Used to support data collection for audio/video (A/V) Quality of Experience (QoE) and call detail recording (CDR) for Enterprise Voice and A/V conferences in your deployment. We discuss it in detail at the Planning for Monitoring topic.

- Director or Director pool. Not required, but useful if you want to improve resiliency and enable redirection of Skype for Business user requests to the user's home pool. If you want to deploy Directors, a maximum of 10 per pool is supported. If this is something you need, definitely continue reading at the Planning for Directors topic.

- Reverse proxy. This isn't a Skype for Business Server component, but if you want to support the sharing of web content for federated users, if you intend to support Mobility traffic, if your remote users want to use the address book, join meetings, and so on, this is something you'll want to have in your environment. There's a Setting up Reverse proxy server topic you can check out for more details, when you're ready.

Additional information on collocation for these servers can be found below.

All the Front End pools and Standard Edition servers deployed at your central site share the following, assuming you've deployed them:

||||
|:-----|:-----|:-----|
|Director or Director pool  <br/> |Stand-alone Mediation Server or Mediation Server pool  <br/> |Office Web Apps Server  <br/> |
|Edge Server or Edge pool  <br/> |Persistent Chat Server or Persistent Chat Server pool  <br/> |Monitoring  <br/> |

Where is Exchange Unified Messaging (UM) Server in this list? Well, you can certainly use it with Skype for Business Server if you want to integrate with Exchange UM, but it's not a component of the Skype for Business Server site, so we're not mentioning it here.

You may be planning to have multiple central site, and if that's so, they can share the following servers and roles, if they're deployed on your central site:

|||
|:-----|:-----|
|Stand-alone Mediation Server or Mediation Server pool  <br/> |Edge Server or Edge pool  <br/> |
|Persistent Chat Server or Persistent Chat Server pool  <br/> |Monitoring  <br/> |

Just like the last list, we aren't including the Exchange UM Server here because it's not part of the Skype for Business Server deployment, but it falls into the same category here, too.

There are some other components and options that go into deployments, of course.

|||||
|:-----|:-----|:-----|:-----|
|Firewalls  <br/> |PSTN gateways (if you deploy Enterprise Voice  <br/> |Exchange UM Server (if you want to integrate with Exchange UM)  <br/> |DNS load balancing  <br/> |
|Hardware load balancers  <br/> |SQL Server databases  <br/> |File shares  <br/> ||

## Server roles

Each server running Skype for Business Server runs one or more server roles. A server role is a defined set of Skype for Business Server functionalities provided by that server. You don't need to deploy all available server roles in your network. Install only the server roles that contain the functionality that you want.

For most server roles, for scalability and high availability you can deploy pools of multiple servers all running the same server role. Each server in a pool must run an identical server role or roles. For most types of pools in Skype for Business Server, you must deploy a load balancer to spread traffic between the various servers in the pool. Skype for Business Server supports both Domain Name System (DNS) load balancing and hardware load balancers.

### Front End Server and Back End Server

In Skype for Business Server Enterprise Edition, the Front End Server is the core server role, and runs many basic Skype for Business Server functions. The Front End Server, along with the Back End Servers, are the only server roles required to be in any Skype for Business Server Enterprise Edition deployment.

A Front End pool is a set of Front End Servers, configured identically, that work together to provide services for a common group of users. A pool of multiple servers running the same role provides scalability and failover capability.

The Front End Server includes the following:

- User authentication and registration.

- Presence information and contact card exchange.

- Address book services and distribution list expansion.

- IM functionality, including multiparty IM conferences.

- Web conferencing, PSTN Dial-in conferencing and A/V conferencing (if deployed).

- Application hosting, for both applications included with Skype for Business Server (for example, Conferencing Attendant and Response Group application), and third-party applications.

- Optionally, Monitoring, to collect usage information in the form of call detail records (CDRs) and call error records (CERs). This information provides metrics about the quality of the media (audio and video) traversing your network for both Enterprise Voice calls and A/V conferences.

- Web components to supported web-based tasks such as web scheduler and join launcher.

- Optionally, Archiving, to archive IM communications and meeting content for compliance reasons. For details, see [Planning for Archiving](https://technet.microsoft.com/library/898b83c1-007b-43be-9484-08fe49c10951.aspx) in the Planning documentation.

    In Lync Server 2010 and prior versions, Monitoring and Archiving were separate server roles, not collocated on Front End Server.

- Optionally, if Persistent chat is enabled, Persistent Chat Web Services for Chat Room Management and Persistent Chat Web Services for File Upload/Download.

Front End Pools are also the primary store for user and conference data. Information about each user is replicated among three Front End Servers in the pool, and backed up on the Back End Servers.

Additionally, one Front End Server in the deployment also runs the Central Management Server, which manages and deploys basic configuration data to all servers running Skype for Business Server. The Central Management Server also provides Lync Server Management Shell and file transfer capabilities.

The Back End Servers are database servers running Microsoft SQL Server that provide the database services for the Front End pool. The Back End Servers serve as backup stores for the pool's user and conference data, and are the primary stores for other databases such as the Response Group database. You can have a single Back End Server, but [Back End Server high availability in Skype for Business Server](../high-availability-and-disaster-recovery/back-end-server.md) is recommended for failover. Back End Servers do not run any Skype for Business Server software.

> [!IMPORTANT]
> We do not recommend collocating Skype for Business Server databases with other databases. If you do so, availability and performance may be affected.

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The  AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances (FCI), and SQL failover clustering methods are preferred with Skype for Business Server 2019.

Information stored in the Back End Server databases includes presence information, users' Contacts lists, conferencing data, including persistent data about the state of all current conferences, and conference scheduling data.

### Edge Server

Edge Server enables your users to communicate and collaborate with users outside the organization's firewalls. These external users can include the organization's own users who are currently working offsite, users from federated partner organizations, and outside users who have been invited to join conferences hosted on your Skype for Business Server deployment.

Deploying Edge Server also enables mobility services, which supports Lync functionality on mobile devices. Users can use supported Apple iOS, Android, Windows Phone, or Nokia mobile devices to perform activities such as sending and receiving instant messages, viewing contacts, and viewing presence. In addition, mobile devices support some Enterprise Voice features, such as click to join a conference, Call via Work, single number reach, voice mail, and missed calls. The mobility feature also supports push notifications for mobile devices that do not support applications running in the background. A push notification is a notification that is sent to a mobile device about an event that occurs while a mobile application is inactive.

Edge Servers also include a fully-integrated Extensible Messaging and Presence Protocol (XMPP) proxy, with an XMPP gateway included on Front End Servers. You can configure these XMPP components to enable your Skype for Business Server users to add contacts from XMPP-based partners for instant messaging and presence.

> [!NOTE]
> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information.

### Mediation Server

Mediation Server is a necessary component for implementing Enterprise Voice, Call Via Work, and dial-in conferencing. Mediation Server translates signaling, and, in some configurations, media between your internal Skype for Business Server infrastructure and a public switched telephone network (PSTN) gateway, IP-PBX, or a Session Initiation Protocol (SIP) trunk. You can run Mediation Server collocated on the same server as Front End Server, or separated into a stand-alone Mediation Server pool.

For details, see [Mediation Server component in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/mediation-server.md).

### Video Interop Server

Video Interop Server is a new role as of Skype for Business Server 2015. It enables you to integrate your Skype for Business Server deployment with certain third-party VTC (Video Teleconferencing System) solutions. A VIS acts as an intermediary between a 3rd party teleconference system and a Skype for Business Server deployment. For this release, VIS is focused on interoperability with Cisco/Tandberg video systems.

For details, see [Plan for Video Interop Server in Skype for Business Server](../../plan-your-deployment/video-interop-server.md).

### Director

Directors can authenticate Skype for Business Server user requests, but they do not home user accounts or provide presence or conferencing services. Directors are most useful to enhance security in deployments that enable external user access. The Director can authenticate requests before sending them on to internal servers. In the case of a denial-of-service attack, the attack ends with the Director and does not reach the Front End servers.

### Persistent Chat Server Roles

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.

Persistent chat enables users to participate in multiparty, topic-based conversations that persist over time. The Persistent Chat Front End Server runs the persistent chat service. The Persistent Chat Back End Server stores the chat history data, and information about categories and chat rooms. The optional Persistent Chat Compliance Back End Server can store the chat content and compliance events for the purpose of compliance.

Servers running Skype for Business Server Standard Edition can also run Persistent chat collocated on the same server. You cannot collocate the Persistent Chat Front End Server with Enterprise Edition Front End Server.

For details, see [Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md).

## High availability and disaster recovery support

Skype for Business Server provides high availability by server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server. This applies to Front End Servers, Edge Servers, Mediation Servers, and Directors.

Skype for Business Server also provides disaster recovery measures by enabling pool pairing. If you deploy this topology, you will designate pairs of Front End pools, with each pool in a pair located in a separate data center, and in a separate geographical area. If one pool or site goes down, you can redirect the users of that pool to use the other pool in the pair, with minimal interruption of service.

Skype for Business Server also supports several options for Back End Server high availability. These include the following:

- Database mirroring

- AlwaysOn Availability Groups

- AlwaysOn Failover Cluster Instances (FCI)

- SQL failover clustering

For details about pool pairing and Back End Server high availability, see [Plan for high availability and disaster recovery in Skype for Business Server](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md).

## Server collocation in Skype for Business Server

We've used the term collocate already, but what does this mean? Skype for Business Server allows you to locate some server roles and features on the same server, which is collocation, or on different servers, but it can be confusing when you're starting out, and whether you're doing a Standard Edition or Enterprise Edition server deployment (they each come with their own rules). To help with your planning, we're including server collocation in Standard Edition server deployments and Enterprise Edition Front End pool deployments (in most cases this information is identical, and where it's different, it's called out specifically).

### Collocation of server roles

The Standard Edition server has the following role collocated (additional configuration is required though), while in the Enterprise Edition Front End pool, this role can be collocated, or deployed to a separate server:

- Mediation

These server roles must each be deployed on a separate server:

- Director

- Edge

- Video Interop Server

- Office Web Apps

### Databases

This is the area with real differences between Standard Edition server deployments and Enterprise Edition server pool deployments, so we'll have two sections below, followed by some additional rules for both.

#### Standard

Since SQL Server Express is collocated on the Standard Edition server, and can't be moved, this is pretty straightforward. Furthermore, if you deploy Persistent Chat Server on a Standard Edition server, you're also able to collocate the Persistent Chat and the Persistent Chat compliance database on the Standard Edition server too, but you don't have to.

    > [!NOTE]
    > Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.

These can't be collocated on the Standard Edition server, but can go on a single database server of their own:

- Monitoring database

- Archiving database

- Any back-end database for an Enterprise Edition Front End pool

#### Enterprise

The following databases can be collocated on the same back end SQL Server:

- Back End database

- Monitoring database

- Archiving database

- Persistent Chat database

- Persistent Chat compliance database

#### Both

Now, there are some additional rules to follow when collocating Skype for Business Server databases in a single SQL instance, or in multiple SQL instances in the same SQL Server database:

- Each SQL instance can only contain a single back end database for an Enterprise Edition Front End pool, a single Monitoring database, a single Archiving database, a single Persistent Chat database, and a single Persistent Chat compliance database.

- The database server can't support more than one Enterprise Edition Front End pool, one server running Archiving, one server running Monitoring, a single Persistent Chat database, and a single Persistent Chat compliance database, but it can support one of each, regardless of whether the databases use the same instance of SQL Server or separate instances of SQL Server.

    > [!NOTE]
    > Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.

### File shares

The file share can be on a separate server, or you can collocate it on the same server as any or all of the following:

- Database server, including the Back End Server of an Enterprise Edition Front End pool

- Monitoring database

- Archiving database

- Persistent Chat database

- Persistent Chat compliance database

> [!CAUTION]
> Note that while you can collocate the file share on these servers, it's vital to note that we don't recommend it. If you'd collocating the file share with any other server role, please make sure you're monitoring for disk space and performance issues on a regular basis.

### Keep in mind

- You can't collocate a reverse proxy server, which isn't a Skype for Business Server component, and may not even be in your topology. You'll need a reverse proxy if you want to support sharing of web content for federated users, among many other things. If you need to, go ahead and implement reverse proxy support for Skype for Business Server by configuring an existing reverse proxy server that's already in your organization that's being used by other applications.

- You can't collocate any Exchange UM component or SharePoint Server component with any Skype for Business Server role.

## See also

[Reference topologies for Skype for Business Server](reference-topologies.md)
