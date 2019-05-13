---
title: 'Lync Server 2013: Configure policies to control XMPP federated user access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure policies to control XMPP federated user access
ms:assetid: 0fe0ff75-e52a-4e3e-923a-64f6412ac4e4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ552446(v=OCS.15)
ms:contentKeyID: 48679557
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure policies to control XMPP federated user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

This is preliminary documentation and is subject to change. Blank topics are included as placeholders.

When you configure policies for support of extensible messaging and presence protocol (XMPP) federated partners, the policies apply to users of XMPP federated domains, but not to users of session initiation protocol (SIP) instant messaging (IM) service providers (for example, Windows Live), or SIP federated domains. You configure an **XMPP Federated Partner** for each XMPP federated domain that you want to allow your users to add contacts and communicate with. XMPP federated partners policies are only available in a single scope, though it is not defined as a global policy, acts as a global policy. To define a global, site or user policy for XMPP Federation Partners, you configure the policy scope by first creating and configuring the External Access Policy for the scope you require. For details about the types of policies that you can configure for external access and federation, see [Managing federation and external access to Lync Server 2013](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md) in the Operations documentation.

<div>


> [!NOTE]  
> All <STRONG>Federation and External Access</STRONG> policies are applied through in-band provisioning. The policies that apply to the user, belong to a site, or are global in scope are communicated to the client during login. You can configure policies to control XMPP federated partner access, even if you have not enabled XMPP federation for your organization. However, the policies that you configure take effect only when you have XMPP partner federation deployed, enabled and configured for your organization. For details about deploying and configuring XMPP partner federation, see <A href="lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md">Configuring SIP federation, XMPP federation and public instant messaging in Lync Server 2013</A> in the Deployment documentation. Additionally, if you specify a user policy in External Access Policy to control XMPP federated partners, the policy applies only to users that are enabled for Lync Server 2013 and configured to use the policy.



</div>

<div>

## To edit a global policy for XMPP federated partners

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **External User Access**, and then click **External Access Policy**.

4.  On the **External Access Policy** page, do the following for the global policy:

5.  Click the global policy, click **Edit**, and then click Show details.

6.  Provide a description for the Global policy (optional).

7.  Select **Enable communications with federated users**.

8.  Select **Enable communications with XMPP federated users**.

9.  Click **Commit** to save your changes to the Global policy.

</div>

<div>

## To create a site or user policy for XMPP federated partners

1.  Click **New**, and then click **Site policy** or **User policy**. In **Select a Site**, click the appropriate site from the list and then click **OK**.

2.  Provide a description for the Site policy (optional).

3.  In the site or user policy, select **Enable communications with federated users**.

4.  Select **Enable communications with XMPP federated users**.

5.  Click **Commit** to save your changes to the site or user policy.

</div>

<div>

## To edit an existing policy for XMPP federated partners

1.  To change an existing policy, select the appropriate policy in the list, click **Edit**, and then click **Show details**.

2.  Change or update the description for the policy (optional).

3.  Select or unselect **Enable communications with federated users**.

4.  Select or unselect **Enable communications with XMPP federated users**.

5.  Click **Commit** to save your changes to the policy.

</div>

<div>

## To edit an existing policy for XMPP federated partners by using Windows PowerShell

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Type the following in the Lync Server Management Shell:
    
        Set-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false>
    
    An example command that will set the global policy for Federated user access to True (enabled) and XMPP domain access to True (enabled):
    
        Set-CsExternalAccessPolicy -Identity global -EnableFederationAccess $true -EnableXmppAccess $true

</div>

<div>

## To create a site or user policy for XMPP federated partners using Windows PowerShell

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Type the following in the Lync Server Management Shell:
    
        New-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false>
    
    An example command that will set a site policy for the Redmond site for Federated user access to enabled and XMPP domain access to enabled:
    
        New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $true -EnableXmppAccess $true

</div>

<div>

## To delete an existing policy for XMPP federated partners by using Windows PowerShell

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Type the following in the Lync Server Management Shell:
    
        Remove-CsExternalAccessPolicy -Identity <name of global, site or user policy>
    
    An example command that will delete a user policy:
    
        Remove-CsExternalAccessPolicy -Identity EAPUserPolicySetXMPP

4.  An example command that will reset the global policy to defaults:
    
        Remove-CsExternalAccessPolicy -Identity global

</div>

<div>

## See Also


[Assign an external user access policy to a Lync enabled user in Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)  
[Enable or disable federation and public IM connectivity in Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)  


[Manage XMPP federated partners in Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
[Set-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsExternalAccessPolicy)  
[New-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/New-CsExternalAccessPolicy)  
[Get-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Get-CsExternalAccessPolicy)  
[Remove-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsExternalAccessPolicy)  
[Grant-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Grant-CsExternalAccessPolicy)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

