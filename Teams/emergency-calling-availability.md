---
ms.date: 08/22/2019
title: Emergency call routing for Calling Plans
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
description: Learn how emergency call routing is supported for Microsoft Calling Plans in different countries/regions.
ms.custom: seo-marvel-mar2020
---

# Emergency call routing for different countries/regions 

This article describes how emergency call routing is supported for Microsoft Calling Plans in different countries/regions.

CLI - Calling Line Identifier<br>
DID - Direct Inward Dialing<br>
EDB - Emergency DataBase<br>
LAC - Location Area Code<br>
PSAP - Public Safety Answering Point<br>

| Country  | How emergency calling works | 
| -------------------- | ----------- | 
| Australia | Emergency addresses are configured and routed by the carrier partner.  | 
| Austria | All outbound calls to Emergency Services are routed to the correct PSAP based on the LAC/first digits of the caller’s number. In Austria, there is no national EDB. The PSAPs will contact the operator in case they are not able to get the address from the caller.| 
| Belgium | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the PSAP system looks up the address against the number and displays it to the PSAP operator.  |
| Canada |  All outbound calls to Emergency Services are first screened to determine the current location of the user before being routed to the local PSAP. |
| Croatia | All outbound calls to Emergency Services are sent to the local PSAP based on the phone number prefix. For non-geo numbers, calls are routed to the national PSAP.  |
| Czech Republic | All outbound calls to Emergency Services are routed to the incumbent Operator, then routed to the East or West Call Centers, and then distributed to the appropriate Emergency Services Provider.  |
| Denmark | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB – when a call is made to the PSAP with the CLI, the Local PSAP system looks up the address against the number and displays it to the PSAP operator.  | 
| Estonia | All outbound calls to Emergency Services are sent to the local PSAP based on the phone number prefix. For non-geo numbers, calls are routed to the national PSAP.  |
| Finland | All outbound calls to Emergency Services are routed to the Local PSAP, and then distributed to the appropriate Emergency Services Provider.   |
| France | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the PSAP system looks up the address against the number and displays it to the PSAP operator.  |
| Germany | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the PSAP system looks up the address against the number and displays it to the PSAP operator.  |
| Hungary | All outbound calls to Emergency Services are routed to the Local PSAP, and then distributed to the appropriate Emergency Services Provider.   |
| Ireland | All outbound calls to Emergency Services are first screened to determine the current location of the user before being routed to the local PSAP. | 
| Italy | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the PSAP system looks up the address against the number and displays it to the PSAP operator.  |  
| Japan  | Emergency calling is not supported.  |
| Latvia | All outbound calls to Emergency Services are sent to the local PSAP based on the phone number prefix. For non-geo numbers, calls are routed to the national PSAP.  |
| Lithuania | All outbound calls to Emergency Services are sent to the local PSAP based on the phone number prefix.  |
| Luxembourg | All outbound calls to Emergency Services are first screened to determine the current location of the user before being routed to the local PSAP. |
| Netherlands| All outbound calls to Emergency Services are routed to the correct PSAP based on the LAC/first digits of the caller’s number. | 
| New Zealand |  All outbound calls to Emergency Services are first screened to determine the current location of the user before being routed to the local PSAP.  |
| Norway | Emergency calls are routed directly to the PSAP serving the emergency address associated with the number. If no address was provided, the call will be routed based on the old geographic number plan to the nearest emergency center.  |
| Poland  | All outbound calls to Emergency Services are routed to the Local PSAP, and then distributed to the appropriate Emergency Services Provider.   |
| Portugal | All outbound calls to Emergency Services are routed to the correct PSAP based on the LAC/first digits of the caller’s number.  |
| Romania | All outbound calls to Emergency Services are routed to the Local PSAP, and then distributed to the appropriate Emergency Services Provider. All Emergency Calls from a VoIP number are routed to a National Call Center in Bucharest. The National Call Center operator consults with the caller to identify the location and re-route to the Local PSAP.   |
| Singapore | All outbound calls to Emergency Services are routed to the Emergency Call Center based on the number dialed. The Operator requires the caller to provide the Address Information.   |
| Slovakia | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the PSAP system looks up the address against the number and displays it to the PSAP operator.   |
| Slovenia | All outbound calls to Emergency Services are sent to local PSAP based on phone number prefix. For non-geo numbers, calls are routed to the national PSAP. |
| South Africa | All outbound calls to Emergency services are dependent on the address of the caller. All outgoing calls to Emergency Services are routed to the nearest center covering the calling DID area code.  |
| Spain | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the PSAP system looks up the address against the number and displays it to the PSAP operator.   |  
| Sweden | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the Local PSAP system looks up the address against the number and displays it to the PSAP operator. |
| Switzerland | All outbound calls to Emergency Services are dependent on the address of the caller. The address registered to the number is stored in a national EDB. When a call is made to the PSAP with the CLI, the Local PSAP system looks up the address against the number and displays it to the PSAP operator.  |
| United Kingdom | All outbound calls to Emergency Services are first screened to determine the current location of the user before being routed to the local PSAP.  |
| United States | - If a Teams client is located at a tenant-defined dynamic emergency location, emergency calls from that client are automatically routed to the PSAP serving that geographic location. <br><br> - If a Teams client is not located at a tenant-defined dynamic emergency location, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location. <br><br> - If an emergency caller is unable to update their emergency location to the screening center, the call will be transferred to the PSAP serving the caller's registered address.  |


## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)




