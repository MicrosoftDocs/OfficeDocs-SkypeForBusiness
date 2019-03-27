---
title: 'Lync Server 2013: Remote call control and phone number normalization'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remote call control and phone number normalization
ms:assetid: 291d9e87-4c65-4ea2-888f-517741391de5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558630(v=OCS.15)
ms:contentKeyID: 48183696
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remote call control and phone number normalization in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-22_

Lync clients download phone number normalization rules as part of the Address Book Service (ABS) file download. In remote call control scenarios, Address Book Service phone number normalization rules are applied to both incoming and outgoing remote call control calls. For incoming calls to a remote call control-enabled user, the phone number of the caller is first normalized to E.164 format by either the SIP/CSTA gateway or private branch exchange (PBX). When Lync Server 2013 receives the call from the gateway, it performs reverse number lookup (RNL) on the phone number of the caller against the normalized number in the callee’s Microsoft Office Outlook Contacts list or the global address list (GAL) that is stored in the Address Book Service. If reverse number lookup successfully finds a match, the caller is identified by name in the incoming call notification.

For outgoing remote call control calls, Lync applies the Address Book Service phone number normalization rules to the dialed number before routing the call to the SIP/CSTA gateway.

For details about creating phone number normalization rules for remote call control, see [Dial plans and normalization rules in Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md) in the Planning documentation.

<div>

## Migrating Phone Number Normalization Rules

If you are migrating users previously enabled for remote call control, see the following topics in the Migration documentation:

  - For Lync Server 2010, see [Migrate Address Book](migrate-address-book.md) in the Migration documentation.

  - For Communications Server 2007 R2, see [Migrate Address Book](migrate-address-book_1.md) in the Migration documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

