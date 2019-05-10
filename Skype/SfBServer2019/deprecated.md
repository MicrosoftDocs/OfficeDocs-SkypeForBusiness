---
title: "What's deprecated from Skype for Business Server 2019"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: overview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: These features have been removed from Skype for Business Server 2019."
---

# What's deprecated from Skype for Business Server 2019

Learn about the features and functionality that are deprecated in Skype for Business Server 2019. For information about new features in Skype for Business Server 2019, see [What's in Skype for Business Server 2019](whats-new.md).

Some de-emphasized features are included in Skype for Business Server 2019 for compatibility with previous product versions.

## Features deprecated in Skype for Business Server 2019 

    The following features and functionality have been deprecated in Skype for Business Server 2019.

### XMPP Gateways for Skype for Business Server

Skype for Business Server 2015 and its predecessors allowed you to configure an Extensible Messaging and Presence Protocol (XMPP) proxy on the Edge Server and an XMPP Gateway on the Front End Server or Front End pool. This functionality is no longer available in Skype for Business Server 2019.

### Persistent Chat for Skype for Business Server

Persistent Chat Server is an optional role that lets multiple users in your organization participate in chat room conversations that persist over time. Persistent chat can't be deployed with Skype for Business Server 2019. This server role is removed from Topology Builder, as well as from the code. 

The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams).

### SQL Mirroring for Skype for Business Server

SQL Mirroring can't be deployed with Skype for Business Server 2019. Other options for providing High Availability and Disaster Recovery are still supported and you should choose from among them. See [Plan for high availability and disaster recovery in Skype for Business Server](../SfbServer/plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md) to review the options.

### In-place upgrades 

In-place upgrades were available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. Side by side upgrade and coexistance is supported, see [Migration to Skype for Business Server 2019](migration/migration-to-skype-for-business-server-2019.md) for more information.

### Mobility Service (Mcx)

Mobility Service support used by legacy mobile clients is no longer available in Skype for Business Server 2019. This was previously announced in Skype for Business Server 2015.

All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using Mcx will need to upgrade to a current client.

For more details, see [Plan for Mobility for Skype for Business Server](../SfbServer/plan-your-deployment/mobility.md) and [Mobile client feature comparison for Skype for Business](../SfbServer/plan-your-deployment/clients-and-devices/mobile-feature-comparison.md).

## Tools

The following tools will not be available for use at the initial release of Skype for Business Server 2019:

- Skype for Business Server Capacity Planning Calculator
- Skype for Business Server Debugging Tools
- Skype for Business Server Resource Kit Tools (some tools will be removed)
    - Call Parkometer
    - Lookup user console
    - Unassigned number Announcement Migration

The following tools are not supported with Skype for Business Server 2019:

- Call Quality Methodology (but not Call Quality Dashboard)
- Microsoft Call Quality Methodology Scorecard, v1.5
- Skype for Business Server 2015 Planning Tool
- Skype for Business Server 2015 Stress and Performance Tool

### See also

[What's new in Skype for Business Server 2019](whats-new.md)

[Migrating XMPP federation](migration/migrating-xmpp-federation.md)
