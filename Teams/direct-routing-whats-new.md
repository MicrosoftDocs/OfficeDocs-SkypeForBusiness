---
title: What's New Direct Routing
ms.reviewer: CarolynRowe
ms.date: 03/29/2022
author: wlibebe
ms.author: wlibebe
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: This article describes what's new in Direct Routing. Check back often for updates.
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
---

# What's new for Direct Routing

This article describes what's new in Direct Routing. Check back often for updates.

## SIP certificate to MSPKI Certificate Authority change additional testing
On September 19th (starting at 4 PM UTC), Microsoft will perform a 24 hour test where all Microsoft SIP endpoints will be switched over to use certificates where the certificate chain will roll up to “DigiCert Global Root G2” Certificate Authority (CA). New Certificate Authority (CA) must be added in your SBC configuration and old Baltimore CA must be retained; do not replace the old CA.  If your SBC doesn’t trust this CA, you won't be able to connect to Teams SIP endpoints during the test. The final switch to the new Certificate Authority (CA) will be performed on October 3.

If you’d like to test and confirm your SBCs certificate configuration prior to the change, Microsoft has prepared a testing endpoint that you can use to verify that SBC appliances trust certificates issued from the new root CA (DigiCert Global Root G2). This endpoint should be used only for SIP OPTIONS ping messages and not for voice traffic. If your SBC can establish a TLS connection to this endpoint, then your connectivity to Teams services should not be affected by the change.

Test endpoint FQDN: sip.mspki.pstnhub.microsoft.com

Port: 5061

## SIP certificate to MSPKI Certificate Authority change test

On September 5th (starting 9 AM UTC) Microsoft will perform a 24h test where all Microsoft SIP endpoints will be switched over to use certificates where the certificate chain will roll up to “DigiCert Global Root G2” Certificate Authority (CA). If your SBC doesn’t trust this CA you might not be able to connect to Teams SIP endpoints.

If you’d like to test and confirm your SBCs certificate configuration prior to the change, Microsoft has prepared a testing endpoint that can be used to verify that SBC appliances trust certificates issued from the new root CA (DigiCert Global Root G2). This endpoint should be used only for SIP OPTIONS ping messages and not for voice traffic. If your SBC can establish a TLS connection to this endpoint, then your connectivity to Teams services should not be affected by the change.

Test endpoint FQDN: sip.mspki.pstnhub.microsoft.com

Port: 5061

## SIP certificate to MSPKI Certificate Authority change

Microsoft 365 is updating services powering messaging, meetings, telephony, voice, and video to use TLS certificates from a different set of Root Certificate Authorities (CAs). This change is being made because the current Root CA will expire in May 2025. Affected endpoints include all Microsoft SIP endpoints used for PSTN traffic that utilize TLS connectivity. The transition to certificates issued by the new CA will begin in late August.

The new Root CA "DigiCert Global Root G2" is widely trusted by operating systems including Windows, macOS, Android, and iOS and by browsers such as Microsoft Edge, Chrome, Safari, and Firefox. However, it is likely that your SBC has a certificate root store that is manually configured, and it needs to be updated. SBCs that do not have the new Root CA in their list of acceptable CAs will receive certificate validation errors, which may impact the availability or function of the service. Please refer to SBC vendor documentation on how to update the accepted certificate list on your SBC.

Today, the TLS certificates used by Microsoft SIP interfaces chain up to the following Root CA: 

Common Name of the CA: Baltimore CyberTrust Root
Thumbprint (SHA1): d4de20d05e66fc53fe1a50882c78db2852cae474
New TLS certificates used by Microsoft SIP interfaces will now chain up to the following Root CA:

Common Name of the CA: DigiCert Global Root G2
Thumbprint (SHA1): df3c24f9bfd666761b268073fe06d1cc8d4f82a4
The new CA certificate can be downloaded directly from DigiCert: DigiCert Global Root G2.

For more information, see [Office TLS Certificate Changes](/purview/encryption-office-365-tls-certificates-changes)
## New Direct Routing SIP endpoints 

Microsoft will introduce new signaling IPs to Teams Direct Routing SIP endpoints. To ensure this change doesn’t affect your service availability, make sure your Session Border Controller and Firewall are configured to use the recommended subnets 52.112.0.0/14 and 52.122.0.0/15 for classification and ACL rules. For more information, see [Microsoft 365, Office 365, and Office 365 GCC environments](direct-routing-plan.md#microsoft-365-office-365-and-office-365-gcc-environments).  

## Trunk demoting logic based on SIP Options

A new feature based on SIP Options is introduced for trunk health. When enabled in the gateway configuration (see Set-CsOnlinePSTNGateway cmdlet and SendSipOptions parameter), the routing logic for outbound calls demotes trunks that don't send SIP Options periodically (expected period is one SIP Option sent by the SBC per minute) to the Microsoft backend. These demoted trunks are put to the end of trunks list available for the outbound call and are tried last, which potentially decreases the call setup time.
Any trunk enabled for that feature that doesn't send at least one SIP Option within five minutes to any of the Microsoft regional (NOAM, EMEA, APAC, OCEA) SIP Proxies is considered demoted. If a trunk sends SIP Options to only a subset of Microsoft regional SIP Proxies, then these routes are tried first and the rest are demoted.
> [!NOTE] 
>
> Any SBC (configured under the customer or carrier tenant with **SendSipOptions** set to *true*) not sending SIP OPTIONS will be demoted. Customers who don't want that behavior should set **SendSipOptions** to *false* in their SBC configuration. The same applies to carrier trunks where the SBC configuration is either under the carrier or customer tenant. In these cases, when **SendSipOptions** is set to *true*, the SBC sends SIP OPTIONS.


## SIP support

On June 1, 2022, Microsoft will remove support for sip-all.pstnhub.microsoft.com and sip-all.pstnhub.gov.teams.microsoft.us FQDNs from Direct Routing configuration.

If no actions are taken before June 1, users won't be able to make or receive calls via Direct Routing.

To prevent service impact:

- Use the recommended subnets: (52.112.0.0/14 and 52.120.0.0/14) for any classification or ACL rules.
- Discontinue use of the sip-all FQDN when configuring Session Border Controls for  Direct Routing.

For more information, see [Plan Direct Routing](direct-routing-plan.md).
> [!NOTE]
> IP ranges presented in this document are specific to Direct Routing and may differ from the ones advised for Teams client.

## TLS certificates

Microsoft 365 is updating Teams and other services to use a different set of Root Certificate Authorities (CAs).

For more information and a full list of affected services, see [TLS certificate changes to Microsoft 365 services including Microsoft Teams](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/tls-certificate-changes-to-microsoft-365-services-including/ba-p/3249676).

## Certificate authorities

Beginning February 1, 2022, the Direct Routing SIP interface will only trust certificates signed by Certificate Authorities (CAs) that are part of the Microsoft Trusted Root Certificate Program. Take the following steps to avoid service impact:

- Ensure that your SBC certificate is signed by a CA that is part of the Microsoft Trusted Root Certificate Program.
- Verify that the Extended Key Usage (EKU) extension of your certificate includes "Server Authentication".

For more information about the Microsoft Trusted Root Certificate Program, see [Program Requirements - Microsoft Trusted Root Program](/security/trusted-root/program-requirements).

For a Trusted CA list, see [Microsoft Included CA Certificate List](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT).

## Replace headers

Starting April 2022, Direct Routing will reject SIP requests that have Replaces headers defined. There are no changes to flows where Microsoft sends Replaces header to the Session Border Controller(SBC).

Check your SBC configurations and ensure sure that you aren't using Replaces headers in SIP requests.

## TLS1.0 and 1.1

To provide the best-in-class encryption to our customers, Microsoft plans to deprecate Transport Layer Security (TLS) versions 1.0 and 1.1. On April 3, 2022, Microsoft will force TLS1.2 usage for the Direct Routing SIP interface.

To avoid any service impact, ensure that your SBCs are configured to support TLS1.2 and can connect using one of the following cipher suites:

- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 i.e. ECDHE-RSA-AES256-GCM-SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 i.e. ECDHE-RSA-AES128-GCM-SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384 i.e. ECDHE-RSA-AES256-SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 i.e. ECDHE-RSA-AES128-SHA256

## Related topics

- [Direct Routing - SIP protocol](direct-routing-protocols-sip.md)
