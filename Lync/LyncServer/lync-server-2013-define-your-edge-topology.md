---
title: 'Lync Server 2013: Define your edge topology'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Define your edge topology
ms:assetid: 787b23f1-8fa0-4c37-abf2-c516c5dd66f0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398591(v=OCS.15)
ms:contentKeyID: 48184562
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define your edge topology in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

You must use Topology Builder to build your topology and you must set up at least one internal Front End pool or Standard Edition server before you can deploy your Edge Server. Use the following procedure to define the edge topology for a single Edge Server, and then use the procedures in [Publish your topology in Lync Server 2013](lync-server-2013-publish-your-topology.md) and [Export your Lync Server 2013 topology and copy it to external media for edge installation](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md) to publish the topology and make it available to your Edge Server.

<div>


> [!NOTE]  
> The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one Edge interface and hardware load balancing on the other Edge interface.



</div>

To successfully publish, enable, or disable a topology when adding or removing a server role, you must be logged in as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. You can also grant the administrator rights and permissions required for adding server roles to a user account. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) in the Standard Edition server or Enterprise Edition server Deployment documentation. For other configuration changes, only membership in the RTCUniversalServerAdmins group is required.

If you defined your edge topology when you defined and published your internal topology, and no changes are required to the edge topology that you previously defined, you do not need to do define it and publish it again. Use the following procedure only if you need to make changes to your edge topology. You must make the previously defined and published topology available to your Edge Servers, which you do by using the procedure in [Export your Lync Server 2013 topology and copy it to external media for edge installation](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md).

<div>


> [!IMPORTANT]  
> You cannot run Topology Builder from an Edge Server. You must run it from your Front End Server or Standard Edition servers.



</div>

The process to define your Edge Server topology is done in Topology Builder. The three primary types of Edge Server topologies that you plan and configure are listed below:

  - To define the Topology for a Single Edge Server

  - To define the Topology for a Load Balanced Edge Server Pool

  - To define the Topology for a Hardware Load Balanced Edge Pool

<div>

## To define the topology for a single Edge Server

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In the console tree, expand the site in which you want to deploy an Edge Server.

3.  Right-click **Edge pools**, and then click **New Edge Pool**.

4.  In **Define the New Edge Pool**, click **Next**.

5.  In **Define the Edge pool FQDN**, do the following:
    
      - In **Pool FQDN**, type the fully qualified domain name (FQDN) of the internal interface for the Edge Server.
        
        <div>
        

        > [!IMPORTANT]  
        > The name you specify must be identical to the computer name configured on the server. By default the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. So, you must configure a DNS suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. Use only standard characters (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (when the FQDN must be assigned to the SN in the certificate). For details about adding a DNS suffix to a computer name, see <A href="lync-server-2013-configure-dns-for-edge-support.md">Configure DNS for edge support in Lync Server 2013</A>.

        
        </div>
    
      - Click **Single computer pool**, and then click **Next**.

6.  In **Select features**, do the following:
    
      - If you plan to use a single FQDN and IP address for the SIP Access service, Lync Server 2013 Web Conferencing service, and A/V Edge services, select the **Use a single FQDN and IP Address** check box.
    
      - If you plan to enable federation select the **Enable federation for this Edge pool (Port 5061)** check box.
        
        <div>
        

        > [!NOTE]  
        > You can select this option, but only one Edge pool or Edge Server in your organization can be published externally for federation. All access by federated users, including public instant messaging (IM) users, go through the same Edge pool or single Edge Server. For example, if your deployment includes an Edge pool or single Edge Server deployed in New York and one deployed in London and you enable federation support on the New York Edge pool or single Edge Server, signal traffic for federated users will go through the New York Edge pool or single Edge Server. This is true even for communications with London users, although a London internal user calling a London federated user uses the London pool or Edge Server for A/V traffic.

        
        </div>
    
      - If you plan to support the extensible messaging and presence protocol (XMPP) for your deployment, select the **Enable XMPP federation (port 5269)** check box

7.  In **Select IP Options**, do the following:
    
      - **Enable IPv4 on internal interface**: Select the check box if you want to apply an IPv4 address to the Edge Server or Edge pool internal interface
    
      - **Enable IPv6 on internal interface**: Select the check box if you want to apply an IPv6 address to the Edge Server or Edge pool internal interface
    
      - **Enable IPv4 on external interface**: Select the check box if you want to apply an IPv4 address to the Edge Server or Edge pool external interface
    
      - **Enable IPv6 on external interface**: Select the check box if you want to apply an IPv6 address to the Edge Server or Edge pool external interface
    
    You can also configure the Edge Server or Edge pool to use a network address translation address for the external IP addresses. You do this by selecting the check box **The external IP address of this Edge pool is translated by NAT**.

8.  In **External FQDNs**, do the following:
    
      - If in **Select features** you chose to use a single FQDN and IP address for the SIP access, Web Conferencing service, and A/V Edge service, type the external FQDN in **SIP Access**.
        
        <div>
        

        > [!NOTE]  
        > If you choose this option, you must specify a different port number for each of the edge services (recommended port settings: 5061 for Access Edge service, 444 for Web Conferencing Edge service, and 443 for A/V Edge service). Selecting this option can help prevent potential connectivity issues, and simplify the configuration because you can then use the same port number (for example, 443) for all three services.

        
        </div>
    
      - If in **Select features** you did not chose to use a single FQDN and IP Address, type the External FQDNs for **SIP Access**, **Web Conferencing** and **Audio Video**, keeping the default ports.

9.  Click **Next**.

10. In **Define the Internal IP address**, type the IP address of your Edge Server in **Internal IPv4 address** and **Internal IPv6 address** as is appropriate for your requirements. Click **Next**.

11. In **Define the External IP address**, do the following:
    
      - If you chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IPv4 address of the Edge Server in **SIP Access**, and then, click **Next**.
    
      - If you chose to use IPv6 addresses, type the external IPv6 address of the Edge Server in **SIP Access**, and then, click **Next**.
    
      - If you did not chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IPv4 addresses of the Edge Server in **SIP Access**, **Web Conferencing**, and **A/V Conferencing**, and then click **Next**.
    
      - If you chose to use IPv6 addresses and did not chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IPv6 addresses of the Edge Server in **SIP Access**, **Web Conferencing**, and **A/V Conferencing**, and then click **Next**.
        
        <div>
        

        > [!NOTE]  
        > If you did not choose to enable and assign IPv6 addressing, you will not see this dialog box.

        
        </div>

12. If you chose to use NAT, a dialog box appears. In **Public IPv4 address for the A/V Edge service**, type the public IPv4 address to be translated by NAT, and then click **Next**.
    
    <div>
    

    > [!NOTE]  
    > This should be the external IP address of the A/V Edge service.

    
    </div>

13. If you chose to use NAT and IPv6 addresses, a dialog box appears. In **Public IPv6 address for the A/V Edge service**, type the public IPv6 address to be translated by NAT, and then click **Next**.
    
    <div>
    

    > [!NOTE]  
    > This should be the external IP address of the A/V Edge service.

    
    </div>

14. In **Define the next hop**, in **Next hop pool**, select the name of the internal pool, which can be either a Front End pool or a Standard Edition pool. Or, if your deployment includes a Director, select the Director. Then, click **Next**.

15. In **Associate Front End pools**, specify one or more internal pools, which can include Front End pools and Standard Edition servers, to be associated with this Edge Server, by selecting the names of the internal pools that are to use this Edge Server for communication with supported external users.
    
    <div>
    

    > [!NOTE]  
    > Only one load-balanced Edge pool or single Edge Server can be associated with each internal pool for A/V traffic. If you already have an internal pool associated with an Edge pool or Edge Server, a warning appears indicating that the internal pool is already associated an Edge pool or Edge Server. If you select a pool that is already associated with another Edge Server, it will change the association.

    
    </div>

16. Click **Finish**.

17. Publish your topology.

</div>

<div>

## To define the topology for a DNS load balanced Edge Server pool

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In the console tree, expand the site in which you want to deploy Edge Servers.

3.  Right-click **Edge Pools**, and then click **New Edge Pool**.

4.  In **Define the New Edge Pool**, click **Next**.

5.  In **Define the Edge pool FQDN**, do the following:
    
      - In **Pool FQDN**, type the fully qualified domain name (FQDN) for the internal connection of the Edge pool.
        
        <div>
        

        > [!IMPORTANT]  
        > The name you specify for the pool must be the internal edge pool name. This must be defined as a FQDN. Topology Builder uses FQDNs, not short names. Use only standard characters (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (when the FQDN must be assigned to the SN in the certificate).

        
        </div>
    
      - Click **Multiple computer pool**, and then click **Next**.

6.  In **Select features**, do the following:
    
      - If you plan to use a single FQDN and IP address for the SIP access, Lync Server 2013 Web Conferencing service and A/V Edge services, select the **Use a single FQDN and IP Address** check box.
    
      - If you plan to enable federation, select the **Enable federation for this Edge pool (Port 5061)** check box. Click **Next**
        
        <div>
        

        > [!NOTE]  
        > You can select this option, but only one Edge pool or Edge Server in your organization can be published externally for federation. All access by federated users, including public instant messaging (IM) users, go through the same Edge pool or single Edge Server. For instance, if your deployment includes an Edge pool or single Edge Server deployed in New York and one deployed in London and you enable federation support on the New York Edge pool or single Edge Server, signal traffic for federated users will go through the New York Edge pool or single Edge Server. This is true even for communications with London users, although a London internal user calling a London federated user uses the London pool or Edge Server for A/V traffic.

        
        </div>
    
      - If you plan to support the extensible messaging and presence protocol (XMPP) for your deployment, select the **Enable XMPP federation (port 5269)** check box

7.  Click **Next**.

8.  In **Select IP Options**, do the following:
    
      - **Enable IPv4 on internal interface**: Select the check box if you want to apply an IPv4 address to the Edge Server or Edge pool internal interface
    
      - **Enable IPv6 on internal interface**: Select the check box if you want to apply an IPv6 address to the Edge Server or Edge pool internal interface
    
      - **Enable IPv4 on external interface**: Select the check box if you want to apply an IPv4 address to the Edge Server or Edge pool external interface
    
      - **Enable IPv6 on external interface**: Select the check box if you want to apply an IPv6 address to the Edge Server or Edge pool external interface
    
    You can also configure the Edge Server or Edge pool to use a network address translation address for the external IP addresses. You do this by selecting the check box **The external IP address of this Edge pool is translated by NAT**.

9.  In **External FQDNs**, do the following:
    
      - If in **Select features** you chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external FQDN in **SIP Access**.
        
        <div>
        

        > [!NOTE]  
        > If you choose this option, you must specify a different port number for each of the Edge services (recommended port settings: 5061 for Access Edge service, 444 for Web Conferencing Edge service, and 443 for A/V Edge service). By selecting this option, you can help prevent potential connectivity issues and simplify the configuration because you can then use the same port number (for example, 443) for all three services.

        
        </div>
    
      - If in **Select features** you did not chose to use a single FQDN and IP Address, type the FQDN that you have chosen for your public facing side of the edge pool for in **SIP Access**. In **Web Conferencing**, type the FQDN you have chosen for your public facing side of the Edge pool. In **Audio/Video**, type the FQDN you have chosen for your public facing side of the Edge pool. Use the default ports.

10. Click **Next**.

11. In **Define the computers in this pool**, click **Add**.

12. In **Internal FQDN and IP address**, do the following:
    
      - In **Internal IPv4 address**, type the IPv4 address and **Internal IPv6 address** as is appropriate for your requirements for the first Edge Server that you want to create in this pool.
    
      - In **Internal FQDN**, type the FQDN of the first Edge Server that you want to create in this pool.
        
        <div>
        

        > [!NOTE]  
        > The name you specify must be identical to the computer name configured on the server. By default, the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. So, you must configure a DNS suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. Use only standard characters (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, pools, and arrays. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (when the FQDN must be assigned to the SN in the certificate). For details about adding a DNS suffix to a computer name, see <A href="lync-server-2013-configure-dns-for-edge-support.md">Configure DNS for edge support in Lync Server 2013</A>.

        
        </div>

13. Click **Next**.

14. In **Define the external IP addresses**, do the following:
    
      - If you chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IP address of the Edge Server in **SIP Access**.
    
      - If you did not chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Conferencing service, type the IP address that you have chosen for your public facing side of this Edge pool server for **SIP Access**. In **Web Conferencing**, type the IP address that you have chosen for your public facing side of this Edge pool server. In **A/V Conferencing**, type the IP address you have chosen for your public facing side of this Edge pool server.

15. Click **Next**.

16. If you chose to enable IPv6 addresses, In **Define the external IP addresses**, do the following:
    
      - If you chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IPv6 address of the Edge Server in **SIP Access**.
    
      - If you did not chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Conferencing service, type the IPv6 address that you have chosen for your public facing side of this Edge pool server for **SIP Access**. In **Web Conferencing**, type the IPv6 address that you have chosen for your public facing side of this Edge pool server. In **A/V Conferencing**, type the IPv6 address you have chosen for your public facing side of this Edge pool server.
    
    <div>
    

    > [!NOTE]  
    > If you did not choose to enable and assign IPv6 addressing, you will not see this dialog box.

    
    </div>

17. Click **Finish**.
    
    <div>
    

    > [!NOTE]  
    > You will now see the first Edge Server you created in your pool in the <STRONG>Define the computers in this pool</STRONG> dialog box.

    
    </div>

18. In **Define the computers in this pool**, click **Add**, and then repeat steps 11 through 14 for the second Edge Server that you want to add to you Edge pool.

19. After you repeat steps 11 through 14, click **Next** in **Define the computers in this pool**.
    
    <div>
    

    > [!NOTE]  
    > At this point, you can see both of the Edge Servers in your pool.

    
    </div>

20. If you chose to use NAT, a dialog box appears. In **Public IP address**, type the public IPv4 and IPv6 (as appropriate) addresses to be translated by NAT, and then click **Next**.
    
    <div>
    

    > [!NOTE]  
    > This should be the external IP Address of the A/V Edge.

    
    </div>

21. In **Define the next hop**, in the **Next hop pool** list, select the name of the internal pool, which can be either a Front End pool or a Standard Edition pool. Or, if your deployment includes a Director, select the name of the Director. Then, click **Next**.

22. In **Associate Front End pools**, specify one or more internal pools, which can include Front End pools and Standard Edition servers, to be associated with this Edge Server, by selecting the names of the internal pool(s) that is to use this Edge Server for communication with supported external users.
    
    <div>
    

    > [!NOTE]  
    > Only one load-balanced Edge pool or single Edge Server can be associated with each internal pool for A/V traffic. If you already have an internal pool associated with an Edge pool or Edge Server, a warning appears indicating that the internal pool is already associated an Edge pool or Edge Server. If you select a pool that is already associated with another Edge Server, it will change the association.

    
    </div>

23. Click **Finish**.

24. Publish your topology.

</div>

<div>

## To define the topology for a hardware load balanced Edge Server pool

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In the console tree, expand the site in which you want to deploy Edge Servers.

3.  Right-click **Edge Pools**, and then select **New Edge Pool**.

4.  In **Define the New Edge Pool**, click **Next**.

5.  In **Define the Edge pool FQDN**, do the following:
    
      - In **FQDN**, type the fully qualified domain name (FQDN) you have chosen for the internal side of the Edge pool.
        
        <div>
        

        > [!IMPORTANT]  
        > The name you specify for the pool must be the internal edge pool name. This must be defined as a FQDN. Topology Builder uses FQDNs, not short names. Use only standard characters (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (when the FQDN must be assigned to the SN in the certificate).

        
        </div>
    
    <!-- end list -->
    
      - Click **Multiple computer pool**, and then **Next**.

6.  In **Select features** do the following:
    
      - If you plan to use a single FQDN and IP address for the SIP access service, Lync Server Web Conferencing service, and A/V Edge service, select the **Use a single FQDN & IP Address** check box.
    
      - If you plan to enable federation, select the **Enable federation for this Edge pool (Port 5061)** check box.
        
        <div>
        

        > [!NOTE]  
        > You can select this option, but only one Edge pool or Edge Server in your organization may be published externally for federation. All access by federated users, including public instant messaging (IM) users, go through the same Edge pool or single Edge Server. For instance, if your deployment includes an Edge pool or single Edge Server deployed in New York and one deployed in London and you enable federation support on the New York Edge pool or single Edge Server, signal traffic for federated users will go through the New York Edge pool or single Edge Server. This is true even for communications with London users, although a London internal user calling a London federated user uses the London pool or Edge Server for A/V traffic.

        
        </div>
    
      - If you plan to support the extensible messaging and presence protocol (XMPP) for your deployment, select the **Enable XMPP federation (port 5269)** check box

7.  Click **Next**.

8.  In **Select IP Options**, do the following:
    
      - **Enable IPv4 on internal interface**: Select the check box if you want to apply an IPv4 address to the Edge Server or Edge pool internal interface
    
      - **Enable IPv6 on internal interface**: Select the check box if you want to apply an IPv6 address to the Edge Server or Edge pool internal interface
    
      - **Enable IPv4 on external interface**: Select the check box if you want to apply an IPv4 address to the Edge Server or Edge pool external interface
    
      - **Enable IPv6 on external interface**: Select the check box if you want to apply an IPv6 address to the Edge Server or Edge pool external interface
    
    <div>
    

    > [!IMPORTANT]  
    > <STRONG>Do Not</STRONG> select the <STRONG>The external IP address of the Edge pool is translated by NAT</STRONG> check box. Network address translation (NAT) is not supported when you are using hardware load balancing.

    
    </div>

9.  In **External FQDNs**, do the following:
    
      - If in **Select features** you chose to use a single FQDN and IP address for the SIP access, Web Conferencing service, and A/V Edge service, type the external FQDN in **SIP Access**.
        
        <div>
        

        > [!NOTE]  
        > If you choose to select this option, you must specify a different port number for each of the Edge services (recommended port settings: 5061 for Access Edge service, 444 for Web Conferencing Edge service, and 443 for A/V Edge service). By selecting this option, you can help prevent potential connectivity issues and simplify the configuration because you can then use the same port number (for example, 443) for all three services.

        
        </div>
    
      - If in **Select features** you did not chose to use a single FQDN and IP address, type the FQDN that you have chosen for your public facing side of the edge pool for in **SIP Access**. In **Web Conferencing**, type the FQDN you have chosen for your public facing side of the Edge pool. In **Audio/Video**, type the FQDN you have chosen for your public facing side of the Edge pool. Use the default ports.
        
        <div>
        

        > [!NOTE]  
        > These will be the publicly facing virtual IP (VIP) FQDNs for the pool.

        
        </div>

10. Click **Next**.

11. In **Define the computers in this pool**, click **Add**.

12. In **Define the external IP addresses**, do the following:
    
      - If you chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IPv4 address of the Edge Server in **SIP Access**.external IP address of the Edge Server in **SIP Access**.
    
      - If you did not chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Conferencing service, type the IP address that you have chosen for your public facing side of this Edge pool server for **SIP Access**. In **Web Conferencing**, type the IP address that you have chosen for your public facing side of this Edge pool server. In **A/V Conferencing**, type the IP address you have chosen for your public facing side of this Edge pool server.

13. Click **Next**.

14. If you chose to enable IPv6 addresses, In **Define the external IP addresses**, do the following:
    
      - If you chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Edge service, type the external IPv6 address of the Edge Server in **SIP Access**.
    
      - If you did not chose to use a single FQDN and IP Address for the SIP access, Web Conferencing service, and A/V Conferencing service, type the IPv6 address that you have chosen for your public facing side of this Edge pool server for **SIP Access**. In **Web Conferencing**, type the IPv6 address that you have chosen for your public facing side of this Edge pool server. In **A/V Conferencing**, type the IPv6 address you have chosen for your public facing side of this Edge pool server.
    
    <div>
    

    > [!NOTE]  
    > If you did not choose to enable and assign IPv6 addressing, you will not see this dialog box.

    
    </div>

15. Click **Finish**.
    
    <div>
    

    > [!NOTE]  
    > You will now see the first Edge Server you created in your pool in the <STRONG>Define the computers in this pool</STRONG> dialog box.

    
    </div>

16. In **Define the computers in this pool**, click **Add**, and then repeat steps 11 through 14 for the second Edge Server that you want to add to your Edge pool.

17. After you repeat steps 11 through 14, click **Next** in **Define the computers in this pool**.
    
    <div>
    

    > [!NOTE]  
    > At this point, you can see both of the Edge Servers in your pool.

    
    </div>

18. In **Define the next hop**, in the **Next hop pool** list, select the name of the internal pool, which can be either a Front End pool or a Standard Edition pool. Or, if your deployment includes a Director, select the name of the Director. Then, click **Next**.

19. In **Associate Front End pools**, specify one or more internal pools, which can include Front End pools and Standard Edition servers, to be associated with this Edge Server, by selecting the names of the internal pool(s) that is to use this Edge Server for communication with supported external users.
    
    <div>
    

    > [!NOTE]  
    > Only one load-balanced Edge pool or single Edge Server can be associated with each internal pool for A/V traffic. If you already have an internal pool associated with an Edge pool or Edge Server, a warning appears indicating that the internal pool is already associated an Edge pool or Edge Server. If you select a pool that is already associated with another Edge Server, it will change the association.

    
    </div>

20. Click **Finish**.

21. Publish your topology.

</div>

</div>

<span> </span>

</div>

</div>

</div>

