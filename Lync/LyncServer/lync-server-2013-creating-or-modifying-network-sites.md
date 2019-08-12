---
title: 'Lync Server 2013: Creating or modifying network sites'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Creating or modifying network sites
ms:assetid: 358aa08a-c5bc-45fc-8017-19e6202f88c5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520975(v=OCS.15)
ms:contentKeyID: 48183801
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Creating or modifying network sites in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-08_

Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can use the Microsoft Lync Server 2013 Control Panel to configure sites and associate them with regions. For example, a network region for North America might be associated with networks sites such as Chicago, Redmond, and Vancouver. A CAC network site must be created for every site within an organization, even if that site has no bandwidth limitations. From the Lync Server Control Panel you can create, modify, and delete network sites. Use the following procedures to create or modify a network site. For details on deleting an existing network site, see [Deleting an existing network site in Lync Server 2013](lync-server-2013-deleting-an-existing-network-site.md).

<div>

## To create a network site

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Site**.

4.  On the **Site** page, click **New**.

5.  In **New Site**, type a name for this site in the **Name** field.
    
    <div>
    

    > [!NOTE]  
    > Site names must be unique within the Lync Server 2013 deployment.

    
    </div>

6.  In the **Region** drop-down list, select a network region to associate with this site.

7.  (Optional) If you want to place bandwidth limitations on audio or video calls to this site, select the bandwidth policy profile with the appropriate settings from the **Bandwidth policy** drop-down list.
    
    <div>
    

    > [!NOTE]  
    > You can view the details of the available bandwidth policy profiles, or create a new bandwidth policy profile, on the <STRONG>Policy Profile</STRONG> page of the <STRONG>Network Configuration</STRONG> group. For details, see <A href="lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md">Creating or modifying bandwidth policy profiles in Lync Server 2013</A>.

    
    </div>

8.  (Optional) If you want to provide location settings for this site, select a location policy from the **Location policy** drop-down list.
    
    <div>
    

    > [!NOTE]  
    > The location policy assigns specific Enhanced 9-1-1 (E9-1-1) and client location settings to the site. You can view the details of the available location policies, or create a new location policy, from the <STRONG>Location Policy</STRONG> page of the <STRONG>Network Configuration</STRONG> group. For details, see <A href="lync-server-2013-viewing-location-policy-information.md">Viewing location policy information in Lync Server 2013</A>.

    
    </div>

9.  (Optional) Type a value in the **Description** field to provide more information about this site that cannot be expressed by the name alone.

10. Click **Commit**.
    
    <div>
    

    > [!NOTE]  
    > You do not use the <STRONG>Associated Subnets</STRONG> table when you create a new network site. You associate a subnet with a site when you create or modify the subnet. For details, see <A href="lync-server-2013-create-or-modify-network-subnets.md">Create or modify network subnets in Lync Server 2013</A>.

    
    </div>

</div>

<div>

## To modify a network site

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Site**.

4.  On the **Site** page, click the site that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Site** page, you can modify the description, region, bandwidth policy profile, and location policy associated with the site. For details, see "To create a network site" section earlier in this topic.

7.  Click **Commit**.

You cannot modify the **Associated Subnets** table on this page. The list of associated subnets is provided for reference so that you are aware of what subnets will be affected when you modify the site settings.

</div>

<div>

## To delete a network site

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Site**.

4.  On the **Site** page, click the site that you want to delete.
    
    <div>
    

    > [!NOTE]  
    > You can delete more than one site at a time. To do this, press CTRL and select multiple sites while holding down the CTRL key. Or, to select all sites, click <STRONG>Select all</STRONG> on the <STRONG>Edit</STRONG> menu.

    
    </div>

5.  On the **Edit** menu, click **Delete**.

6.  Click **OK**.
    
    <div>
    

    > [!WARNING]  
    > You cannot remove a network site if it is associated with a network subnet. If you attempt to remove a site associated with a subnet you will receive an error message. To see if a site is associated with any subnets, click the site and then click <STRONG>Show details</STRONG> on the <STRONG>Edit</STRONG> menu.

    
    </div>

</div>

<div>

## See Also


[Deleting an existing network site in Lync Server 2013](lync-server-2013-deleting-an-existing-network-site.md)  


[New-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkSite)  
[Set-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkSite)  
[Remove-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkSite)  
[Get-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkSite)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

