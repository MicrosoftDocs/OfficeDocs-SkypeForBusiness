---
title: 'Example of gathering your requirements for call admission control'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: "Example of gathering your requirements for call admission control"
ms:assetid: 3363ac53-b7c4-4a59-aea1-b2f3ee016ae1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425827(v=OCS.15)
ms:contentKeyID: 48183820
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Example: Gathering your requirements for call admission control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

This example shows you how to plan for and implement call admission control (CAC). At a high level, this consists of the following activities:

1.  Identify all of your network hubs and backbones (known as *network regions*).

2.  Identify the Lync Server central site that will manage CAC for each network region.

3.  Identify and define the *network sites* that are connected to each network region.

4.  For each network site whose connection to the WAN is bandwidth-constrained, describe the bandwidth capacity of the WAN connection and the bandwidth limits that to the network administrator has set for Lync Server media traffic, if applicable. You do not need to include sites whose connection to the WAN is not bandwidth-constrained.

5.  Associate each subnet in your network with a network site.

6.  Map the links between the network regions. For each link, describe its bandwidth capacity and any limits that the network administrator has placed on Lync Server media traffic.

7.  Define a route between every pair of network regions.

<div>

## Gather the Required Information

To prepare for call admission control, gather the information described in the following steps:

1.  Identify your network regions. A network region represents a network backbone or a network hub.
    
    A network backbone or a network hub is a part of computer network infrastructure that interconnects various pieces of network, providing a path for the exchange of information between different LANs or subnets. A backbone can tie together diverse networks, from a small location to a wide geographic area. The backbone's capacity is typically greater than that of the networks connected to it.
    
    Our example topology has three network regions: North America, EMEA, and APAC. A network region contains a collection of network sites. Work with your network administrator to define the network regions for your enterprise.

2.  Identify each network region’s associated central site. A central site contains at least one Front End Server and is the Lync Server deployment that will manage CAC for all media traffic that passes through the network region’s WAN connection.
    
    **An example enterprise network divided into three network regions**
    
    ![Network Topology Example with 3 Network Regions](images/Gg425827.08937347-250f-488f-ba5f-c256e6afcd8b(OCS.15).jpg "Network Topology Example with 3 Network Regions")  
    
    <div>
    

    > [!NOTE]
    > A Multiprotocol Label Switching (MPLS) network should be represented as a network region in which each geographic location has a corresponding network site. For details, see the “<A href="lync-server-2013-call-admission-control-on-an-mpls-network.md">Call admission control on an MPLS network with Lync Server 2013</A>” topic in the Planning documentation.

    
    </div>
    
    In the preceding example network topology, there are three network regions, each with a Lync Server central site that manages CAC. The appropriate central site for a network region is chosen by the geographic vicinity. Because media traffic will be heaviest within network regions, the ownership by geographic vicinity makes it self-contained and will continue to be functional even if other central sites become unavailable.
    
    In this example, a Lync Server deployment named Chicago is the central site for the North America region.
    
    All Lync users in North America are homed on servers in the Chicago deployment. The following table shows central sites for all three network regions.
    
    ### Network Regions and their Associated Central Sites
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Network Region</th>
    <th>Central Site</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>North America</p></td>
    <td><p>Chicago</p></td>
    </tr>
    <tr class="even">
    <td><p>EMEA</p></td>
    <td><p>London</p></td>
    </tr>
    <tr class="odd">
    <td><p>APAC</p></td>
    <td><p>Beijing</p></td>
    </tr>
    </tbody>
    </table>
    
    <div>
    

    > [!NOTE]
    > Depending on your Lync Server topology, the same central site can be assigned to multiple network regions.

    
    </div>

3.  For each network region, identify all of the network sites (offices or locations) whose WAN connections are not bandwidth-constrained. Because these sites are not bandwidth constrained, you do not need to apply CAC bandwidth policies to them.
    
    In the example shown in the following table, three network sites do not have bandwidth-constrained WAN links: New York, Chicago, and Detroit.
    
    ### Network Sites not Constrained by WAN Bandwidth
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Network Site</th>
    <th>Network Region</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>New York</p></td>
    <td><p>North America</p></td>
    </tr>
    <tr class="even">
    <td><p>Chicago</p></td>
    <td><p>North America</p></td>
    </tr>
    <tr class="odd">
    <td><p>Detroit</p></td>
    <td><p>North America</p></td>
    </tr>
    </tbody>
    </table>


4.  For each network region, identify all of the network sites that connect to the network region through bandwidth-constrained WAN links.
    
    To help ensure audio and video quality, we recommend that these bandwidth-constrained network sites have their WANs monitored and CAC bandwidth policies that limit media (voice or video) traffic flow to and from the network region.
    
    In the example shown in the following table, there are three network sites that are constrained by WAN bandwidth: Portland, Reno and Albuquerque.
    
    ### Network Sites Constrained by WAN Bandwidth
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Network Site</th>
    <th>Network Region</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Albuquerque</p></td>
    <td><p>North America</p></td>
    </tr>
    <tr class="even">
    <td><p>Reno</p></td>
    <td><p>North America</p></td>
    </tr>
    <tr class="odd">
    <td><p>Portland</p></td>
    <td><p>North America</p></td>
    </tr>
    </tbody>
    </table>
    
    **CAC network region North America with three network sites that are unconstrained by bandwidth (Chicago, New York, and Detroit) and three network sites that are constrained by WAN bandwidth (Portland, Reno, and Albuquerque)**
    
    ![Example network sites constrained by WAN bandwidth](images/Gg425827.d9d1f231-db4d-4dd7-8fbc-eb0b6d1e705d(OCS.15).jpg "Example network sites constrained by WAN bandwidth")  

5.  For each bandwidth-constrained WAN link, determine the following:
    
      - Overall bandwidth limit that you want to set for all concurrent audio sessions. If a new audio session will cause this limit to be exceeded, Lync Server does not allow the session to start.
    
      - Bandwidth limit that you want to set for each individual audio session. The default CAC bandwidth limit is 175 kbps, but it can be modified by the administrator.
    
      - Overall bandwidth limit that you want to set for all concurrent video sessions. If a new video session will cause this limit to be exceeded, Lync Server does not allow the session to start.
    
      - Bandwidth limit that you want to set for each individual video session. The default CAC bandwidth limit is 700 kbps, but it can be modified by the administrator.
    
    ### Network Sites with WAN Bandwidth Constraint Information (Bandwidth in kbps)
    
    <table style="width:100%;">
    <colgroup>
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Network Site</th>
    <th>Network Region</th>
    <th>BW Limit</th>
    <th>Audio Limit</th>
    <th>Audio Session Limit</th>
    <th>Video Limit</th>
    <th>Video Session Limit</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Albuquerque</p></td>
    <td><p>North America</p></td>
    <td><p>5,000</p></td>
    <td><p>2,000</p></td>
    <td><p>175</p></td>
    <td><p>1,400</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="even">
    <td><p>Reno</p></td>
    <td><p>North America</p></td>
    <td><p>10,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="odd">
    <td><p>Portland</p></td>
    <td><p>North America</p></td>
    <td><p>5,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="even">
    <td><p>New York</p></td>
    <td><p>North America</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    </tr>
    <tr class="odd">
    <td><p>Chicago</p></td>
    <td><p>North America</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    </tr>
    <tr class="even">
    <td><p>Detroit</p></td>
    <td><p>North America</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    </tr>
    </tbody>
    </table>


6.  For every subnet in your network, specify its associated network site.
    
    <div>
    

    > [!IMPORTANT]
    > Every subnet in your network must be associated with a network site, even if the network site is not bandwidth constrained. This is because call admission control uses subnet information to determine at which network site an endpoint is located. When the locations of both parties in the session are determined, call admission control can determine if there is sufficient bandwidth to establish a call. When a session is established over a link that has no bandwidth limits, an alert is generated.<BR>If you deploy Audio/Video Edge Servers, the public IP addresses of each Edge Server must be associated with the network site where the Edge Server is deployed. Each public IP address of the A/V Edge Server must be added to your network configuration settings as a subnet with a subnet mask of 32. For example, if you deploy A/V Edge Servers in Chicago, then for each external IP address of those servers create a subnet with a subnet mask of 32 and associate network site Chicago with those subnets. For details about public IP addresses, see <A href="lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md">Determine external A/V firewall and port requirements for Lync Server 2013</A> in the Planning documentation.

    
    </div>
    
    <div>
    

    > [!NOTE]
    > A Key Health Indicator (KHI) alert is raised, specifying a list of IP addresses that are present in your network but are either not associated with a subnet, or the subnet that includes the IP addresses is not associated with a network site. This alert will not be raised more than once within an 8 hour period. The relevant alert information and an example are as follows:<BR><STRONG>Source:</STRONG> CS Bandwidth Policy Service (Core)<BR><STRONG>Event number:</STRONG> 36034<BR><STRONG>Level:</STRONG> 2<BR><STRONG>Description:</STRONG> The subnets for the following IP Addresses: &lt;List of IP Addresses&gt; are either not configured or the subnets are not associated to a network site.<BR><STRONG>Cause:</STRONG> The subnets for the corresponding IP addresses are missing from the network configuration settings or the subnets are not associated to a network site.<BR><STRONG>Resolution:</STRONG> Add subnets corresponding to the preceding list of IP addresses into the network configuration settings and associate every subnet to a network site.<BR>For example, if the IP address list in the alert specifies 10.121.248.226 and 10.121.249.20, either these IP addresses are not associated with a subnet, or the subnet that they are associated with does not belong to a network site. If 10.121.248.0/24 and 10.121.249.0/24 are the corresponding subnets for these addresses, you can resolve this issue as follows: 
    > <OL>
    > <LI>
    > <P>Be sure that IP address 10.121.248.226 is associated with the 10.121.248.0/24 subnet and IP address 10.121.249.20 is associated with the 10.121.249.0/24 subnet.</P>
    > <LI>
    > <P>Be sure that the 10.121.248.0/24 and 10.121.249.0/24 subnets are each associated with a network site.</P></LI></OL>

    
    </div>
    
    ### Network Sites and Associated Subnets (Bandwidth in kbps)
    
    <table>
    <colgroup>
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Network Site</th>
    <th>Network Region</th>
    <th>BW Limit</th>
    <th>Audio Limit</th>
    <th>Audio Session Limit</th>
    <th>Video Limit</th>
    <th>Video Session Limit</th>
    <th>Subnets</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Albuquerque</p></td>
    <td><p>North America</p></td>
    <td><p>5,000</p></td>
    <td><p>2,000</p></td>
    <td><p>175</p></td>
    <td><p>1,400</p></td>
    <td><p>700</p></td>
    <td><p>172.29.79.0/23, 157.57.215.0/25, 172.29.90.0/23, 172.29.80.0/24</p></td>
    </tr>
    <tr class="even">
    <td><p>Reno</p></td>
    <td><p>North America</p></td>
    <td><p>10,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    <td><p>157.57.210.0/23, 172.28.151.128/25</p></td>
    </tr>
    <tr class="odd">
    <td><p>Portland</p></td>
    <td><p>North America</p></td>
    <td><p>5,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    <td><p>172.29.77.0/24 10.71.108.0/24, 157.57.208.0/23</p></td>
    </tr>
    <tr class="even">
    <td><p>New York</p></td>
    <td><p>North America</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24</p></td>
    </tr>
    <tr class="odd">
    <td><p>Chicago</p></td>
    <td><p>North America</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>157.57.211.0/23, 172.28.152.128/25</p></td>
    </tr>
    <tr class="even">
    <td><p>Detroit</p></td>
    <td><p>North America</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>(no limit)</p></td>
    <td><p>172.29.78.0/24 10.71.109.0/24, 157.57.209.0/23</p></td>
    </tr>
    </tbody>
    </table>


7.  In Lync Server call admission control, the connections between network regions are called *region links*. For each region link, determine the following, just as you did for the network sites:
    
      - Overall bandwidth limit that you want to set for all concurrent audio sessions. If a new audio session will cause this limit to be exceeded, Lync Server does not allow the session to start.
    
      - Bandwidth limit that you want to set for each individual audio session. The default CAC bandwidth limit is 175 kbps, but it can be modified by the administrator.
    
      - Overall bandwidth limit that you want to set for all concurrent video sessions. If a new video session will cause this limit to be exceeded, Lync Server does not allow the session to start.
    
      - Bandwidth limit that you want to set for each individual video session. The default CAC bandwidth limit is 700 kbps, but it can be modified by the administrator.
    
    **Network Region links with associated bandwidth limits**
    
    ![Example of Limitations between 3 Regions](images/Gg425827.25259afa-ee7c-4d26-bc41-92ba9cb56dec(OCS.15).jpg "Example of Limitations between 3 Regions")  
    
    ### Region Link Bandwidth Information (Bandwidth in kbps)
    
    <table>
    <colgroup>
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Region Link Name</th>
    <th>First Region</th>
    <th>Second Region</th>
    <th>BW Limit</th>
    <th>Audio Limit</th>
    <th>Audio Session Limit</th>
    <th>Video Limit</th>
    <th>Video Session Limit</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>NA-EMEA-LINK</p></td>
    <td><p>North America</p></td>
    <td><p>EMEA</p></td>
    <td><p>50,000</p></td>
    <td><p>20,000</p></td>
    <td><p>175</p></td>
    <td><p>14,000</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="even">
    <td><p>EMEA-APAC-LINK</p></td>
    <td><p>EMEA</p></td>
    <td><p>APAC</p></td>
    <td><p>25,000</p></td>
    <td><p>10,000</p></td>
    <td><p>175</p></td>
    <td><p>7,000</p></td>
    <td><p>700</p></td>
    </tr>
    </tbody>
    </table>


8.  Define a route between every pair of network regions.
    
    <div>
    

    > [!NOTE]
    > Two links are required for the route between the North America and APAC regions because there is no region link that directly connects them.

    
    </div>
    
    ### Region Routes
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Region Route Name</th>
    <th>First Region</th>
    <th>Second Region</th>
    <th>Region Links</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>NA-EMEA-ROUTE</p></td>
    <td><p>North America</p></td>
    <td><p>EMEA</p></td>
    <td><p>NA-EMEA-LINK</p></td>
    </tr>
    <tr class="even">
    <td><p>EMEA-APAC-ROUTE</p></td>
    <td><p>EMEA</p></td>
    <td><p>APAC</p></td>
    <td><p>EMEA-APAC-LINK</p></td>
    </tr>
    <tr class="odd">
    <td><p>NA-APAC-ROUTE</p></td>
    <td><p>North America</p></td>
    <td><p>APAC</p></td>
    <td><p>NA-EMEA-LINK, EMEA-APAC-LINK</p></td>
    </tr>
    </tbody>
    </table>


9.  For every pair of network sites that are directly connected by a single link (called an *inter-site* link), determine the following:
    
      - Overall bandwidth limit that you want to set for all concurrent audio sessions. If a new audio session will cause this limit to be exceeded, Lync Server does not allow the session to start.
    
      - Bandwidth limit that you want to set for each individual audio session. The default CAC bandwidth limit is 175 kbps, but it can be modified by the administrator.
    
      - Overall bandwidth limit that you want to set for all concurrent video sessions. If a new video session will cause this limit to be exceeded, Lync Server does not allow the session to start.
    
      - Bandwidth limit that you want to set for each individual video session. The default CAC bandwidth limit is 700 kbps, but it can be modified by the administrator.
    
    **CAC network region North America showing the bandwidth capacities and bandwidth limits for the inter-site link between Reno and Albuquerque**
    
    ![Network Sites Constrained by WAN Bandwidth example](images/Gg425827.063e5e1d-b6c8-4e8c-98db-c227c78f671d(OCS.15).jpg "Network Sites Constrained by WAN Bandwidth example")  
    
    ### Bandwidth Information for an Inter-Site Link between Two Network Sites (Bandwidth in kbps)
    
    <table>
    <colgroup>
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Inter-Site Link Name</th>
    <th>First Site</th>
    <th>Second Site</th>
    <th>BW Limit</th>
    <th>Audio Limit</th>
    <th>Audio Session Limit</th>
    <th>Video Limit</th>
    <th>Video Session Limit</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Reno-Albu-Intersite-Link</p></td>
    <td><p>Reno</p></td>
    <td><p>Albuquerque</p></td>
    <td><p>20,000</p></td>
    <td><p>12,000</p></td>
    <td><p>175</p></td>
    <td><p>5,000</p></td>
    <td><p>700</p></td>
    </tr>
    </tbody>
    </table>


<div>

## Next Steps

After you have gathered the required information, you can perform CAC deployment either by using the Lync Server Management Shell or Lync Server Control Panel.

<div>


> [!NOTE]
> Although you can perform most network configuration tasks by using Lync Server Control Panel, to create subnets and intersite links, you must use Lync Server Management Shell. For details, see the Lync Server Management Shell documentation for the <STRONG>New-CsNetworkSubnet</STRONG> cmdlet and the <STRONG>New-CsNetworkIntersitePolicy</STRONG> cmdlet.



</div>

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

