---
title: "Failing over the Edge pool used for XMPP federation in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 587e7829-a26b-46f8-8aad-b78a7b325b55
description: "In your organization, there is one Edge pool designated as the pool to use for XMPP federation. If this pool goes down, you must fail over XMPP federation to use a different Edge pool before XMPP federation can work again."
---

# Failing over the Edge pool used for XMPP federation in Lync Server 2013
[]
In your organization, there is one Edge pool designated as the pool to use for XMPP federation. If this pool goes down, you must fail over XMPP federation to use a different Edge pool before XMPP federation can work again.
  
When you first install Edge pools and enable XMPP Federation, you can simplify the disaster recovery process by setting up external DNS SRV records for all of your Edge pools for XMPP federation, instead of just one. Each of these SRV records must have a different priority set. All XMPP federation traffic goes through the pool with the SRV record with the highest priority. For more information on enabling and setting up XMPP federation, see [Setting up XMPP federation in Lync Server 2013](setting-up-xmpp-federation.md). 
  
In the following procedure, EdgePool1 is the pool which originally hosted XMPP federation, and EdgePool2 is the pool which will now host XMPP federation.
  
### Failing Over the Edge Pool Used for XMPP Federation

1. If you don't already have another Edge pool deployed (besides the one which is currently down), deploy that pool. For details, see [Deploying external user access in Lync Server 2013](deploying-external-user-access.md).
    
2. On each Edge Server in the new Edge pool which will now host XMPP federation (EdgePool2), run the following cmdlet:
    
  ```
  Stop-CsWindowsService
  ```

3. Run the following cmdlet to repoint the XMPP federation route to EdgePool2:
    
  ```
  Set-CsSite Site2 -XmppExternalFederationRoute EdgeServer2.contoso.com
  ```

    In this example, Site2 is the site containing the Edge pool which will now host the XMPP federation route, and EdgeServer2.contoso.com is the FQDN of an Edge Server in that pool.
    
4. On the external DNS server, change the DNS A record for XMPP federation to point to EdgeServer2.contoso.com.
    
5. If you do not already have a DNS SRV record for XMPP federation which resolves to the Edge pool which will now host XMPP federation, you must add it, as in the following example. This SRV record must have a port value of 5269.
    
  ```
  _xmpp-server._tcp.contoso.com
  ```

6. Verify that the Edge pool which will now host XMPP federation has port 5269 open externally.
    
7. Start the services on all Edge Servers in the Edge pool which will now host XMPP federation:
    
  ```
  Start-CsWindowsService
  ```


