---
title: "Remote call control and phone number normalization in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 291d9e87-4c65-4ea2-888f-517741391de5
description: "Lync clients download phone number normalization rules as part of the Address Book Service (ABS) file download. In remote call control scenarios, Address Book Service phone number normalization rules are applied to both incoming and outgoing remote call control calls. For incoming calls to a remote call control-enabled user, the phone number of the caller is first normalized to E.164 format by either the SIP/CSTA gateway or private branch exchange (PBX). When Lync Server 2013 receives the call from the gateway, it performs reverse number lookup (RNL) on the phone number of the caller against the normalized number in the callee's Microsoft Office Outlook Contacts list or the global address list (GAL) that is stored in the Address Book Service. If reverse number lookup successfully finds a match, the caller is identified by name in the incoming call notification."
---

# Remote call control and phone number normalization in Lync Server 2013
[]
Lync clients download phone number normalization rules as part of the Address Book Service (ABS) file download. In remote call control scenarios, Address Book Service phone number normalization rules are applied to both incoming and outgoing remote call control calls. For incoming calls to a remote call control-enabled user, the phone number of the caller is first normalized to E.164 format by either the SIP/CSTA gateway or private branch exchange (PBX). When Lync Server 2013 receives the call from the gateway, it performs reverse number lookup (RNL) on the phone number of the caller against the normalized number in the callee's Microsoft Office Outlook Contacts list or the global address list (GAL) that is stored in the Address Book Service. If reverse number lookup successfully finds a match, the caller is identified by name in the incoming call notification.
  
For outgoing remote call control calls, Lync applies the Address Book Service phone number normalization rules to the dialed number before routing the call to the SIP/CSTA gateway.
  
For details about creating phone number normalization rules for remote call control, see [Dial plans and normalization rules in Lync Server 2013](dial-plans-and-normalization-rules.md) in the Planning documentation. 
  
## Migrating Phone Number Normalization Rules

If you are migrating users previously enabled for remote call control, see the following topics in the Migration documentation:
  
- For Lync Server 2010, see [Migrate Address Book [W14 to W15]](migrate-address-book-w14-to-w15.md) in the Migration documentation. 
    
- For Communications Server 2007 R2, see [Migrate Address Book [OCS 2007 R2 to W15]](migrate-address-book-ocs-2007-r2-to-w15.md) in the Migration documentation. 
    

