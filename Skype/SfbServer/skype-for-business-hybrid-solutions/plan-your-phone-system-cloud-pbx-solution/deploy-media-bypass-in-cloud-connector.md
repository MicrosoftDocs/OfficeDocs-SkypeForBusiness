---
title: "Deploy media bypass in Cloud Connector Edition"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 11/15/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom:
ms.assetid: 0ebba3a4-6124-434c-84aa-32b1cc3345bc
description: "Read this topic to learn about steps to deploy media bypass with Cloud Connector Edition version 2.0 and later."
---

# Deploy media bypass in Cloud Connector Edition
 
Read this topic to learn about steps to deploy media bypass with Cloud Connector Edition version 2.0 and later. 
  
Media bypass allows a client to send media directly to the Public Switched Telephone Network (PSTN) next hop—a gateway or Session Border Controller (SBC)—and eliminate the Cloud Connector Edition component from the media path. See also [Plan for media bypass in Cloud Connector Edition](plan-for-media-bypass-in-cloud-connector-edition.md).
  
## Enable media bypass

To enable media bypass, you must configure the DNS name of the media bypass web service and turn on media bypass in the tenant configuration. The media bypass web service deploys automatically on every Mediation Server. A tenant administrator must pick a name for a hybrid voice service (site), and this name should be from a SIP domain registered for hybrid voice. The service name should be the same across all Cloud Connector appliances and all PSTN sites regardless of the client location. The web service should only be available internally on the network.
  
A tenant administrator must configure a DNS A record in the internal production Active Directory. If you have a complex multi-site environment, see the example in [Example: media bypass web site DNS records in complex multi-site environments](deploy-media-bypass-in-cloud-connector.md#Example). The DNS record should only resolve for internal network clients; it should not resolve for external network clients.
  
After configuring DNS, connect to Skype for Business Online by using remote PowerShell with Skype for Business Administrator credentials. For more information, see [Set up your computer for Windows PowerShell](../../../SfbOnline/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md) .
  
In the PowerShell session, enter the following commands to enable media bypass:
  
```
Set-CsTenantHybridConfiguration -HybridConfigServiceInternalUrl http://newname.domain/hybridconfig/hybridconfigservice.svc
$mediabypass = New-CsNetworkMediaBypassConfiguration -AlwaysBypass $true -Enabled $true
Set-CsNetworkConfiguration -MediaBypassSettings $mediabypass
```

Enabling media bypass is a two-step process. The New-CsNetworkMedia cmdlet does not immediately save the new configuration; it only creates the settings in memory. The object created by this cmdlet must be saved to a variable, and then assigned to the MediaBypassSettings property of the network configuration. For more information, see [Example: media bypass web site DNS records in complex multi-site environments](deploy-media-bypass-in-cloud-connector.md#Example).
  
The replication between the on-premises and online components can take up to 24 hours, so Microsoft recommends that you run the necessary commands before enabling users.
  
## Confirm media bypass settings

You can check the media bypass settings as follows. 
  
To check online replication to your tenant pool, run the following command in remote PowerShell:
  
```
Get-CsTenantHybridConfiguration -LocalStore
Get-CsNetworkConfiguration -LocalStore
```

To check the on-premises replication, connect to the Cloud Connector Mediation servers, run the following command in PowerShell, and confirm that Enabled=True and AlwaysBypass=True
  
```
Get-CsNetworkConfiguration -LocalStore
```

To check the client settings, sign out of the Skype for Business client, sign back in, and confirm that the client has received the service URL as follows:
  
1. Open %appdatalocal%\Microsoft\Office\16.0\Lync\Tracing\Lync-UccApi-0.UccApilog. 
    
2. Search for hybridconfigserviceinternalurl and confirm the URL matches the one you defined.
    
## Change media bypass parameters

Tenant administrators are able to change the DNS name of the web service by running the following cmdlet:
  
```
Set-CsTenantHybridConfiguration -HybridConfigServiceInternalUrl http://newname.domain/hybridconfig/hybridconfigservice.svc
```

> [!IMPORTANT]
> Clients need to sign out and sign in to get the new service name and recognize the change. 
  
## Temporarily disable media bypass

This scenario might be useful for troubleshooting or maintenance. To disable the service, run the following cmdlets:
  
```
$mediabypass = New-CsNetworkMediaBypassConfiguration  -Enabled $false
Set-CsNetworkConfiguration -MediaBypassSettings $mediabypass
```

After making the change, it could take some time for changes to replicate to all Cloud Connectors. To check the status of replication, run the following cmdlet in PowerShell on Cloud Connector Mediation servers: 
  
```
Get- CsNetworkConfiguration -LocalStore
```

After the changes replicate, the web service on the Mediation Server will start rejecting client requests for the media bypass service.
  
## Disable media bypass permanently

To permanently disable media bypass, a tenant administrator needs to run the following commands: 
  
```
Set-CsTenantHybridConfiguration -HybridConfigServiceInternalUrl  $null
	$mediabypass = New-CsNetworkMediaBypassConfiguration  -Enabled $false 
Set-CsNetworkConfiguration -MediaBypassSettings $mediabypass 
```

An administrator will also need to remove the web addresses for media bypass from internal DNS servers. After making the change, it could take some time for changes to replicate to all Cloud Connector appliances. 
  
## Example: media bypass web site DNS records in complex multi-site environments
<a name="Example"> </a>

Clients will receive the web address of the media bypass web service from an internal DNS server. The name of the web service will be the same across all Cloud Connector appliances and Cloud Connector PSTN sites. In a complex multi-site environment, we recommend using the Windows 2016 DNS Policy for Geo-Location Based Traffic Management, so clients can be redirected to the web service which is local for their network. 
  
Fore more information about Windows 2016 DNS Policies, see [Use DNS Policy for Geo-Location Based Traffic Management with Primary Servers](https://docs.microsoft.com/windows-server/networking/dns/deploy/primary-geo-location).
  
The following is an example of configuration for a company with several sites using Windows 2016 DNS Policy for Geo-Location Based Traffic Management.
  
The name for the bypass service is 'hybridvoice.adatum.biz'.
  
The site in Amsterdam has four Cloud Connector appliances deployed with the following Mediation Server IP addresses:
  
- 192.168.1.45
    
- 192.168.1.46
    
- 192.168.1.47
    
- 192.168.1.48
    
The site in Seattle has three Cloud Connector appliances deployed with the following Mediation Server IP addresses:
  
- 10.10.1.8
    
- 10.10.1.9
    
- 10.10.1.10
    
Using Geo-Location Based Traffic Management, the DNS servers would be configured as follows:
  
1. Create DNS Client Subnets for both the Amsterdam and Seattle subnets.
    
2. Create DNS Zone Scopes for adatum.biz for both Amsterdam and Seattle.
    
3. Create DNS records in each DNS Zone Scope.
    
    Amsterdam
    
   - Type A;
    
   - Name : hybridvoice in the adatum.biz DNS zone
    
   - Target: 192.168.1.45
    
     Create additional records for additional mediation servers
    
   - 192.168.1.46
    
   - 192.168.1.47
    
   - 192.168.1.48
    
     Seattle
    
   - Type A
    
   - Name : hybridvoice in adatum.biz DNS zone
    
   - Target: 10.10.1.8
    
     Create additional records for additional mediation servers
    
   - 10.10.1.9
    
   - 10.10.1.10
    
4. Create the DNS policy that connects the client subnets to the appropriate zone scopes to ensure desired DNS resolution.
    
At this point, clients making DNS queries from the Amsterdam subnet for hybridvoice.adatum.biz will return the 192.168.1.45, 192.168.1.46, 192.168.1.47 and 192.168.1.48 addresses, while clients making the same query form Seattle will return 10.10.1.8, 10.10.1.9 and 10.10.1.10.

> [!NOTE]
> If the CCE appliance doesn't seem to be getting the updated settings, check to see if the appliance is able to contact the tenant via remote PowerShell. You can use Remote PowerShell to check appliance status with Get-CsHybridPSTNAppliance or use PowerShell on the CCE host to check status with Get-CcApplianceStatus.

  
## See also
<a name="Example"> </a>

[Plan for media bypass in Cloud Connector Edition](plan-for-media-bypass-in-cloud-connector-edition.md)
