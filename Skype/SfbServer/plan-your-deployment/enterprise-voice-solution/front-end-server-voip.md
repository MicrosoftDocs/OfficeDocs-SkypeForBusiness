---
title: "Front End Server VoIP components for Skype for Business Server"
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
ms.assetid: 310e81a7-da45-47d4-95d0-92837e386502
description: "Learn about the Enterprise Voice components that are located on Front End Servers in Skype for Business Server, including translation service and various routing components."
---

# Front End Server VoIP components for Skype for Business Server

Learn about the Enterprise Voice components that are located on Front End Servers in Skype for Business Server, including translation service and various routing components.

The VoIP components located on Front End Servers are as follows:

- Translation Service

- Inbound Routing component

- Outbound Routing component

- Exchange UM Routing component

- Intercluster Routing component

- [Mediation Server component in Skype for Business Server](mediation-server.md)

## Translation Service

The Translation Service is the server component that is responsible for translating a dialed number into the E.164 format or another format, according to the normalization rules that are defined by the administrator. The Translation Service can translate to formats other than E.164 if your organization uses a private numbering system or uses a gateway or PBX that does not support E.164.

## Inbound Routing Component

The Inbound Routing component handles incoming calls largely according to preferences that are specified by users on their Enterprise Voice clients. It also facilitates delegate ringing and simultaneous ringing, if configured by the user. For example, users specify whether unanswered calls are forwarded or simply logged for notification. If call forwarding is enabled, users can specify whether unanswered calls should be forwarded to another number or to a Exchange UM server that has been configured to provide call answering. The Inbound Routing component is installed by default on all Standard Edition server and Front End Servers.

## Outbound Routing Component

The Outbound Routing component routes calls to PBX or PSTN destinations. It applies call authorization rules, as defined by the user's voice policy, to callers and determines the optimal PSTN gateway for routing each call. The Outbound Routing component is installed by default on all Standard Edition server and Front End Servers.

The routing logic that is used by the Outbound Routing component is in large measure configured by network or telephony administrators according to the requirements of their organizations.

## Exchange UM Routing Component

The Exchange UM routing component handles routing between Skype for Business Server and servers running Exchange Unified Messaging (UM), to integrate Skype for Business Server with Unified Messaging features.

The Exchange UM routing component also handles rerouting of voice mail over the PSTN if Exchange UM servers are unavailable. If you have Enterprise Voice users at branch sites that do not have a resilient WAN link to a central site, the Survivable Branch Appliance that you deploy at the branch site provides voice mail survivability for branch users during a WAN outage. When the WAN link is unavailable, the Survivable Branch Appliance does the following:

- reroutes unanswered calls over the PSTN to the Exchange Unified Messaging server in the central site

- provides the ability for a user to retrieve voice mail messages over the PSTN

- queues missed call notifications, and then uploads them to the Exchange UM server when the WAN link is restored.

To enable voice mail rerouting, we recommend that your Exchange administrator configure Exchange UM Auto Attendant (AA) to accept messages only.

For details about these features, see [On-Premises Exchange Unified Messaging Integration](https://technet.microsoft.com/library/e7c63a71-2d99-4aa9-b649-36c1a431bdf1.aspx) and [Planning for Enterprise Voice Resiliency](https://technet.microsoft.com/library/ca116700-1055-4ca5-9b87-4c7f380c3655.aspx), respectively.

## Intercluster Routing Component

The Intercluster routing component is responsible for routing calls to the callee's primary Registrar pool. If that is unavailable, the component routes the call to the callee's backup Registrar pool. If the callee's primary and backup Registrar pools are unreachable over the IP network, the Intercluster routing component reroutes the call over the PSTN to the user's telephone number.

## Other Front End Server Components Required for VoIP

Other components residing on the Front End Server or Director that provide essential support for VoIP, but are not themselves VoIP components, include the following:

- **User Services.** Perform reverse number lookup on the destination phone number of each incoming call and match that number to the SIP URI of the destination user. Using this information, the Inbound Routing component distributes the call to that user's registered SIP endpoints. User Services is a core component on all Front End Servers and Directors.

- **User Replicator.** Extracts user phone numbers from Active Directory Domain Services and writes them to tables in the RTC database, where they are available to User Services and Address Book Server. User Replicator is a core component on all Front End Servers.

- **Address Book Server.** Provides global address list information from Active Directory Domain Services to Skype for Business Server clients. It also retrieves user and contact information from the RTC database, writes the information to the Address Book files, and then stores the files on a shared folder where they are downloaded by Skype for Business clients. The Address Book Server writes the information to the RTCAb database, which is used by the Address Book Web Query service to respond to user search queries from Skype for Business mobile. It optionally normalizes enterprise user phone numbers that are written to the RTC database for the purpose of provisioning user contacts in Skype for Business. The Address Book service is installed by default on all Front End Servers. The Address Book Web Query service is installed by default with the Web services on each Front End Servers.


