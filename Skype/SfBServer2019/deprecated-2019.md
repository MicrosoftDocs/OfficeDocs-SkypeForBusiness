---
title: "Skype for Business Server 2019 deprecations"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 6/31/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: These features have been removed from Skype for Business Server 2019."
---

# What's deprecated or removed from Skype for Business Server 2019 

[!INCLUDE [disclaimer](disclaimer.md)]

Learn about the features and functionality that are deprecated or removed in Skype for Business Server 2019.

Some deprecated features are included in Skype for Business Server 2019 for compatibility with previous product versions. For information about new features in SharePoint Server 2016, see New and improved features in SharePoint Server 2016.


## Features deprecated in Skype for Business Server 2019

The following features and functionality have been deprecated or removed in Skype for Business Server.

### XMPP Gateways for Skype for Business Server

Skype for Business Server 2015 and its predecessors allowed you to configure an Extensible Messaging and Presence Protocol (XMPP) proxy on the Edge Server and an XMPP Gateway on the Front End Server or Front End pool. This functionality is no longer available in Skype for Business Server 2019.

If you want to keep this functionality, See [Migrating XMPP federation](migration/migrating-xmpp-federation.md) for more information.

### Persistent chat for Skype for Business Server

Persistent Chat Server is an optional role that lets multiple users in your organization participate in chat room conversations that persist over time. Persistent chat cannot be deployed with Skype for Business Server 2019. This server role is removed from Topology Builder, as well as from the code. 

The same functionality is available in Teams. If you need to maintain this functionality, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.  

### SQL Mirroring for Skype for Business Server

SQL Mirroring cannot be deployed with Skype for Business Server 2019. Other options for providing HADR are still supported and you should choose from among them.

### In-place upgrades 

In-place upgrades were available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migration to Skype for Business Server 2019](migration/migration-to-skype-for-business-server-2019.md) for more information.

###  Mobility Service (MCX)

MCX support used by legacy mobile clients is no longer available in Skype for Business Server 2019. This was previously announced in Skype for Business Server 2015.

All mobile clients will use Unified Communications Web API (UCWA). Users with legacy clients using MCX will need to upgrade to a current client.


## Tools

The following tools will not be available for use at the initial release of Skype for Business Server 2019, but will be available afterwards:

- Call Quality Dashboard <!-- see Vijay Manian -->
- KHI Resources <!-- see David Chow -->
- Statistics Manager for Skype for Business Server 2019 <!-- see David Chow -->
- Skype for Business Server 2019 Resource Kit Tools (some tools removed) <!-- See Dave Howe for cut list -->
- Networking Guide: CQM Scorecard, Call Quality Methodology, KHI <!-- Will not Evergreen, may add notes claiming it still applies, contact Aaron Steele -->
- Centralized Logging Service in Skype for Business 2019 <!-- see Sushil -->
- Manage Skype for Business Server 2015 using SCOM Management pack <!-- see David Chow -->
- Skype for Business Server 2015 Capacity Planning Calculator <!-- see Huiwen -->
- Skype for Business Server 2015, Debugging Tools <!-- see Sushil -->

The following tools will not be updated for use with Skype for Business Server 2019:

- Microsoft Call Quality Methodology Scorecard, v1.5 <!-- see Rahul-->
- CQM Poster for Skype for Business <!-- see Rahul-->
- CQM Poster for Lync 2013 <!-- see Rahul-->
- Skype for Business Server 2015 Planning Tool 
- Skype for Business Server 2015 Stress and Performance Tool <!-- see Mira -->

## Legacy clients

Clients released prior to Lync 2013 are no longer supported.

