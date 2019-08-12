---
title: 'Lync Server 2013: Get-CsService for Address Book management'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Get-CsService for Address Book management
ms:assetid: 373b717d-5efa-4c36-a899-a23a5bd922b4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg429698(v=OCS.15)
ms:contentKeyID: 48183853
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsService for Address Book management in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Who can run this cmdlet: By default, members of the following groups are authorized to run the Get-CsService cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsService"}

Get-CsService is valuable to retrieve and display the current configuration of your infrastructure’s defined Web Services. By defining the pool’s fully qualified domain name (FQDN) and the parameter WebServer, the cmdlet returns the web-based services offered by your server, including the Address Book handler and distribution list expansion URIs.

For example:

    Get-CsService -PoolFqdn "fe01.contoso.net" -WebServer

This cmdlet returns the following:

Identity : WebServer:pool01.contoso.net

FileStore : FileStore:dc01.contoso.net

UserServer : UserServer:pool01.contoso.net

PrimaryHttpPort : 80

PrimaryHttpsPort : 443

ExternalHttpPort : 8080

ExternalHttpsPort : 4443

PublishedPrimaryHttpPort : 80

PublishedPrimaryHttpsPort : 443

PublishedExternalHttpPort : 80

PublishedExternalHttpsPort : 443

ReachPrimaryPsomServerPort : 8060

ReachExternalPsomServerPort : 8061

AppSharingPortStart : 49152

AppSharingPortCount : 16383

LIServiceInternalUri : https://internalweb.contoso.net/locationinformation/liservice.svc

ABHandlerInternalUri : https://internalweb.contoso.net/abs/handler

ABHandlerExternalUri : https://csweb.contoso.com/abs/handler

DLExpansionInternalUri : https://internalweb.contoso.net/groupexpansion/service.svc

DLExpansionExternalUri : https://csweb.contoso.com/groupexpansion/service.svc

CAHandlerInternalUri : https://internalweb.contoso.net/CertProv/CertProvisioningService.svc

CAHandlerInternalAnonUri : http://internalweb.contoso.net/CertProv/CertProvisioningService.svc

CollabContentInternalUri : https://internalweb.contoso.net/CollabContent

CollabContentExternalUri : https://csweb.contoso.com/CollabContent

CAHandlerExternalUri : https://csweb.contoso.com/CertProv/CertProvisioningService.svc

DeviceUpdateDownloadInternalUri : https://internalweb.contoso.net/RequestHandler/ucdevice.upx

DeviceUpdateDownloadExternalUri : https://csweb.contoso.com/RequestHandlerExt/ucdevice.upx

DeviceUpdateStoreInternalUri : http://internalweb.contoso.net/RequestHandler/Files

DeviceUpdateStoreExternalUri : https://csweb.contoso.com/RequestHandlerExt/Files

RgsAgentServiceInternalUri : https://internalweb.contoso.net/RgsClients/AgentService.svc

RgsAgentServiceExternalUri : https://csweb.contoso.com/RgsClients/AgentService.svc

MeetExternalUri : https://csweb.contoso.com/Meet

DialinExternalUri : https://csweb.contoso.com/Dialin

CscpInternalUri : https://internalweb.contoso.net/Cscp

ReachExternalUri : https://csweb.contoso.com/Reach

ReachInternalUri : https://internalweb.contoso.net/Reach

WebTicketExternalUri : https://csweb.contoso.com/WebTicket/WebTicketService.svc

WebTicketInternalUri : https://internalweb.contoso.net/WebTicket/WebTicketService.svc

ExternalFqdn : csweb.contoso.com

InternalFqdn : internalweb.contoso.net

DependentServiceList : {Registrar:pool01.contoso.net, ConferencingServer:pool01.contoso.net}

ServiceId : 1-WebServices-1

SiteId : Site:Redmond

PoolFqdn : pool01.contoso.net

Version : 5

Role : WebServer

<div>

## See Also


[Get-CsService](https://docs.microsoft.com/powershell/module/skype/Get-CsService)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

