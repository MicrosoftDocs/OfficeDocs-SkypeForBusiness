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

The use of EMS is optional. If you do not want Microsoft to automatically apply mitigations to your Skype for Business servers, you can disable the feature.  


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



> [!NOTE]
> The documentation for cmdlets will be made available soon.
