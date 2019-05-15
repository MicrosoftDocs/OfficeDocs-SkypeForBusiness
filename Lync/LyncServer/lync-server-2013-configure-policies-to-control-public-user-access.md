---
title: 'Lync Server 2013: Configure policies to control public user access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure policies to control public user access
ms:assetid: 090aea0f-ef0b-49da-9c80-02d9279f2fa6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520946(v=OCS.15)
ms:contentKeyID: 48183343
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure policies to control public user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

Public instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by public IM service providers, including the Windows Live network of Internet services, Yahoo\!, and AOL. You configure one or more external user access policies to control whether public users can collaborate with internal Lync Server users. Public instant messaging connectivity is an added feature that relies on configuration of your deployment and users. It also depends on the provisioning of the service at the public IM provider. For information on how to provision your deployment to use the public providers, see the “Public IM Connectivity Provisioning Guide for Microsoft Lync Server, Office Communications Server, and Live Communications Server” guide: [http://go.microsoft.com/fwlink/?LinkId=269821](http://go.microsoft.com/fwlink/?linkid=269821)

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

To access the Microsoft Lync Server Public IM Connectivity Provisioning site, use the following link: [http://go.microsoft.com/fwlink/p/?linkId=212638](http://go.microsoft.com/fwlink/p/?linkid=212638)

To control public user access, you can configure policies at the global, site, and user level. For details about the types of policies that you can configure, see [Configuring support for external user access in Lync Server 2013](lync-server-2013-configuring-support-for-external-user-access.md) in the Deployment documentation or the Planning documentation. Lync Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Lync Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.

In the case of IM invitations, the response depends on the client software. The request is accepted unless external senders are explicitly blocked by a user-configured rule (that is, the settings in the user’s client **Allow** and **Block** lists). Additionally, IM invitations can be blocked if a user elects to block all IM from users who are not on his or her **Allow** list.

<div>


> [!NOTE]  
> You can configure policies to control public user access, even if you have not enabled federation for your organization. However, the policies that you configure are in effect only when you have federation enabled for your organization. For details about enabling federation, see <A href="lync-server-2013-enable-or-disable-remote-user-access.md">Enable or disable remote user access in Lync Server 2013</A> in the Deployment documentation or the Operations documentation. Additionally, if you specify a user policy to control public user access, the policy applies only to users that are enabled for Lync Server and configured to use the policy. For details about specifying public users that can sign in to Lync Server, see <A href="lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md">Assign an external user access policy to a Lync enabled user in Lync Server 2013</A> in the Deployment documentation or the Operations documentation.



</div>

Use the following procedure to configure a policy to support access by users of one or more public IM providers.

<div>

## To configure an external access policy to support public user access

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **External User Access**, and then click **External Access Policy**.

4.  On the **External Access Policy** page, do one of the following:
    
      - To configure the global policy to support public user access, click the global policy, click **Edit**, and then click **Show details**.
    
      - To create a new site policy, click **New**, and then click **Site policy**. In **Select a Site**, click the appropriate site from the list and then click **OK**.
    
      - To create a new user policy, click **New**, and then click **User policy**. In **New External Access Policy**, create a unique name in the **Name** field that indicates what the user policy covers (for example, **EnablePublicUsers** for a user policy that enables communications for public users).
    
      - To change an existing policy, click the appropriate policy listed in the table, click **Edit**, and then click **Show details**.

5.  (Optional) If you want to add or edit a description, specify the information for the policy in **Description**.

6.  Do one of the following:
    
      - To enable public user access for the policy, select the **Enable communications with public users** check box.
    
      - To disable public user access for the policy, clear the **Enable communications with public users** check box.

7.  Click **Commit**.

To enable public user access, you must also enable support for federation in your organization. For details, see [Configure policies to control federated user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md).

If this is a user policy, you must also apply the policy to public users that you want to be able to collaborate with public users. For details, see [Assigning per-user policies in Lync Server 2013](lync-server-2013-assigning-per-user-policies.md).

</div>

<div>

## See Also


[Create or edit public SIP federated providers in Lync Server 2013](lync-server-2013-create-or-edit-public-sip-federated-providers.md)  


[Manage SIP federated providers for your organization in Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

