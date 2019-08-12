---
title: 'Lync Server 2013: Enable or disable federation and public IM connectivity'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enable or disable federation and public IM connectivity
ms:assetid: 8ec58f4b-9f6d-47b4-a187-d18a83fe4577
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182549(v=OCS.15)
ms:contentKeyID: 48184813
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable or disable federation and public IM connectivity in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-06-24_

Support for federation is required to enable users who have an account with a trusted customer or partner organization, including partner domains and users of public instant messaging (IM) provider users that you support, to collaborate with users in your organization. Federation is also required to use a hosted Exchange service provider to provide voice mail to Enterprise Voice users whose mailboxes are located on a hosted Exchange service such as Microsoft Exchange Online. When you have established a trust relationship with these external domains, you can authorize users in those domains to access your deployment and participate in Lync Server communications. This trust relationship is called a federation and it is not related to, or dependent upon, an Active Directory trust relationship.

To support access by users of federated domains, you must enable federation. If you enable federation for your organization, you must also specify whether to implement the following options:

  - **Enable partner domain discovery**   If you enable this option, Lync Server uses Domain Name System (DNS) records to try to discover domains not listed in the allowed domains list, automatically evaluating incoming traffic from discovered federated partners and limiting or blocking that traffic based on trust level, amount of traffic, and administrator settings. If you do not select this option, federated user access is enabled only for users in the domains that you include on the allowed domains list. Whether or not you select this option, you can specify that individual domains to be blocked or allowed, including restricting access to specific servers running the Access Edge service in the federated domain. For details about controlling access by federated domains, see [Configure support for allowed external domains in Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md).

  - **Send an archiving disclaimer to federated partners**    Disclaimer notice is sent to federated partners that archiving in your deployment is in place. If you support archiving of external communications with federated partner domains, you should enable the archiving disclaimer notification to warn partners that their messages are being archived.

If you later want to temporarily or permanently prevent access by users of federated domains, you can disable federation for your organization. Use the procedure in this section to enable or disable federated user access for your organization, including specifying the appropriate federation options to be supported for your organization.

<div>


> [!NOTE]  
> Enabling federation for your organization only specifies that your servers running the Access Edge service support routing to federated domains. Users in federated domains cannot participate in IM or conferences in your organization until you also configure at least one policy to support federated user access. Users of public IM service providers cannot participate in IM or conferences in your organization until you also configure at least one policy to support public IM connectivity. Lync Server cannot use a hosted Exchange service to provide call answering, Outlook Voice Access (including voice mail), or auto-attendant services for users whose mailboxes are located on a hosted Exchange service until you configure a hosted voice mail policy that provides routing information. For details about configuring policies for communication with users of federated domains in other organizations, see <A href="lync-server-2013-manage-sip-federated-domains-for-your-organization.md">Manage SIP federated domains for your organization in Lync Server 2013</A> in the Operations documentation. Additionally, if you want to support communication with users of IM service providers, you must configure policies to support it and also configure support for the individual service providers that you want to support. For details, see <A href="lync-server-2013-manage-sip-federated-providers-for-your-organization.md">Manage SIP federated providers for your organization in Lync Server 2013</A> in the Operations documentation. For details about creating a hosted voice mail policy, see <A href="lync-server-2013-manage-hosted-voice-mail-policies.md">Manage hosted voice mail policies in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## To enable or disable federated user access for your organization

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **External User Access**, and then click **Access Edge Configuration**.

4.  On the **Access Edge Configuration** page, click **Global**, click **Edit**, and then click **Show details**.

5.  In **Edit Access Edge Configuration**, do one of the following:
    
      - To enable federated user access for your organization, select the **Enable communications with federated users** check box.
    
      - To disable federated user access for your organization, clear the **Enable communications with federated users** check box.

6.  If you selected the **Enable communications with federated users** check box, do the following:
    
    1.  If you want to support automatic discovery of partner domains, select the **Enable partner domain discovery** check box.
    
    2.  If your organization supports archiving of external communications, select the **Send archiving disclaimer to federated partners** check box.

7.  Click **Commit**.

To enable federated users to collaborate with users in your Lync Server 2013 deployment, you must also configure at least one external access policy to support federated user access. For details, see [Configure policies to control federated user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md) in the Deployment documentation or the Operations documentation. To control access for specific federated domains, see [Configure support for allowed external domains in Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md) in the Deployment documentation or Operations documentation.

</div>

<div>

## Enabling or Disabling Federation and Public IM Connectivity by Using Windows PowerShell Cmdlets

Federation and public IM connectivity can also be managed by using Windows PowerShell and the Set-CsAccessEdgeConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To enable federation and public IM connectivity

  - To enable federation and public IM connectivity, set the value of the **AllowFederatedUsers** property to True ($True):
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

</div>

<div>

## To disable federation and public IM connectivity

  - To disable federation and public IM connectivity, set the value of the **AllowFederatedUsers** property to False ($False):
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $False

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

