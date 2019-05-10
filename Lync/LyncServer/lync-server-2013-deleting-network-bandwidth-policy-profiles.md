---
title: 'Lync Server 2013: Deleting network bandwidth policy profiles'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deleting network bandwidth policy profiles
ms:assetid: 4d6beda8-6aa5-4d5e-8a07-363598f0e0c8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688050(v=OCS.15)
ms:contentKeyID: 49733643
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deleting network bandwidth policy profiles in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Use the following procedures to delete a network bandwidth policy profiles. For details on creating or modifying a network bandwidth policy profile, see [Creating or modifying bandwidth policy profiles in Lync Server 2013](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md).

<div>

## To delete a bandwidth policy profile

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Bandwidth Policy**.

4.  On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to delete.
    
    <div>
    

    > [!NOTE]  
    > You can delete more than one profile at a time. To do this, press CTRL and select multiple profiles while holding down the CTRL key. Or, to select all profiles, click <STRONG>Select all</STRONG> on the <STRONG>Edit</STRONG> menu.

    
    </div>

5.  On the **Edit** menu, click **Delete**.
    
    <div>
    

    > [!WARNING]  
    > You cannot delete a bandwidth policy profile that is associated with a network site. You must first remove the association with the network site before you can delete the profile. For details about how to modify the network site, see <A href="lync-server-2013-creating-or-modifying-network-sites.md">Creating or modifying network sites in Lync Server 2013</A>.

    
    </div>

</div>

<div>

## See Also


[Creating or modifying bandwidth policy profiles in Lync Server 2013](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)  
[Viewing network bandwidth policy profile information in Lync Server 2013](lync-server-2013-viewing-network-bandwidth-policy-profile-information.md)  


[Configure call admission control in Lync Server 2013](lync-server-2013-configure-call-admission-control.md)  
[Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkBandwidthPolicyProfile)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

