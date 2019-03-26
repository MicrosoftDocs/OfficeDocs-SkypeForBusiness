---
title: 'Lync Server 2013: Manage external access policy for your organization'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Manage external access policy for your organization
ms:assetid: 5571811e-34c8-443a-b94c-1ab5d4275581
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520995(v=OCS.15)
ms:contentKeyID: 48184160
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Manage external access policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

After deploying one or more Edge Servers, you must enable the types of external access that will be supported for your organization.

By default, there are no policies configured to support external user access, including remote user access, federated user access, even if you have already enabled external user access support for your organization. To control the use of external user access, you must configure one or more policies, specifying the type of external user access supported for each policy. The following policy scopes are available for creation and configuration. By default, the Global policy is created, but cannot be deleted.

  - **Global policy**   The global policy is created when you deploy your Edge Servers. By default, no external user access options are enabled in the global policy. To support external user access at the global level, you configure the global policy to support one or more types of external user access options. The global policy applies to all users in your organization, but site policies and user policies override the global policy. If you delete the global policy, you do not remove it. Instead, you reset it to the default setting.

  - **Site policy**   You can create and configure one or more site policies to limit support for external user access to specific sites. The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy. For example, if you enable remote user access in the global policy, you might specify a site policy that disables remote user access for a specific site. By default, a site policy is applied to all users of that site, but you can assign a user policy to a user to override the site policy setting.

  - **User policy**   You can create and configure one or more user policies to limit support for remote user access to specific users. The configuration in the user policy overrides the global and site policy, but only for the specific users to whom the user policy is assigned. For example, if you enable remote user access in the global policy and site policy, you might specify a user policy that disables remote user access and then assign that user policy to specific users. If you create a user policy, you must apply it to one or more users before it takes effect.

<div>


> [!IMPORTANT]  
> Lync Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Lync Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.



</div>

These options include the following types of external access:

  - **Enable communications with federated users**   Enable this if you want to support user access to federated partner domains. This setting configures the ability for users to communicate with other SIP federated domains, as well as Hosted providers like Microsoft Office 365. Selecting this setting allows you to select the option to allow communication with XMPP federated domains.
    
    As an option, you can select **Enable communications with XMPP federated partners** if you first select **Enable communications with federated users**. XMPP federation is a federation with organizations that use extensible messaging and presence protocol (XMPP).
    
    <div>
    

    > [!NOTE]  
    > If you enable XMPP federation, you must also select to deploy <STRONG>XMPP federation</STRONG> in the Edge pools configuration section of Topology Builder. Configuring for XMPP federation deploys an XMPP Proxy on the Edge Server and an XMPP gateway on the Front End Server.

    
    </div>

  - **Enable communications with remote users**   Enable this option if you want users in your organization who are outside your firewall, such as telecommuters and users who are traveling, to be able to connect to Lync Server over the Internet.

  - **Enable communications with public users**   Enable this option if you want internal users to be able to communicate with public IM provider contacts, such as those provided by Windows Live, Yahoo\!, and America Online (AOL).
    
    <div>
    

    > [!IMPORTANT]  
    > <UL>
    > <LI>
    > <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
    > <LI>
    > <P>The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.</P>
    > <LI>
    > <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.</P></LI></UL>

    
    </div>

<div>


> [!NOTE]  
> In addition to enabling external user access support, you must also configure policies to control the use of external user access in your organization before any type of external user access is available to users. For details about creating, configuring, and applying policies for external user access see <A href="lync-server-2013-enable-or-disable-remote-user-access.md">Enable or disable remote user access in Lync Server 2013</A>.



</div>

**To view external access policies by using Windows PowerShell cmdlets**

  - You can view external access policies by using Lync Server Management Shell and the **Get-CsExternalAccessPolicy** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    To view information about all your external access policies, type the following command in the Lync Server Management Shell and then press ENTER:
    
        Get-CsExternalAccessPolicy
    
    This command returns information similar to the following:
    
        Identity                          : Global
        Description                       :
        EnableFederationAccess            : False
        EnableXmppAccess                  : False
        EnablePublicCloudAccess           : False
        EnablePublicCloudAudioVideoAccess : False
        EnableOutsideAccess               : False

<div>

## In This Section

  - [Configure policies to control federated user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md)

  - [Configure policies to control XMPP federated user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md)

  - [Configure policies to control remote user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-remote-user-access.md)

  - [Configure policies to control public user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)

  - [Assign an external user access policy to a Lync enabled user in Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)

  - [Resetting or deleting external user access policies in Lync Server 2013](lync-server-2013-resetting-or-deleting-external-user-access-policies.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

