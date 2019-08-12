---
title: 'Configuring on-premises Lync Server integration with Exchange Online'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring on-premises Lync Server integration with Exchange Online
ms:assetid: 95a20117-2064-43c4-94fe-cac892cadb6f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh533880(v=OCS.15)
ms:contentKeyID: 48184900
ms.date: 03/30/2018
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring on-premises Lync Server 2013 integration with Exchange Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2018-03-30_

Customers who are using on-premises Lync Server 2013 deployments can configure interoperability with Microsoft Outlook Web App in Microsoft Exchange Online in a hybrid deployment mode. Interoperability features include single sign on and instant messaging (IM) and presence integration with the Outlook Web App interface. To enable this integration, you must configure the Edge Server in your on-premises Lync Server deployment by completing the following tasks:

  - Configure a shared SIP address space

  - Configure a hosting provider on the Edge Server

  - Verify replication of the updated Central Management store

If Lync Server 2013 is integrated with Exchange Online, a user who is trying to sign in to IM from OWA is considered a remote or external user. In this scenario, this user must have an external access policy assigned that has the following option selected:

**Enable communications with remote users**

Enable this option if you want users in your organization who are outside your firewall, such as telecommuters and users who are traveling, to be able to connect to Lync Server over the Internet.

For more information, see [Manage external access policy in Lync Server 2013](lync-server-2013-manage-external-access-policy-for-your-organization.md).

<div>

## Configure a Shared SIP Address Space

To integrate on-premises Lync Server 2013 with Exchange Online, you must configure a shared SIP address space. The same SIP domain address space is supported by both Lync Server and the Exchange Online service.

Using the Lync Server Management Shell, configure the Edge Server for federation by running the **Set-CSAccessEdgeConfiguration** cmdlet, using the parameters that are displayed in the following example:

    Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

  - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a shared SIP address space scenario with Lync Server and Exchange Online.

For details about how to use the Lync Server Management Shell, see [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md).

</div>

<div>

## Configure a Hosting Provider on the Edge Server

Use the Lync Server Management Shell to configure a hosting provider on the Edge Server. To do this, run the **New-CsHostingProvider** cmdlet, using the parameters in the following example:

    New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification

<div>


> [!NOTE]
> If you are using Office 365 operated by 21Vianet in China, replace the value for the <STRONG>ProxyFqdn</STRONG> parameter in this example ("exap.um.outlook.com") with the FQDN for the service operated by 21Vianet: "exap.um.partner.outlook.cn".



</div>

  - **Identity** specifies a unique string value identifier for the hosting provider that you are creating (for example, "Exchange Online"). Values that contain spaces must be in double quotation marks.

  - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. This must be set to **True**.

  - **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. This must be set to **True**.

  - **HostsOCSUsers** indicates whether the hosting provider is used to host Office Communications Server or Lync Server. This must be set to **False**.

  - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider. For Exchange Online, the FQDN is exap.um.outlook.com.

  - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Lync Server topology. This must be set to **False**.

  - **VerificationLevel** indicates the verification level allowed for messages that are sent to and from the hosted provider. Specify **UseSourceVerification**. This option relies on the verification level that is included in messages that are sent from the hosting provider. If this level is not specified, the message will be rejected as being unverifiable.

</div>

<div>

## Verify Replication of the Updated Central Management Store

The changes that you made by using the cmdlets in the preceding sections are automatically applied to the Edge Server, and generally take less than one minute to replicate. You can verify the replication status and that the changes were applied to your Edge Server by using the following cmdlets.

To verify replication updates on a server internal in your Lync Server deployment, run the following cmdlet:

    Get-CsManagementStoreReplicationStatus

To verify that the changes were applied, run the following cmdlet on the Edge Server:

    Get-CsHostingProvider -LocalStore

</div>

<div>

## See Also


[Providing Lync Server 2013 users voice mail on hosted Exchange UM](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md)  
[Hosted Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

