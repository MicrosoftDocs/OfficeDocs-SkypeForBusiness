---
title: "Configuring on-premises Lync Server 2013 integration with Exchange Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 95a20117-2064-43c4-94fe-cac892cadb6f
description: "In this articleConfigure a Shared SIP Address SpaceConfigure a Hosting Provider on the Edge ServerVerify Replication of the Updated Central Management Store"
---

# Configuring on-premises Lync Server 2013 integration with Exchange Online
[]
 **In this article**
  
[Configure a Shared SIP Address Space](#sectionSection0)
  
[Configure a Hosting Provider on the Edge Server](#sectionSection1)
  
[Verify Replication of the Updated Central Management Store](#sectionSection2)
  
Customers who are using on-premises Lync Server 2013 deployments can configure interoperability with Microsoft Outlook Web App in Microsoft Exchange Online in a hybrid deployment mode. Interoperability features include single sign on and instant messaging (IM) and presence integration with the Outlook Web App interface. To enable this integration, you must configure the Edge Server in your on-premises Lync Server deployment by completing the following tasks: 
  
- Configure a shared SIP address space
    
- Configure a hosting provider on the Edge Server
    
- Verify replication of the updated Central Management store
    
## Configure a Shared SIP Address Space
<a name="sectionSection0"> </a>

To integrate on-premises Lync Server 2013 with Exchange Online, you must configure a shared SIP address space. The same SIP domain address space is supported by both Lync Server and the Exchange Online service.
  
Using the Lync Server Management Shell, configure the Edge Server for federation by running the **Set-CSAccessEdgeConfiguration** cmdlet, using the parameters displayed in the following example: 
  
```
Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True
```

- **AllowFederatedUsers** parameter specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a shared SIP address space scenario with Lync Server and Exchange Online. 
    
For details about using the Lync Server Management Shell, see [Lync Server 2013 Management Shell](lync-server-management-shell.md).
  
## Configure a Hosting Provider on the Edge Server
<a name="sectionSection1"> </a>

Using the Lync Server Management Shell, configure a hosting provider on the Edge Server by running the **New-CsHostingProvider** cmdlet, using the parameters in the following example: 
  
```
New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification
```

> [!NOTE]
> If you are using Office 365 operated by 21Vianet in China, replace the value for the **ProxyFqdn** parameter in this example ("exap.um.outlook.com") with the FQDN for the service operated by 21Vianet: "exap.um.partner.outlook.cn". 
  
- **Identity** specifies a unique string value identifier for the hosting provider that you are creating (for example, "Exchange Online"). Values that contain spaces must be in double quotes. 
    
- **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. This must be set to True. 
    
- **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. This must be set to True. 
    
- **HostsOCSUsers** indicates whether the hosting provider is used to host Office Communications Server or Lync Server. This must be set to False. 
    
- **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider. For Exchange Online, the FQDN is exap.um.outlook.com. 
    
- **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Lync Server topology. This must be set to False. 
    
- **VerificationLevel** Indicates the verification level allowed for messages that are sent to and from the hosted provider. Specify **UseSourceVerification**, which relies on the verification level included in messages sent from the hosting provider. If this level is not specified, the message will be rejected as being unverifiable.
    
## Verify Replication of the Updated Central Management Store
<a name="sectionSection2"> </a>

The changes you made by using the cmdlets in the preceding sections are automatically applied to the Edge Server, and generally take less than a minute to replicate. You can validate replication status, and then confirm that the changes were applied to your Edge Server by using the following cmdlets.
  
To verify replication updates, on a server internal in your Lync Server deployment, run the following cmdlet:
  
```
Get-CsManagementStoreReplicationStatus
```

To confirm that the changes were applied, on the Edge Server, run the following cmdlet:
  
```
Get-CsHostingProvider -LocalStore
```

## See also
<a name="sectionSection2"> </a>

#### 

[Providing Lync Server 2013 users voice mail on hosted Exchange UM](providing-lync-server-2013-users-voice-mail-on-hosted-exchange-um.md)
  
[Hosted Exchange Unified Messaging integration in Lync Server 2013](hosted-exchange-unified-messaging-integration.md)

