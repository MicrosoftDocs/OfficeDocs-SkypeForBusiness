---
title: 'Lync Server 2013: Creating an Archiving policy to enable or disable Archiving of Internal or external communications for specific sites or users'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Creating an Archiving policy to enable or disable Archiving of Internal or external communications for specific sites or users
ms:assetid: 5864793a-ba72-470c-bb5b-9fb41e968896
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398385(v=OCS.15)
ms:contentKeyID: 48184193
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Creating an Archiving policy in Lync Server 2013 to enable or disable Archiving of Internal or external communications for specific sites or users

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
> To control the implementation of Archiving, you must specify options in Archiving configurations, such as whether to archive IM or conferencing, the use of critical mode, and purging options. By default no options are enabled in the global Archiving configuration or any site or pool Archiving configuration. You should specify all appropriate options in the Archiving configurations before enabling Archiving for internal or external communications in the Archiving policies. For details, see <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools</A> in the Operations documentation.<BR>If you enabled Microsoft Exchange integration for your deployment, Exchange policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration</A> in the Deployment documentation.



</div>

<div>

## To create an archiving policy for a site or users

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.

4.  Click **New**, and then do one of the following:
    
      - To create a site-level archiving policy, click **Site policy** and then, in **Select a site**, click the site to which the policy is to be applied.
    
      - To create a user-level archiving policy, click **User policy**.

5.  In **New Archiving Policy**, do the following:
    
      - In **Name**, specify a name for the new policy (for example, externalContoso).
    
      - In **Description**, provide details about what the policy is (for example, External user archiving policy for Contoso).
    
      - To control archiving of communications with internal users, select or clear the **Archive internal communications** check box.
    
      - To control archiving of communications with external users, select or clear the **Archive external communications** check box.

6.  Click **Commit**.
    
    <div>
    

    > [!IMPORTANT]
    > The settings of a user policy only apply to the specific users and user groups to which you apply the policy. For details, see <A href="lync-server-2013-applying-an-archiving-policy-to-users.md">Applying an Archiving policy to users in Lync Server 2013</A>

    
    </div>

</div>

<div>

## Creating an Archiving Policy by Using Windows PowerShell Cmdlets

Archiving policies can be created by using Windows PowerShell and the **Remove-CsArchivingPolicy** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To create a new archiving policy at the site scope

  - This command creates a new archiving policy for the Redmond site:
    
        New-CsArchivingPolicy -Identity "site:Redmond"

</div>

<div>

## To create a new archiving policy at the per-user scope

  - To create a new archiving policy at the per-user scope, simply specify a unique Identity when creating the policy:
    
        New-CsArchivingPolicy -Identity "RedmondArchivingPolicy"

</div>

<div>

## To create a new archiving policy that enables archiving of internal communication sessions

  - Because no parameters (other than the mandatory Identity parameter) were specified in the preceding commands, the new policies will use the default values for all their properties. To create policies that use different property values, simply include the appropriate parameter and parameter value. For example, to create an archiving policy that permits archiving of internal instant messaging sessions use a command like this:
    
        New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True

</div>

<div>

## To create a new archiving policy that enables archiving of both internal and external communication sessions

  - Multiple property values can be modified by including multiple parameters. For example, this command configures the new policy to archiving both internal and external instant messaging sessions:
    
        New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True -ArchiveExternal $True

</div>

For more information, see the help topic for the [New-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg399032(v=OCS.15)) cmdlet.

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

