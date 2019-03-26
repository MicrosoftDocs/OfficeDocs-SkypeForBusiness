---
title: 'Lync Server 2013: Create or edit public SIP federated providers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or edit public SIP federated providers
ms:assetid: 5321598c-1ab1-40e3-b739-4b2e6d0a3a3b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398349(v=OCS.15)
ms:contentKeyID: 48184167
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or edit public SIP federated providers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Public instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by public IM service providers, including the Windows Live Messenger, Yahoo\!, and AOL.

Lync Server 2013 has public provider configurations for America Online, Windows Live and Yahoo\! instant messaging. Each public provider is configured with the provider’s Edge server fully qualified domain name, and the default verification level **Allow users to communicate only with people on their Contacts list who use this provider**.

As a default setting, none of the public providers are enabled. You should complete license agreement and provisioning work before enabling the public providers. You can enable the provider before completing the licensing and provisioning work. Users will not be able to communicate with contacts on those providers until the pre-requisite work is completed. For details on licensing and provisioning of public providers, see [Configure policies to control public user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md).

Use the following procedure to create or edit Public providers:

<div>

## To create or edit public providers

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Federation and External Access**, and then click **SIP Federated Providers**.

4.  If you need to create a new Public provider, click **New** and then click **Public provider**.

5.  If you need to edit an entry from the list of Public providers, select a public provider, click **Edit**, then click **Show details**.

6.  On the **Edit SIP Federated Provider** page, you can type or edit the following settings:
    
      - **Enable communications with this provider**   Selecting this setting enables IM with this provider’s users.
    
      - **Provider name:**   A required property, type the name of the provider as it will be reflected in the listing of SIP Federated Providers.
    
      - **Access Edge service (FQDN):**   A required property, type the fully qualified domain name of the Access Edge service of the provider that you are configuring. This information is provided as a default item, and should only be changed if the public provider makes a change to the FQDN of the Access Edge service at the public provider.
    
      - **Default verification level:**   The default setting, **Allow users to communicate with people on their Contacts list who use this provider** will limit communication to contacts that you have accepted and are in your contact list.
        
        Selecting **Allow users to communicate with everyone using this provider** removes the restriction that you must have received and accepted a contact invite. This setting does not limit who can contact you from the public provider’s network.

7.  When you are done configuring the settings, click **Commit** to save, or click **Cancel** to discard your changes.

</div>

<div>

## See Also


[Configure policies to control public user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)  
[Enable or disable federation and public IM connectivity in Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

