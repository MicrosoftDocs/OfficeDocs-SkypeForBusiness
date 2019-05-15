---
title: Run backward compatibility for Persistent Chat Server
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Run backward compatibility for Persistent Chat Server
ms:assetid: 53f1a706-3104-4a94-8b4e-8badd9a066d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204901(v=OCS.15)
ms:contentKeyID: 48184175
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Run backward compatibility for Persistent Chat Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

The Lync Server 2013, Persistent Chat Server endpoint provides a way to create a simple URL that points to a Persistent Chat Server pool. This is useful for legacy clients (Microsoft Office Communications Server 2007 R2 Group Chat Server or Lync Server 2010, Group Chat) because users can enter a simple URL in the manual configuration when trying to point the legacy client to a computer running Lync 2013, Persistent Chat. This endpoint isn’t used by Persistent Chat, and is required for legacy clients only. This is useful for the interim period where rooms may be migrated, but the Lync 2013 clients have not been deployed throughout the organization. Users running Lync 2010 Group Chat (client) can then still connect to the Persistent Chat Server Back End Server.

You don’t need to create multiple Persistent Chat Server endpoints; you just need one for each Persistent Chat Server pool. Administrators can create multiple endpoints (one per pool), but legacy clients can be configured to connect to only one pool at a time. In the usual or mainstream scenario, the legacy deployment is one pool only. A new deployment generally migrates that pool to a new Lync Server 2013 and might add some new additional Persistent Chat Server pools.

This mainstream scenario generally follows this pattern:

  - You administer users with one Lync Server 2010, Group Chat pool, and your Lync 2010 Group Chat clients connect to that pool by using some well-known user (either default sip:ocschat@\<domainName\>.com, or a similar one). The users are SIP-enabled Active Directory Domain Services, and the Lookup service registers with them to receive incoming requests.

  - Subsequently, you install a Lync Server 2013 Persistent Chat Server and Persistent Chat Server pool.

  - During a time when users are generally offline (for example, a weekend):
    
      - Turn off Lync Server 2010, Group Chat.
    
      - Migrate data from the Lync Server 2010, Group Chat pool to the Lync Server 2013 Persistent Chat Server pool.
    
      - Delete the well-known user from the Active Directory Domain Services.
    
      - Create a new *legacy endpoint* with the same SIP URI as the previously deleted well-known user.
    
      - Start the Lync Server 2013, Persistent Chat Servers.

  - Users log back on by using their Lync 2010 Group Chat (client) and connect to their data without needing to change any configuration.

  - At a later time, you can decommission the Lync Server 2010, Group Chat. Subsequently, you can deploy Lync Server 2013, Persistent Chat Server, and install new Lync Server 2013 Persistent Chat Server pools.

For details about migrating from Lync Server 2010, Group Chat to Lync Server 2013, Persistent Chat Server, see [Migration from Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md).

To run backward compatibility (to create a Persistent Chat Server endpoint that points to a Persistent Chat Server pool, which can be used by legacy Group Chat pool clients):

    New-CsPersistentChatEndpoint -SipAddress <CO name, ex. persistentchat@contoso.com> -PersistentChatPoolFqdn <pool FQDN, like pcpool.contoso.com>

Next, configure Persistent Chat clients to use that SIP address as their contact object. The SIP address is created with the **New-CsPersistentChatEndpoint** cmdlet for a specific Persistent Chat Server pool.

To add the Persistent Chat Server endpoint by using Windows PowerShell command-line interface, consider the following example. In this case, you are configuring the contact object to be named "persistentchat" on the "contoso.com" topology, where the pool fully qualified domain name (FQDN) is "pcpool.contoso.com":

    New-CsPersistentChatEndpoint -SipAddress sip:persistentchat@contoso.com -PersistentChatPoolFqdn pcpool.contoso.com

<div>

## See Also


[Migration from Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

