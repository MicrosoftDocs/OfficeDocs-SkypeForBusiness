---
title: "More about Calling Line ID and Calling Party Name"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: roykuntz, jens
ms.topic: article
ms.tgt.pltfrm: cloud
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business Online
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
  - CSH
ms.custom: 
  - Calling Plans
ms.service: msteams
description: "Learn why you need to add an authorized person who can make changes to the account when you use the New Local Number Port Order wizard."
---

# More about Calling Line ID and Calling Party Name

CallerID consists of two user-facing identifiable pieces of information:

- A phone number (typically referred to as CLID or calling line ID).

- Calling party name (typically referred to as CNAM). 

When a call is made, the CLID (phone number) is routed to the destination's carrier (also known as the terminating carrier). The CNAM info for the call may or may not be routed with the call as this depends on how the country has implemented CNAM (if at all). The reliability of CNAM delivery with the call varies depending on the country and carriers which handle the call either as an intermediary and/or a terminating carrier. 

CLID & CNAM transmission is the responsibility of the terminating carrier. The terminating carrier must support CLID & CNAM functionality as well as provide up-to-date records for both values. Microsoft reliably provides CLID values when originating calls, but those values may not be kept intact once they pass through an intermediary carrier or the terminating carrier. If the CLID value is changed, omitted, or truncated by the intermediary or terminating carrier, Microsoft has little to no recourse in correcting such problems in the public telephone network.

Inconsistencies in CNAM can be caused when the intermediate or terminating carriers delays refreshing the CNAM information in authoritative databases--as in the case of the United States. In countries where there is no authoritative database for CNAM, individual carrier practices can also cause problems with CNAM information arriving intact with the call. Microsoft currently does not support originating CNAM information in countries other than the United States.

## Related topics


