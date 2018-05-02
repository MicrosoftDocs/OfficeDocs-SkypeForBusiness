---
title: "Configure federation routes and media traffic [W14 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8b2f5f81-a955-4ad1-ad74-397322ff9521
description: "Federation is a trust relationship between two or more SIP domains that permits users in separate organizations to communicate across network boundaries. After you migrate to your Lync Server 2013 pilot pool, you need to transition from the federation route of your Lync Server 2010 Edge Servers to the federation route of your Lync Server 2013 Edge Servers."
---

# Configure federation routes and media traffic [W14 to W15]
[]
Federation is a trust relationship between two or more SIP domains that permits users in separate organizations to communicate across network boundaries. After you migrate to your Lync Server 2013 pilot pool, you need to transition from the federation route of your Lync Server 2010 Edge Servers to the federation route of your Lync Server 2013 Edge Servers. 
  
Use the following procedures to transition the federation route and the media traffic route from your Lync Server 2010 Edge Server and Director to your Lync Server 2013 Edge Server, for a single-site deployment.
  
> [!IMPORTANT]
> Changing the federation route and media traffic route requires that you schedule maintenance downtime for the Lync Server 2013 and Lync Server 2010 Edge Servers. This entire transition process also means that federated access will be unavailable for the duration of the outage. You should schedule the downtime for a time when you expect minimal user activity. You should also provide sufficient notification to your end users. Plan accordingly for this outage and set appropriate expectations within your organization. 
  
> [!IMPORTANT]
> If your legacy Lync Server 2010 Edge Server is configured to use the same FQDN for the Access Edge service, Web Conferencing Edge service, and the A/V Edge service, the procedures in this section are not supported. If the legacy Edge services are configured to use the same FQDN, you must first migrate all your users from Lync Server 2010 to Lync Server 2013, then decommission the Lync Server 2010 Edge Server before enabling federation on the Lync Server 2013 Edge Server. 
  
> [!IMPORTANT]
> If your XMPP federation is routed through a Lync Server 2013 Edge Server, legacy Lync Server 2010 users will not be able to communicate with the XMPP federated partner until all users have been moved to Lync Server 2013, XMPP policies and certificates have been configured, the XMPP federated partner has been configured on Lync Server 2013, and lastly the DNS entries have been updated. 
  
### To remove the legacy federation association from Lync Server 2013 sites

1. On the Lync Server 2013 Front End server, open the existing topology in Topology Builder. 
    
2. In the left pane, navigate to the site node, which is located directly below **Lync Server**.
    
3. Right-click the site and then click **Edit Properties**.
    
4. In the left pane, select **Federation route**. 
    
5. Under **Site federation route assignment**, clear the **Enable SIP federation** check box to disable the federation route through the legacy Lync Server 2010 environment. 
    
     ![Edit Properties dialog, Federation route page](../../media/migration_lyncserver_w15_federation_disable.JPG)
  
6. Click **OK** to close the Edit Properties page. 
    
7. From **Topology Builder**, select the top node **Lync Server**.
    
8. From the **Action** menu, click **Publish Topology**.
    
9. Click **Next** to complete the publishing process and then click **Finish** when the publishing process has completed. 
    
### To configure the legacy Edge Server as a non-federating Edge Server

1. In the left pane, navigate to the **Lync Server 2010** node and then to the **Edge pools** node. 
    
2. Right-click the Edge server, and then click **Edit Properties**.
    
3. Select **General** in the left pane. 
    
4. Clear the **Enable federation for this Edge pool (port 5061)** check box entry and select **OK** to close the page. 
    
     ![Edit Properties, General, clear Enable federation](../../media/migration_lyncserver_w15_federation_remove.JPG)
  
5. From the **Action** menu, select **Publish Topology**, and then click **Next**.
    
6. When the **Publishing wizard** completes, click **Finish** to close the wizard. 
    
7. Verify federation for the legacy Edge server is disabled.
    
     ![Topology Builder, Edge pool, federation disabled](../../media/migration_lyncserver_w15_federation_verify_disabled.JPG)
  
### To configure certificates on the Lync Server 2010 Edge Server

1. Export the external Access Proxy certificate, with the private key, from the legacy Lync Server 2010 Edge Server. 
    
2. On the Lync Server 2013 Edge Server, import the Access Proxy external certificate from the previous step.
    
3. Assign the Access Proxy external certificate to the Lync Server 2013 external interface of the Edge Server.
    
4. The internal interface certificate of the Lync Server 2013 Edge Server should be requested from a trusted CA and assigned. 
    
### To change Lync Server 2010 federation route to use Lync Server 2013 Edge Server

1. From Topology Builder, in the left pane, navigate to the **Lync Server 2013** node and then to the **Edge pools** node. 
    
2. Right-click the Edge server, and then click **Edit Properties**.
    
3. Select **General** in the left pane. 
    
4. Select the check box entry for **Enable federation for this Edge pool (port 5061)** and then click **OK** to close the page. 
    
     ![Edit Properties dialog, General page](../../media/migration_lyncserver_w15_federation_enable_2013_federation.JPG)
  
5. From the **Action** menu, select **Publish Topology**, and then click **Next**.
    
6. When the **Publishing wizard** completes, click **Finish** to close the wizard. 
    
7. Verify **Federation (port 5061)** is set to **Enabled**.
    
     ![Topology Builder, Edge pool, Federation enabled](../../media/migration_lyncserver_w15_federation_verify_2013_enabled.JPG)
  
### To update Lync Server 2013 Edge Server federation next hop

1. From Topology Builder, in the left pane, navigate to the **Lync Server 2013** node and then to the **Edge pools** node. 
    
2. Expand the node, right-click the Edge Server listed, and then click **Edit Properties**. 
    
3. On the **General** page, under **Next hop selection**, select from the drop-down list the Lync Server 2013 pool.
    
     ![Edit Properties dialog, Next hop page](../../media/migration_lyncserver_w15_federation_configure_nexthop.JPG)
  
4. Click **OK** to close the Edit Properties page. 
    
5. From **Topology Builder**, select the top node **Lync Server**. 
    
6. From the **Action** menu, click **Publish Topology** and complete the wizard. 
    
### To configure Lync Server 2013 Edge Server outbound media path

1. From Topology Builder, in the left pane, navigate to the **Lync Server 2013** node and then to the pool below **Standard Edition Front End Servers** or **Enterprise Edition Front End pools**.
    
2. Right-click the pool, and then click **Edit Properties**.
    
3. In the **Associations** section, select the **Associate Edge pool (for media components)** check box. 
    
     ![Edit Properties, General, Associate Edge pool](../../media/migration_lyncserver_w15_federation_enable_W15media.JPG)
  
4. From the drop down box, select the Lync Server 2013 Edge Server.
    
5. Click **OK** to close the **Edit Properties** page. 
    
### To turn on Lync Server 2013 Edge Server federation

1. From Topology Builder, in the left pane, navigate to the **Lync Server 2013** node and then to the **Edge pools** node. 
    
2. Expand the node, right-click the Edge Server listed, and then click **Edit Properties**. 
    
    > [!NOTE]
    > Federation can only be enabled for a single Edge pool. If you have multiple Edge pools, select one to use as the federating Edge pool. 
  
3. On the **General** page, verify the **Enable federation for this Edge pool (Port 5061)** setting is checked. 
    
     ![Edit Properties dialog, General page](../../media/migration_lyncserver_w15_federation_enable_2013_federation.JPG)
  
4. Click **OK** to close the Edit Properties page. 
    
5. Next, navigate to the site node. 
    
6. Right-click the site, and then click **Edit Properties**.
    
7. In the left pane, click **Federation route**.
    
8. Under **Site federation route assignment**, select **Enable SIP federation**, and then from the list select the Lync Server 2013 Edge Server listed. 
    
     ![Edit Properties, Federation route page](../../media/migration_lyncserver_w15_federation_site_enablefed.JPG)
  
9. Click **OK** to close the **Edit Properties** page. 
    
     For multi-site deployments, complete this procedure at each site. 
    
### To publish Edge Server configuration changes

1. From **Topology Builder**, select the top node **Lync Server**. 
    
2. From the **Action** menu, select **Publish Topology** and complete the wizard. 
    
3. Wait for Active Directory replication to occur to all pools in the deployment.
    
    > [!NOTE]
    > You may see the following message: > **Warning: The topology contains more than one Federated Edge Server. This can occur during migration to a more recent version of the product. In that case, only one Edge Server would be actively used for federation. Verify that the external DNS SRV record points to the correct Edge Server. If you want to deploy multiple federation Edge Server to be active concurrently (that is, not a migration scenario), verify that all federated partners are using Lync Server. Verify that the external DNS SRV record lists all federation enabled Edge Servers.**> This warning is expected and can be safely ignored. 
  
### To configure Lync Server 2013 Edge Server

1. Bring all of the Lync Server 2013 Edge Servers online. 
    
2. Update the external firewall routing rules or the hardware load balancer settings to send SIP traffic for external access (usually port 443) and federation (usually port 5061) to the Lync Server 2013 Edge Server, instead of the legacy Edge Server.
    
    > [!NOTE]
    > If you do not have a hardware load balancer, you need to update the DNS A record for federation to resolve to the new Lync Server Access Edge server. To accomplish this with minimum disruption, reduce the TLL value for the external Lync Server Access Edge FQDN so that when DNS is updated to point to the new Lync Server Access Edge, federation and remote access will be updated quickly. 
  
3. Next, stop the **Lync Server Access Edge** from each Edge Server computer. 
    
4. From each legacy Edge Server computer, open the **Services** applet from the **Administrative Tools**.
    
5. In the services list, find **Lync Server Access Edge**.
    
6. Right-click the services name, and then select **Stop** to stop the service. 
    
7. Set the Startup type to **Disabled**. 
    
8. Click **OK** to close the **Properties** window. 
    

