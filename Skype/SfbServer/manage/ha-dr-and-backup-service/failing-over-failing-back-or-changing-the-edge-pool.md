---
title: 'Failing over, failing back, or changing the Edge pool'
author: heidip
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn how to fail over and fail back the Edge pool used for Skype for Business federation or XMPP federation, or change the Edge pool associated with a Front End pool."
---

# Failing over, failing back, or changing the Edge pool in Skype for Business Server

Use the sections in this article to learn how to fail over and fail back the Edge pool used for Skype for Business federation or XMPP federation, or change the Edge pool associated with a Front End pool.


## Fail over the Edge pool used for Skype for Business Server federation 

If the Edge pool where you have Skype for Business Server federation configured goes down, you must change federation to use a different Edge pool for federation to work.

1.  On a Front End server, open Topology Builder. Expand **Edge pools**, then right click the Edge server or Edge server pool that is currently configured for Federation. Select **Edit properties**.

2.  In **Edit Properties** under **General**, clear **Enable federation for this Edge pool (Port 5061)**. Click **OK**.

3.  Expand **Edge pools**, then right click the Edge server or Edge server pool that you now want to use for Federation. Select **Edit properties**.

4.  In **Edit Properties** under **General**, select **Enable federation for this Edge pool (Port 5061)**. Click **OK**.

5.  Click **Action**, select **Topology**, select **Publish**. When prompted on **Publish the topology**, click **Next**. When the Publish is finished, click **Finish**.

6.  On the Edge server, open the Skype for Business Server Deployment wizard. Click **Install or Update Skype for Business Server System**, then click **Setup or Remove Skype for Business Server Components**. Click **Run Again**.

7.  Click **Next**. The summary screen will show actions as they are executed. Once the deployment is done, click **View Log** to view available log files. Click **Finish** to complete the deployment.
    
    If the site containing the failed Edge pool contains Front End Servers that are still running, you must update the Web Conferencing Service and A/V Conferencing Service on these Front End pools to use an Edge pool in a remote site that is still running. 

 ## Fail over the Edge pool used for XMPP federation in Skype for Business Server 

In your organization, there is one Edge pool designated as the pool to use for XMPP federation. If this pool goes down, you must fail over XMPP federation to use a different Edge pool before XMPP federation can work again.

When you first install Edge pools and enable XMPP Federation, you can simplify the disaster recovery process by setting up external DNS SRV records for all of your Edge pools for XMPP federation, instead of just one. Each of these SRV records must have a different priority set. All XMPP federation traffic goes through the pool with the SRV record with the highest priority. 

In the following procedure, EdgePool1 is the pool which originally hosted XMPP federation, and EdgePool2 is the pool which will now host XMPP federation.


### To fail over the Edge pool used for XMPP federation

1.  If you don’t already have another Edge pool deployed (besides the one which is currently down), deploy that pool. 

2.  On each Edge Server in the new Edge pool which will now host XMPP federation (EdgePool2), run the following cmdlet:
    
        Stop-CsWindowsService

3.  Run the following cmdlet to repoint the XMPP federation route to EdgePool2:
    
        Set-CsSite Site2 -XmppExternalFederationRoute EdgeServer2.contoso.com
    
    In this example, Site2 is the site containing the Edge pool which will now host the XMPP federation route, and EdgeServer2.contoso.com is the FQDN of an Edge Server in that pool.

4.  On the external DNS server, change the DNS A record for XMPP federation to point to EdgeServer2.contoso.com.

5.  If you do not already have a DNS SRV record for XMPP federation which resolves to the Edge pool which will now host XMPP federation, you must add it, as in the following example. This SRV record must have a port value of 5269.
    
        _xmpp-server._tcp.contoso.com

6.  Verify that the Edge pool which will now host XMPP federation has port 5269 open externally.

7.  Start the services on all Edge Servers in the Edge pool which will now host XMPP federation:
    
        Start-CsWindowsService


## Fail back the Edge pool used for Skype for Business Server federation or XMPP federation 

After a failed Edge pool that used to host federation has been brought back online, use this procedure to fail back the Skype for Business Server federation route and/or the XMPP federation route to again use this restored Edge pool.

1.  On the Edge pool that is now available again, start the Edge Services.

2.  If you want to fail back the Skype for Business Server federation route to use the restored Edge Server, do the following:
    
      - On a Front End server, open Topology Builder. Expand **Edge pools**, then right click the Edge server or Edge server pool that is currently configured for Federation. Select **Edit properties**.
    
      - In **Edit Properties** under **General**, clear **Enable federation for this Edge pool (Port 5061)**. Click **OK**.
    
      - Expand **Edge pools**, then right click the original Edge server or Edge server pool that you again want to use for Federation. Select **Edit properties**.
    
      - In **Edit Properties** under **General**, select **Enable federation for this Edge pool (Port 5061)**. Click **OK**.
    
      - Click **Action**, select **Topology**, select **Publish**. When prompted on **Publish the topology**, click **Next**. When the Publish is finished, click **Finish**.
    
      - On the Edge server, open the Skype for Business Server Deployment wizard. Click **Install or Update Skype for Business Server System**, then click **Setup or Remove Skype for Business Server Components**. Click **Run Again**.
    
      - Click **Next**. The summary screen will show actions as they are executed. Once the deployment is done, click **View Log** to view available log files. Click **Finish** to complete the deployment.

3.  If you want to fail back the XMPP federation route to use the restored Edge Server, do the following:
    
      - Run the following cmdlet to repoint the XMPP federation route to the Edge pool which will now host XMPP federation (in this example, EdgeServer1):
        
            Set-CsSite Site1 -XmppExternalFederationRoute EdgeServer1.contoso.com
        
        In this example, Site1 is the site containing the Edge pool which will now host the XMPP federation route, and EdgeServer1.contoso.com is the FQDN of an Edge Server in that pool.
    
      - If you do not already have a DNS SRV record for XMPP federation which resolves to the Edge pool which will now host XMPP federation, you must add it, as in the following example. This SRV record must have a port value of 5269.
        
            _xmpp-server._tcp.contoso.com
    
      - On the external DNS server, change the DNS A record for XMPP federation to point to EdgeServer2.contoso.com.
    
      - Verify that the Edge pool which will now host XMPP federation has port 5269 open externally.

4.  If the Front End pools remained running in the site containing the Edge pool that failed and has been restored, you should update the Web Conferencing Service and A/V Conferencing Service on these Front End pools to again use the Edge pools at their local site.

5.  If the Front End pool at the same site as the failed Edge pool also failed, you can now use Invoke–CsPoolFailback to fail back the Front End pool.


## Change the Edge pool associated with a Front End pool

If an Edge pool goes down but the Front End pool at the same site is still running, you will need to set the Front End pool to use an Edge pool at a different site until the failed Edge pool is restored.

1.  In Topology Builder, navigate to the name of the Front End pool you need to change.

2.  Right-click the pool, and then click **Edit Properties**.

3.  In the **Associations** section, under **Associate Edge Pool (for media components)**, use the drop down box to select the Edge pool you want to associate this Front End pool with.

4.  Click **OK**.