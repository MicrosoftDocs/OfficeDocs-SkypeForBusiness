---
title: 'Lync Server 2013: Enable or disable anonymous user access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable or disable anonymous user access
ms:assetid: f10c19e6-b6f9-4d26-9923-0165f36e4af8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619192(v=OCS.15)
ms:contentKeyID: 49733872
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable or disable anonymous user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Anonymous users are users who do not have a user account in your organization's Active Directory Domain Services or in a supported federated domain, but can be invited to participate remotely in an on-premises conference. By allowing anonymous participation in meetings you enable anonymous users (that is, users whose identity is verified through the meeting or conference key only) to join meetings. Allowing anonymous participation requires enabling it for your organization.

If you later want to temporarily or permanently prevent access by anonymous users, you can disable it for your organization. Use the procedure in this section to enable or disable anonymous user access for your organization.

<div>


> [!NOTE]  
> By enabling anonymous user access for your organization you are only specifying that your servers running the Access Edge service support access by anonymous users. Anonymous users cannot participate in any meetings in your organization until you also configure at least one conferencing policy and apply it to one or more users or user groups. The only users that can invite anonymous users to meetings are those users that are assigned a conferencing policy that is configured to support anonymous users. For details about configuring conferencing policies to support inviting anonymous users, see <A href="lync-server-2013-conferencing-policies.md">Conferencing policies in Lync Server 2013</A>.



</div>

<div>

## To enable or disable anonymous user access for your organization

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **External User Access**, and then click **Access Edge Configuration**.

4.  On the **Access Edge Configuration** page, click **Global**, click **Edit**, and then click **Show details**.

5.  In **Edit Access Edge Configuration**, do one of the following:
    
      - To enable anonymous user access for your organization, select the **Enable communications with anonymous users** check box.
    
      - To disable anonymous user access for your organization, clear the **Enable communications with anonymous users** check box.

6.  Click **Commit**.

</div>

<div>

## Enabling or Disabling Anonymous User Access by Using Windows PowerShell Cmdlets

You can manage anonymous user access by using Windows PowerShell and the **Set-CsAccessEdgeConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To enable anonymous user access

  - To enable anonymous user access, set the value of the **AllowAnonymousUsers** property to True ($True):
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $True

</div>

<div>

## To disable anonymous user access

  - To disable anonymous user access, set the value of the **AllowAnonymousUsers** property to False ($False):
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $False

</div>

</div>

<div>

## See Also


[Conferencing policy settings reference for Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

