---
title: Configure federation routes and media traffic
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure federation routes and media traffic
ms:assetid: ed6cb922-7863-453a-adce-2ce0ba761d74
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721925(v=OCS.15)
ms:contentKeyID: 49733860
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

# Configure federation routes and media traffic

 


Federation is a trust relationship between two or more SIP domains that permits users in separate organizations to communicate across network boundaries. After you migrate to your Lync Server 2013 pilot pool, you need to transition from the federation route of your Microsoft Office Communications Server 2007 R2 Edge Servers to the federation route of your Lync Server 2013 Edge Servers.

Use the procedures that follow to transition the federation route and the media traffic route from your Office Communications Server 2007 R2 Edge Server and Director to your Lync Server 2013 Edge Server, for a single-site deployment.


> [!IMPORTANT]  
> Changing the federation route and media traffic route requires that you schedule maintenance downtime for the Lync Server 2013 and Office Communications Server 2007 R2 Edge Servers. This entire transition process also means that federated access will be unavailable for the duration of the outage. You should schedule the downtime for a time when you expect minimal user activity. You should also provide sufficient notification to your end users. Plan accordingly for this outage and set appropriate expectations within your organization.




> [!IMPORTANT]  
> If your legacy Office Communications Server 2007 R2 Edge Server is configured to use the same FQDN for the Access Edge service, Web Conferencing Edge service, and the A/V Edge service, the procedures in this section to transition the federation setting to a Lync Server 2013 Edge Server are not supported. If the legacy Edge services are configured to use the same FQDN, you must first migrate all your users from Office Communications Server 2007 R2 to Lync Server 2013, then decommission the Office Communications Server 2007 R2 Edge Server before enabling federation on the Lync Server 2013 Edge Server. For details, see the following topics: 
> <UL>
> <LI>
> <P><A href="move-remaining-users-to-lync-server-2013_1.md">Move remaining users to Lync Server 2013</A></P>
> <LI>
> <P>"Remove Servers and Server Roles" at <A href="http://go.microsoft.com/fwlink/p/?linkid=268790">http://go.microsoft.com/fwlink/p/?LinkId=268790</A></P></LI></UL>




> [!IMPORTANT]  
> If your XMPP federation is routed through a Lync Server 2013 Edge Server, legacy Office Communications Server 2007 R2 users will not be able to communicate with the XMPP federated partner until all users have been moved to Lync Server 2013, XMPP policies and certificates have been configured, the XMPP federated partner has been configured on Lync Server 2013, and lastly the DNS entries have been updated.



To successfully publish, enable, or disable a topology when adding or removing a server role, you should be logged in as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. It is also possible to delegate the proper user rights and permissions for adding server roles. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) in the Standard Edition server or Enterprise Edition server Deployment documentation. For other configuration changes, only membership in the RTCUniversalServerAdmins group is required.

## To remove the legacy federation association from Lync Server 2013 sites

1.  Open the pilot pool topology using Topology Builder.

2.  In the left pane, navigate to the site node.

3.  Right-click the site, and then click **Edit Properties**.

4.  Select **Federation route** in the left pane.

5.  Under Site federation route assignment, clear the check box next to **Enable SIP federation** to disable the federation route through the **BackCompatSite**.
    
    ![Edit Properties dialog, Federation route](images/JJ721925.2a80c103-c0cc-43ed-ba00-420f9add006a(OCS.15).jpg "Edit Properties dialog, Federation route")

6.  Click **OK** to close the Edit Properties page.

7.  From **Topology Builder**, select the top node **Lync Server**.

8.  From the **Action** menu, click **Publish Topology** and complete the wizard.

## To configure the legacy Edge Server as a non-federating Edge Server

1.  From **Topology Builder**, from the **Action** menu click **Merge Office Communications Server 2007 R2 Topology**.

2.  Click **Next** to continue.

3.  On the **Specify Edge Setup**, select the **Edge Server Internal FQDN** that is currently configured for federation, and then click **Change**.
    
    ![Merge OCS 2007 R2 Topology, Specify Edge Setup](images/JJ721925.42c15aaf-c1ac-4fb1-a086-665835c57b23(OCS.15).jpg "Merge OCS 2007 R2 Topology, Specify Edge Setup")

4.  Click **Next** and accept the default settings until you get to the **Specify External Edge** page:
    
    ![Topology Builder Specify External Edge page](images/JJ721925.e36f3a1f-3655-456e-9e6d-4814c37da0bf(OCS.15).jpg "Topology Builder Specify External Edge page")

5.  In **Specify External Edge**, clear the **This Edge pool is used for federation and public IM connectivity** check box. This will remove the federation association with the BackCompatSite.
    

    > [!IMPORTANT]  
    > This step is important. You must clear this option to remove the legacy federation association.



6.  Click **Next** and accept the default settings of the remaining pages of the wizard.

7.  In **Summary**, click **Next** to begin merging the topologies.

8.  In the **Status** column, verify that the value is **Success**, and then click **Finish** to close the wizard.

9.  From the **Action** menu, select **Publish Topology**, and then click **Next**.

10. When the **Publishing wizard** completes, click **Finish** to close the wizard.
    
    ![Topology Builder with site displayed after merge](images/JJ721925.92b679ad-332f-49aa-b4e2-19f939b711ca(OCS.15).jpg "Topology Builder with site displayed after merge")
    
    As shown in the previous figure, the **SIP federation** located under **Site federation route assignment** is set to **Disabled**.

## To configure certificates on the Lync Server 2013 Edge Server

1.  Export the external Access Proxy certificate, with the private key, from the legacy Office Communications Server 2007 R2 Edge Server.

2.  On the Lync Server 2013 Edge Server, import the Access Proxy external certificate from the previous step.

3.  Assign the Access Proxy external certificate to the Lync Server 2013 external interface of the Edge Server.

4.  The internal interface certificate of the Lync Server 2013 Edge Server should not be changed.

## To change Office Communications Server 2007 R2 federation route to use Lync Server 2013 Edge Server

1.  On the Office Communications Server 2007 R2 Standard Edition server or Front End Server, open the Office Communications Server 2007 R2 Administrative tool.

2.  In the left pane, expand the top node, and then right-click the **Forest** node. Select **Properties**, and then click **Global Properties**.

3.  Click the **Federation** tab.

4.  Select the check box to enable federation and Public IM connectivity.

5.  Enter the FQDN of the Lync Server 2013 Edge Server, and then click **OK**.
    
    ![OCS Global Properties, Federation tab](images/JJ721925.da633f72-43c6-4dac-8d37-ccd0dcde79c9(OCS.15).jpg "OCS Global Properties, Federation tab")

## To turn on Lync Server 2013 Edge Server federation

1.  From Topology Builder, in the left pane, navigate to the Lync Server 2013 **Edge pools** node.

2.  Expand the node, right-click the Edge Server listed, and then click **Edit Properties**.
    

    > [!NOTE]  
    > Federation can only be enabled for a single Edge pool. If you have multiple Edge pools, select one to use as the federating Edge pool.



3.  On the **General** page, select the **Enable federation for this Edge pool (Port 5061)** check box.
    
    ![Edit Properties, General, Enable Edge Federation](images/JJ721925.2aeb5958-da55-4910-b3d7-2124e144a2f0(OCS.15).jpg "Edit Properties, General, Enable Edge Federation")

4.  Click **OK** to close the Edit Properties page.

5.  Next, navigate to the site node.

6.  Right-click the site, and then click **Edit Properties**.

7.  In the left pane, click **Federation route**.

8.  Under **Site federation route assignment**, select **Enable SIP federation**, and then from the list select the Lync Server 2013 Edge Server listed.

9.  Click **OK** to close the **Edit Properties** page.
    
    ![Edit Properties, General, Associate Edge pool](images/JJ721925.33d43297-10cd-412e-bf4a-a1d9a84b9009(OCS.15).jpg "Edit Properties, General, Associate Edge pool")
    
    For multi-site deployments, complete this procedure at each site.

## To configure Lync Server 2013 Edge Server outbound media path

1.  From **Topology Builder**, navigate to the Lync Server 2013 pool below **Standard Edition Front End Servers** or **Enterprise Edition Front End pools**.

2.  Right-click the pool, and then click **Edit Properties**.

3.  In the **Associations** section, select the **Associate Edge pool (for media components)** check box.

4.  From the drop down box, select the Lync Server 2013 Edge Server.
    
    ![Edit Properties dialog, Associate Edge Pool](images/JJ721925.0cb76b08-5923-4972-8d7a-a829cb77136b(OCS.15).jpg "Edit Properties dialog, Associate Edge Pool")

5.  Click **OK** to close the **Edit Properties** page.

## To publish Edge Server configuration changes

1.  From **Topology Builder**, select the top node **Lync Server**.

2.  From the **Action** menu, select **Publish Topology** and complete the wizard.

3.  Wait for Active Directory replication to occur to all pools in the deployment.
    

    > [!NOTE]  
    > You may see the following message:<BR><STRONG>Warning: The topology contains more than one Federated Edge Server. This can occur during migration to a more recent version of the product. In that case, only one Edge Server would be actively used for federation. Verify that the external DNS SRV record points to the correct Edge Server. If you want to deploy multiple federation Edge Server to be active concurrently (that is, not a migration scenario), verify that all federated partners are using Office Communications Server 2007 R2 or Lync Server. Verify that the external DNS SRV record lists all federation enabled Edge Servers.</STRONG><BR>This warning is expected and can be safely ignored.



## To verify federation and remote access for external users

1.  From the Lync Server 2013 Front End Server, open the Lync Server Management Shell.

2.  To verify the status of federation and remote access, from the command line, type the following:
    
        Get-CsAccessEdgeConfiguration

3.  To enable federation and remote access, from the command line, type the following:
    
        Set-CsAccessEdgeConfiguration
    
    For more information on these cmdlets, see the following topics: [Get-CsAccessEdgeConfiguration](https://technet.microsoft.com/en-us/library/gg398574\(v=ocs.15\)) and [Set-CsAccessEdgeConfiguration](https://technet.microsoft.com/en-us/library/gg413017\(v=ocs.15\)).

4.  Wait until replication has completed before bringing the Lync Server 2013 Edge servers online, and testing federation and external access.

## To configure Lync Server 2013 Edge Server

1.  Bring all of the Lync Server 2013 Edge Servers online.

2.  Update the external firewall routing rules or the hardware load balancer settings to send SIP traffic for external access (usually port 443) and federation (usually port 5061) to the Lync Server 2013 Edge Server, instead of the legacy Edge Server.
    

    > [!NOTE]  
    > If you do not have a hardware load balancer, you need to update the DNS A record for federation to resolve the new Lync Server Access Edge server. To accomplish this with minimum disruption, reduce the TTL value for the external Lync Server Access Edge FQDN so that when DNS is updated to point to the new Lync Server Access Edge server, federation and remote access will be updated quickly.



3.  Next, stop the **Lync Server Access Edge** from each Edge Server computer.

4.  From each legacy Edge Server computer, open the **Services** applet from the **Administrative Tools**.

5.  In the services list, find **Office Communications Server Access Edge**.

6.  Right-click the services name, and then select **Stop** to stop the service.

7.  Set the Startup type to **Disabled**.

8.  Click **OK** to close the **Properties** window.

## To Test Connectivity of External Users and External access

  - Users from at least one federated domain, an internal user on Lync Server 2013 and a user on Office Communications Server 2007 R2. Test instant messaging (IM), presence, audio/video (A/V), and desktop sharing.

  - Users of each public IM service provider that your organization supports (and for which provisioning has been completed) communicating with a user on Lync Server 2013 and a user on Office Communications Server 2007 R2.

  - Verify anonymous users are able to join conferences.

  - A user hosted on Office Communications Server 2007 R2 using remote user access (logging into Office Communications Server 2007 R2 from outside the intranet but without VPN) with a user on Lync Server 2013, and a user on Office Communications Server 2007 R2. Test IM, presence, A/V, and desktop sharing.

  - A user hosted on Lync Server 2013 using remote user access (logging into Lync Server 2013 from outside the intranet but without VPN) with a user on Lync Server 2013, and a user on Office Communications Server 2007 R2. Test IM, presence, A/V, and desktop sharing.

