---
title: "Configure partner applications in Skype for Business Server 2015 and Exchange Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 12/20/2018
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 9c3a3054-6201-433f-b128-4c49d3341370
description: "Summary: Configure server to server authentication for Exchange Server 2016 or Exchange Server 2013 and Skype for Business Server."
---

# Configure partner applications in Skype for Business Server and Exchange Server
 
**Summary:** Configure server to server authentication for Exchange Server 2016 or Exchange Server 2013 and Skype for Business Server.
  
Server-to-server authentication usually requires two servers that need to communicate with one another and a third-party security token server. If Server A and Server B need to communicate, then both of those servers typically start by contacting a token server and obtaining a mutually-trusted security token. Server A then presents that security token to Server B (and vice-versa) as a way to guarantee its authenticity and trustworthiness.
  
However, that's a general rule. Skype for Business Server, Exchange Server 2016, Exchange Server 2013, and SharePoint Server 2013 do not need to use a third-party token server when communicating with one another; that's because these server products can create security tokens that can be accepted by one another without the need for a separate token server. (This capability is only available in Skype for Business Server, Exchange Server 2016, Exchange Server 2013, and SharePoint Server 2013. If you need to set up server-to-server authentication with other servers, including other Microsoft server products, then you will need to do so by using a third-party token server.)
  
In order to set up server-to-server authentication between Skype for Business Server and Exchange Server you must do two things: 1) you must assign the appropriate certificates to each server; and, 2) you must configure each server to be a partner application of the other server: that means you must configure Skype for Business Server to be a partner application for Exchange Server, and you must configure Exchange Server to be a partner application for Skype for Business Server.
  
## Configuring Skype for Business Server to be a Partner Application for Exchange Server

The easiest way to configure Skype for Business Server to be a partner application with Exchange Server 2016 or Exchange Server 2013 is to run the Configure-EnterprisePartnerApplication.ps1 script, a Windows PowerShell script that ships with Exchange Server. To run this script, you must provide the URL for the Skype for Business Server authentication metadata document; this will typically be the fully qualified domain name of the Skype for Business Server pool followed by the suffix /metadata/json/1. For example:
  
```
https://atl-cs-001.litwareinc.com/metadata/json/1
```

To configure Skype for Business Server as a partner application, open the Exchange Management Shell and run a command similar to this (assuming that Exchange has been installed on drive C: and that it uses the default folder path):
  
```
"C:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl 'https://atl-cs-001.litwareinc.com/metadata/json/1' -ApplicationType Lync"
```

After configuring the partner application it is recommended that you stop and restart Internet Information Services (IIS) on your Exchange mailbox and client access servers. You can restart IIS by using a command similar to this, which restarts the service on the computer atl-exchange-001:
  
```
iisreset atl-exchange-001
```

This command can be run from within the Exchange Management Shell or from any other command window run under administrator privileges.
  
## Configuring Exchange Server to be a Partner Application for Skype for Business Server

After you have configured Skype for Business Server to be a partner application for Exchange Server 2016 or Exchange Server 2013, you must then configure Exchange Server to be a partner application for Skype for Business Server. This can be done by using the Skype for Business Server Management Shell and specifying the authentication metadata document for Exchange; this will typically be the URI of the Exchange autodiscover service followed by the suffix /metadata/json/1. For example:
  
```
https://autodiscover.litwareinc.com/autodiscover/metadata/json/1
```

In Skype for Business Server, partner applications are configured by using the [New-CsPartnerApplication](https://docs.microsoft.com/powershell/module/skype/new-cspartnerapplication?view=skype-ps) cmdlet. In addition to specifying the metadata URI you should also set the application trust level to Full; this will allow Exchange to represent both itself and any authorized user in the realm. For example:
  
```
New-CsPartnerApplication -Identity Exchange -ApplicationTrustLevel Full -MetadataUrl "https://autodiscover.litwareinc.com/autodiscover/metadata/json/1"
```

Alternatively, you can create a partner application by copying and modifying the script code found in the Skype for Business Server server-to-server authentication documentation. See the [Manage server-to-server authentication (OAuth) and partner applications in Skype for Business Server](../../manage/authentication/server-to-server-and-partner-applications.md) article for more information.
  
If you have successfully configured partner applications for both Skype for Business Server and Exchange Server, you have also successfully configured server-to-server authentication between the two products. Skype for Business Server includes a Windows PowerShell cmdlet, [Test-CsExStorageConnectivity](https://docs.microsoft.com/powershell/module/skype/test-csexstorageconnectivity?view=skype-ps) which enables you to verify that server-to-server authentication has been correctly configured and that the Skype for Business Server Storage Service can connect to Exchange Server. The cmdlet does this by connecting to the mailbox of an Exchange Server user, writing an item into the Conversation History folder for that user, and then (optionally) deleting that item.
  
To test the integration of Skype for Business Server and Exchange Server, run a command similar to the following from the Skype for Business Server Management Shell:
  
```
Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com"
```

In the preceding command, the SipUri represents the SIP address of a user with an account on Exchange Server; your command will fail in this is not a valid user account.
  
> [!NOTE]
> If you receive a 401 response from this cmdlet, it is probably because the default configuration for Exchange does not include support for accepting Oauth tokens. For more information about using Oauth in Exchange, see [Configure OAuth authentication with SharePoint 2013 and Skype for Business Server](https://go.microsoft.com/fwlink/p/?LinkId=513103). 
  
If the test succeeds and connectivity has been established, you can then proceed to configure optional features such as archiving integration and the unified contact store.
