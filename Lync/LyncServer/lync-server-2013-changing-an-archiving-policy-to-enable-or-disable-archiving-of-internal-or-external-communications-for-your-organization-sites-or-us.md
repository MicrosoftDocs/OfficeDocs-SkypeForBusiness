---
title: 'Lync Server 2013: Changing an Archiving policy to enable or disable Archiving of internal or external communications for your organization, sites, or users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Changing an Archiving policy to enable or disable Archiving of internal or external communications for your organization, sites, or users
ms:assetid: b85dc3fb-8ebd-4e3c-ac90-fc79270ac867
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182576(v=OCS.15)
ms:contentKeyID: 48185234
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Changing an Archiving policy in Lync Server 2013 to enable or disable Archiving of internal or external communications for your organization, sites, or users

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

In Lync Server 2013, you use policies to enable and disable archiving for internal communications and external communications for users homed on Lync Server 2013. This includes the following Archiving policies:

  - A global policy that is created by default when you deploy Lync Server 2013.

  - Optional site-level and user-level policies that you can create and use to specify how archiving is implemented for specific sites or users.

You initially set up Archiving policies when you deploy Archiving, but you can change, add, and delete policies after deployment. In Lync Server 2013 Control Panel, you can use the **Archiving Policy** page of the **Archiving and Monitoring** group to manage policies at the global level, site level, and user level. If you integrate your Lync Server storage with Exchange 2013 storage, the Exchange user policies take precedence over the Lync Server 2013 archiving policies.

For details about how policies are implemented, including the hierarchy of policies, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> If you enabled Microsoft Exchange integration for your deployment, Exchange policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration</A> in the Deployment documentation.<BR>You should specify all appropriate options in the Archiving configurations before enabling Archiving. For details, see <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools</A> in the Operations documentation.



</div>

<div>

## To change an archiving policy

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.

4.  In the list of policies, do one of the following:
    
      - To change the policy for your entire deployment, click **Global** in the list of policies, click **Edit**, and then click **Show details**.
    
      - To change the policy for a single site, click the site name in the list of policies, click **Edit**, and then click **Show details**.
    
      - To change the policy for a single user or user group, click the user or user group name in the list of policies, click **Edit**, and then click **Show details**.

5.  On the **Edit Archiving Policy** page, do the following:
    
      - To enable or disable internal archiving for the policy, select or clear the **Archive internal communications** check box.
    
      - To enable or disable external archiving for the policy, select or clear the **Archive external communications** check box.

6.  Click **Commit**.
    
    <div>
    

    > [!IMPORTANT]  
    > The settings of a user policy only apply to the specific users and user groups to which you apply the policy. For details, see <A href="lync-server-2013-applying-an-archiving-policy-to-users.md">Applying an Archiving policy to users in Lync Server 2013</A>

    
    </div>

</div>

<div>

## Enabling and Disabling Archiving by Using Windows PowerShell Cmdlets

Archiving can be enabled and disabled (for both internal and external communication sessions) by using the **Set-CsArchivingPolicy** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To enable the archiving of internal communication sessions

  - To enable archiving of internal communication sessions, set the value of the **ArchiveInternal** property to True ($True). For example:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True

</div>

<div>

## To enable the archiving of external communication sessions

  - To enable archiving of external communication sessions, set the value of the **ArchiveExternal** property to True ($True). For example:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveExternal $True

</div>

<div>

## To enable the archiving of both internal and external communication sessions

  - To enable archiving of both internal and external communications sessions, set both the **ArchiveInternal** and the **ArchiveExternal** properties to True:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True

</div>

<div>

## To disable archiving

  - To disable archiving altogether, set both the **ArchiveInternal** and **ArchiveExternal** properties to False ($False). For example:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $False -ArchiveExternal $False

</div>

For more information, see the help topic for the [Set-CsArchivingPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsArchivingPolicy) cmdlet.

</div>

<div>

## See Also


[Managing the Archiving of internal and external communications in Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

