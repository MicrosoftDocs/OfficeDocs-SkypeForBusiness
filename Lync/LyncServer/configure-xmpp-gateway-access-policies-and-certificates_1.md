---
title: Configure XMPP gateway access policies and certificates
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure XMPP gateway access policies and certificates
ms:assetid: cd91433e-6dfb-4553-8316-c1086b394221
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721885(v=OCS.15)
ms:contentKeyID: 49733819
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure XMPP gateway access policies and certificates

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-15_

XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol (XMPP). An XMPP configuration allows Lync users access to XMPP domain users by:

  - IM and Presence – person to person only

  - Creation of XMPP federated contacts in the Lync client

When you configure policies for support of extensible messaging and presence protocol (XMPP) federated partners, the policies apply to users of XMPP federated domains, but not to users of session initiation protocol (SIP) instant messaging (IM) service providers (for example, Windows Live), or SIP federated domains. You configure an XMPP Federated Partner for each XMPP federated domain that you want to allow your users to add contacts and communicate with. Once the policies are in place, you need to configure the XMPP Gateway certificates.

<div>


> [!NOTE]  
> To begin the XMPP Gateway migration, you need to deploy the Lync Server 2013 XMPP Gateway, and configure access policies to enable users for Lync Server 2013 XMPP Gateway. All users must be moved to the Lync Server 2013 deployment before you perform these steps. For details, see <A href="configure-xmpp-gateway-on-lync-server-2013_1.md">Configure XMPP gateway on Lync Server 2013</A>.



</div>

<div>

## Configure an External Access Policy to Enable Users for Lync Server 2013 XMPP Gateway

1.  Open Lync Server Control Panel.

2.  In the left navigation bar, click **Federation and External Access**, and then click **External Access Policy**.

3.  Click **New** and then click **User policy**.

4.  Enter a name for the external access user policy.

5.  Provide a description for external access user policy.

6.  Select **Enable communications with federated users**.

7.  Select **Enable communications with XMPP federated users**.

8.  Click **Commit** to save your changes to the site or user policy.

</div>

</div>

<span> </span>

</div>

</div>

</div>

