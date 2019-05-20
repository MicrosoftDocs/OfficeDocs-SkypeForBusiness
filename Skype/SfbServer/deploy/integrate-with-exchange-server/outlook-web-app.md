---
title: "Configure integration between on-premises Skype for Business Server and Outlook Web App"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/7/2016
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 95a20117-2064-43c4-94fe-cac892cadb6f
description: "Summary: Integrate Skype for Business Server and Outlook Web App."
---

# Configure integration between on-premises Skype for Business Server and Outlook Web App

**Summary:** Integrate Skype for Business Server and Outlook Web App.

Customers who are using on-premises Skype for Business Server deployments can configure interoperability with Microsoft Outlook Web App in Microsoft Exchange Online in a hybrid deployment mode. Interoperability features include single sign on and instant messaging (IM) and presence integration with the Outlook Web App interface. To enable this integration, you must configure the Edge Server in your on-premises Skype for Business Server deployment by completing the following tasks:

- Configure a shared SIP address space

- Configure a hosting provider on the Edge Server

- Verify replication of the updated Central Management store

## Configure a Shared SIP Address Space

To integrate on-premises Skype for Business Server with Exchange Online, you must configure a shared SIP address space. The same SIP domain address space is supported by both Skype for Business Server and the Exchange Online service.

Using the Skype for Business Server Management Shell, configure the Edge Server for federation by running the **Set-CSAccessEdgeConfiguration** cmdlet, using the parameters displayed in the following example:

```
Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True
```

- **AllowFederatedUsers** parameter specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a shared SIP address space scenario with Skype for Business Server and Exchange Online.

For details about using the Skype for Business Server Management Shell, see [Skype for Business Server Management Shell](../../manage/management-shell.md).

## Configure a Hosting Provider on the Edge Server

Using the Skype for Business Server Management Shell, configure a hosting provider on the Edge Server by running the **New-CsHostingProvider** cmdlet, using the parameters in the following example:

```
New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification
```

> [!NOTE]
> If you are using Office 365 operated by 21Vianet in China, replace the value for the ProxyFqdn parameter in this example ("exap.um.outlook.com") with the FQDN for the service operated by 21Vianet: "exap.um.partner.outlook.cn". If you are using Office 365 GCC High, replace the value for the ProxyFqdn parameter in this example ("exap.um.outlook.com") with the FQDN for GCC High: “exap.um.office365.us”.

- **Identity** specifies a unique string value identifier for the hosting provider that you are creating (for example, "Exchange Online"). Values that contain spaces must be in double quotes.

- **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. This must be set to True.

- **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. This must be set to True.

- **HostsOCSUsers** indicates whether the hosting provider is used to host Office Communications Server or Skype for Business Server. This must be set to False.

- **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider. For Exchange Online, the FQDN is exap.um.outlook.com.

- **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server topology. This must be set to False.

- **VerificationLevel** Indicates the verification level allowed for messages that are sent to and from the hosted provider. Specify **UseSourceVerification**, which relies on the verification level included in messages sent from the hosting provider. If this level is not specified, the message will be rejected as being unverifiable.

## Verify Replication of the Updated Central Management Store

The changes you made by using the cmdlets in the preceding sections are automatically applied to the Edge Server, and generally take less than a minute to replicate. You can validate replication status, and then confirm that the changes were applied to your Edge Server by using the following cmdlets.

To verify replication updates, on a server internal in your Skype for Business Server deployment, run the following cmdlet:

```
Get-CsManagementStoreReplicationStatus
```
Check if UpToDate value is showing TRUE for all Replicas.

To confirm that the changes were applied, on the Edge Server, run the following cmdlet:

```
Get-CsHostingProvider -LocalStore
```
Double check if the information shown matches the changes committed in the previous steps.

## See also

[Providing Skype for Business Server users voice mail on hosted Exchange UM](https://technet.microsoft.com/library/306d3fb5-231b-4f0b-b8d8-0d9083b5ed77.aspx)

[Hosted Exchange Unified Messaging integration in Skype for Business Server](https://technet.microsoft.com/library/f4de0165-da3b-499e-98fc-28ddd0db02d5.aspx)
