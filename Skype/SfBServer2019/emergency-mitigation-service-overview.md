---
title: "Emergency Mitigation Service - Overview"
ms.reviewer: 
ms.author: akprakash
author: akprakash
manager: rahulgup
ms.date: 07/29/2023
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: "This article provides an overview of the Emergency Mitigation Service."
---

# Emergency Mitigation Service
Skype for Business (SfB) Server EMS helps keep your Skype for Business servers secure by applying mitigations to address specific potential threats against your servers.  

EMS uses the cloud-based Office Config Service (OCS) to check for new mitigations, download available mitigations, and send diagnostic data to Microsoft.  

> [!NOTE]
> The use of EMS is optional. If you do not want Microsoft to automatically apply mitigations to your Skype for Business servers, you can disable the feature. 

## Mitigations

A mitigation is an action or set of actions that are taken automatically to secure a Skype for Business server from a known threat that is being actively exploited in the wild.  

To help protect your organization and mitigate the risk, EMS will automatically disable features or functionalities on a Skype for Business server. 
 
EMS can apply the following types of mitigations: 

- **IIS URL Rewrite rule mitigation**: This mitigation is a rule that blocks specific patterns of malicious HTTP requests that can endanger a Skype for Business server.
- **App Pool mitigation**: This mitigation disables a vulnerable app pool on a Skype for Business server.

You have visibility and control over any applied mitigation by using Skype for Business PowerShell cmdlets. 

 ### How does it work
 
If Microsoft learns about a security exploit, an appropriate mitigation may be created and released. If this happens, the mitigation is sent from the OCS to EMS as a signed XML file containing the configuration settings that are required to apply the mitigation. 

EMS checks OCS for available mitigations every hour. EMS subsequently downloads newly discovered XML file mitigations and validates the signature to prevent file tampering. EMS checks the issuer, the extended Key Usage, and the certificate chain. After successful validation, EMS applies mitigation. 

Each mitigation is a temporary “fix” until the security update that fixes the vulnerability in the code is applied. EMS is not a replacement for Skype for Business SUs and CUs. However, it's the fastest and easiest way to mitigate the highest risks to internet-connected, on-premises SfB servers before updating. Customers do not have to undo the pre-existing mitigation when applying the SU or CU. The mitigation is automatically removed once a proper fix has been released.

## Connectivity

The EM service needs outbound connectivity to the OCS to check for and download mitigations. 

While the EM service can be installed without connectivity to the OCS, it must have connectivity to the OCS in order to download and apply the latest mitigations. The OCS must be reachable from the front end computer on which Skype for Business Server is installed for the EM service to function correctly.

|Endpoint|Address|Port|Description|
|---|---|---|---|
|Office Config Service|`https://config.officeapps.live.com/*|443|Required endpoint for the Skype for Business EM service|

You can verify that an Skype for Business server has connectivity to OCS by using the following cmdlet.

```Powershell
Test-CsMitigationServiceConnectivity
```
If the server has connectivity, the output is:

```powershell
Result: Success.
Message: The Mitigation Service endpoint is accessible from this computer.
```

If the server doesn't have connectivity, the output is:

```Powershell
Result: Failed.
Message: Unable to connect to the Mitigation Service endpoint from this computer.
```


## Diagnostic data collection

While installation, you will have an option to accept or reject data collection by Microsoft. This data helps us keep your servers safe and we recommend accepting this request.
In any case the installer should run successfully.
You can use **Get-CsMitigationTelemetryConfiguration** cmdlet to check if diagnostic data is being sent. 
You can use **Set-CsMitigationTelemetryConfiguration** cmdlet  to enable or disable sending diagnostic data at any point in time.

### Viewing Applied Mitigations

Once mitigations are applied to a server, you can view the applied mitigations by using **Get-CsMitigation** cmdlet.
For a more detailed view, you can export as an XML file using the *ExportAsXml* parameter.

## Disabling auto apply of Mitigations through EM Service

One of the EM service functions is downloading mitigations from the OCS and automatically applying them to the Skype for Business Server. If your organization has an alternate means of mitigating a known threat, you might choose to disable automatic applications of mitigations. You can enable or disable automatic mitigation at any point in time

By default, _MitigationsEnabled_ is set to `$true`. When set to `$false`, the EM service still checks for mitigations hourly but will not automatically apply mitigations

To disable automatic mitigation
```Powershell
Set-CsMitigationConfiguration - PoolFqdn <Pool1> -MitigationsEnabled $false
```

## Blocking or removing Mitigations
If a mitigation critically affects the functionality of your SfB server and you accept the risk of exposing your servers to the vulnerabilities, you can block the mitigation and manually reverse it. 

Use the following cmdlet to block a mitigation. Replace M0001 with the mitigation ID you wish to block.
```Powershell
Set-Csmitigation - PoolFqdn <poolName> -MitigationBlocked M0001
```

To add more than one mitigation, add the Mitigation ID as S comma separated list
```Powershell
Set-Csmitigation - PoolFqdn <poolName> -MitigationBlocked M0001,M002
```
> [!NOTE]
> To manually remove the mitigation immediately, stop and restart EMS

## Reapplying a Mitigation

You can remove one or more mitigations from the blocked mitigations list by:

Removing the Mitigation ID in the MitigationsBlocked parameter or using the MitigationsApplied parameter: 


```PowerShell
Set-Csmitigation - PoolFqdn <poolName> -MitigationApplied M0001
```

you can also use the cmdlet **Repair-CsMitigation**

> [!NOTE]
> To manually reapply the mitigation immediately, stop and restart EMS


