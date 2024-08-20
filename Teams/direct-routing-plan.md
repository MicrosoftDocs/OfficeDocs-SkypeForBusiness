---
title: "Plan Direct Routing"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
audience: ITPro
ms.reviewer: filippse
ms.date: 06/17/2024
ms.topic: conceptual
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
description: Learn how Microsoft Direct Routing lets you connect a supported customer-provided Session Border Controller (SBC) to Microsoft Teams Phone.
---

# Plan Direct Routing

Direct Routing lets you connect a supported, customer-provided Session Border Controller (SBC) to Microsoft Teams Phone. With this capability, you can configure on-premises Public Switched Telephone Network (PSTN) connectivity with Teams, as shown in the following diagram: 

![Diagram showing configuration of on-premises PSTN connectivity.](media/PlanDirectRouting1-PSTNwithTeams.png "Configuration of on-premises PSTN connectivity with Microsoft Teams")

Planning your deployment of Direct Routing is key to a successful implementation. This article describes infrastructure and licensing requirements, and provides information about SBC connectivity. Be sure to read this article before you start your configuration, which is described in [Configure Direct Routing](direct-routing-configure.md).

With Direct Routing, you can connect your SBC to almost any telephony trunk or interconnect with third-party PSTN equipment. Direct Routing enables you to: 

- Use virtually any PSTN trunk with Teams Phone. 

- Configure interoperability between customer-owned telephony equipment, such as a third-party private branch exchange (PBX), analog devices, and Teams.

Microsoft also offers all-in-the-cloud voice solutions, such as Microsoft Calling Plan. However, Direct Routing might be best for your organization if: 

- Microsoft Calling Plan isn't available in your country/region. 

- Your organization requires connection to third-party analog devices, call centers, and so on. 

- Your organization has an existing contract with a PSTN carrier.

For more information about voice solutions, see [Plan your Teams voice solution](cloud-voice-landing-page.md).

With Direct Routing, when users participate in a scheduled meeting, the dial-in number is provided by the Microsoft Audio Conferencing service, which requires proper licensing. When dialing out, Audio Conferencing places the call using online calling capabilities, which requires proper licensing. If a user doesn't have a Microsoft Audio Conferencing license, the call routes through Direct Routing. For more information, see [Direct Routing with Audio Conferencing](#direct-routing-with-audio-conferencing).

Direct Routing also supports users who have another license for Microsoft Calling Plan. For more information, see [Direct Routing with Calling Plan and Operator Connect](#direct-routing-with-calling-plans-and-operator-connect). 

## Infrastructure requirements

The infrastructure requirements for the supported SBCs, domains, and other network connectivity requirements to deploy Direct Routing are listed in the following table:  

|Infrastructure requirement|You need the following|
|:--- |:--- |
|Session Border Controller (SBC)|A supported SBC. For more information, see [Supported SBCs](#supported-session-border-controllers-sbcs).|
|Telephony trunks connected to the SBC|One or more telephony trunks connected to the SBC. On one end, the SBC connects to Teams Phone through Direct Routing. The SBC can also connect to third-party telephony entities, such as PBXs, Analog Telephony Adapters, and so on. Any PSTN connectivity option connected to the SBC will work. (For configuration of the PSTN trunks to the SBC, refer to the SBC vendors or trunk providers.)|
|Microsoft 365 organization|A Microsoft 365 organization that you use to home your Microsoft Teams users, and the configuration and connection to the SBC.|
|User registrar|User must be homed in Microsoft 365.<br/>If your company has an on-premises Skype for Business environment with hybrid connectivity to Microsoft 365, you can't enable voice in Teams for a user homed on-premises.<br/><br/>To check the registrar of a user, use the following Teams PowerShell cmdlet:<br/><code>Get-CsOnlineUser -Identity \<user> \| fl HostingProvider</code> <br/><br/>The output of the cmdlet should show:<br/><code>HostingProvider : sipfed.online.lync.com</code>|
|Domains|One or more domains added to your Microsoft 365 or Office 365 organizations.<br/><br/>You can't use the default domain, \*.onmicrosoft.com, which is automatically created for your tenant.<br/><br/>To view the domains, you can use the following Teams PowerShell cmdlet:<br/><code>Get-CsTenant \| fl Domains</code><br/><br/>For more information about domains and Microsoft 365 or Office 365 organizations, see [Domains FAQ](https://support.office.com/article/Domains-FAQ-1272bad0-4bd4-4796-8005-67d6fb3afc5a).|
|Public IP address for the SBC|A public IP address that can be used to connect to the SBC. Based on the type of SBC, the SBC can use NAT.|
|Fully Qualified Domain Name (FQDN) for the SBC|An FQDN for the SBC, where the domain portion of the FQDN is one of the registered domains in your Microsoft 365 or Office 365 organization. For more information, see [SBC domain names](#sbc-domain-names).|
|Public DNS entry for the SBC |A public DNS entry mapping the SBC FQDN to the public IP Address. |
|Public trusted certificate for the SBC |A certificate for the SBC to be used for all communication with Direct Routing. For more information, see [Public trusted certificate for the SBC](#public-trusted-certificate-for-the-sbc).|
|Connection points for Direct Routing |The connection points for Direct Routing are the following three FQDNs:<br/><br/>`sip.pstnhub.microsoft.com` – Global FQDN, must be tried first.<br/>`sip2.pstnhub.microsoft.com` – Secondary FQDN, geographically maps to the second priority region.<br/>`sip3.pstnhub.microsoft.com` – Tertiary FQDN, geographically maps to the third priority region.<br/><br/>For information on configuration requirements, see [SIP Signaling: FQDNs](#sip-signaling-fqdns).|
|Firewall IP addresses and ports for Direct Routing media |The SBC communicates to the following services in the cloud:<br/><br/>- SIP Proxy, which handles the signaling<br/>- Media Processor, which handles media -except when Media Bypass is on<br/><br/>These two services have separate IP addresses in Microsoft Cloud, described later in this document.<br/><br/>For more information, see the [Microsoft Teams section](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) in [URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges). |
|Media Transport Profile|TCP/RTP/SAVP <br/>UDP/RTP/SAVP|



## Licensing and other requirements 

Direct Routing users must have the following licenses assigned in Microsoft 365: 

- Teams Phone 
- Microsoft Teams 

For information about when an Audio Conferencing license is required, see [Direct Routing with Audio Conferencing](#direct-routing-with-audio-conferencing).

Direct Routing also supports users who are licensed for Microsoft Calling Plan. For more information, see [Direct Routing with Calling Plan and Operator Connect](#direct-routing-with-calling-plans-and-operator-connect).

For more information about licensing, see [Microsoft Teams licensing](user-access.md) and [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

Note: Direct Routing isn't supported in Islands mode.

### Direct Routing with Audio Conferencing 

This section describes requirements and considerations when using Direct Routing and Audio Conferencing.  

- **For GCC High and DoD G5 users**, Microsoft recommends that you disable the Audio Conferencing component included in G5 until you configure Direct Routing, and you've added Audio Conferencing numbers to your organization's tenant. 

- **For GCC High and DoD G3 users**, Microsoft recommends that you don't assign the Audio Conferencing license add-on until you configure Direct Routing, and you've added Audio Conferencing numbers to your organization's tenant.

 For more information, see [Audio Conferencing with Direct Routing for GCC High and DoD](./audio-conferencing-with-direct-routing-for-gcch-and-dod.md). 

#### Unplanned call escalation and Audio Conferencing license

A Teams user can start a one-on-one Teams-to-PSTN or Teams-to-Teams call and add a PSTN participant to it. The path that the call takes depends on whether the user who escalates the call has a Microsoft Audio Conferencing license assigned or not:

- **If the Teams user who escalates the call has a Microsoft Audio Conferencing license assigned**, the escalation happens through the Microsoft Audio Conferencing service. The remote PSTN participant who is invited to the existing call receives a notification about the incoming call, and sees the number of the Microsoft bridge assigned to the Teams user who initiated the escalation.

- **If the Teams user who escalates the call doesn't have the Microsoft Audio Conferencing license assigned**, the escalation happens through a Session Border Controller connected to the Direct Routing interface. The remote PSTN participant who is invited to the call receives a notification about the incoming call and sees the number of the Teams user who initiated the escalation. The specific SBC used for the escalation is defined by the routing policy of the user. 

You must ensure the following:
 
- CsOnlineVoiceRoutingPolicy is assigned to the user.

- Allow Private Calling is enabled at the tenant level for Microsoft Teams. 



### Direct Routing with Calling Plans and Operator Connect

Direct Routing also supports users who are licensed for Microsoft Calling Plan or assigned an Operator Connect phone number. Teams Phone with Calling Plan or Operator Connect enabled users can route some calls using the Direct Routing interface. 

Mixing Calling Plan or Operator Connect and Direct Routing connectivity for the same user is optional, but could be useful. For example, when the user is assigned a Microsoft Calling Plan or Operator Connect number but wants to route some calls using the SBC. 

One of the most common scenarios is calls to third-party PBXs. With this configuration, calls to the phones connected to the third-party PBX are routed using Direct Routing and therefore stay within the enterprise network, not traversing the PSTN. Meanwhile, all other calls are routed to the PSTN based on the users’ assigned PSTN connectivity method: Microsoft Calling Plan or Operator Connect.

For more information about Teams Phone licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).


## Supported end points

You can use the following as an end point:

- Any Teams client.

- Common area phones.  You don't need a Calling Plan license when setting up a common area phone with Direct Routing. For more information, see [Set up common area phones for Microsoft Teams](./set-up-common-area-phones.md).

## SBC domain names

The SBC domain name must be from one of the names registered in Domains of the tenant. 

The following table shows examples of DNS names registered for the tenant, whether the name can be used as an FQDN for the SBC, and examples of valid FQDN names. Note that you can't use the \*.onmicrosoft.com tenant for the FQDN name of the SBC.

|DNS name|Can be used for SBC FQDN|Examples of FQDN names|
|:--- |:--- |:--- |
contoso.com|Yes|**Valid names:**<br/>sbc1.contoso.com<br/>ssbcs15.contoso.com<br/>europe.contoso.com|
|contoso.onmicrosoft.com|No|Using *.onmicrosoft.com domains isn't supported for SBC names

Assume you want to use a new domain name. For example, your tenant has contoso.com as a domain name registered in your tenant, and you want to use sbc1.sip.contoso.com. 

Before you can pair an SBC with the name sbc1.sip.contoso.com, you must register the domain name sip.contoso.com in Domains in your tenant. If you try pairing an SBC with sbc1.sip.contoso.com before registering the domain name, you'll get the following error: "Can't use the "sbc1.sip.contoso.com" domain as it wasn't configured for this tenant."

After you add the domain name, you need to create a user with UPN user@sip.contoso.com and assign a Teams license. It may take up to 24 hours to fully provision the domain name after it's added to Domains of your tenant, to create a user with a new name, and to assign a license to the user.

It's possible that a company might have several SIP address spaces in one tenant. For example, a company might have contoso.com as a SIP address space and fabrikam.com as the second SIP address space. Some users have address user@contoso.com and some users have address user@fabrikam.com. 

The SBC only needs one FQDN and can service users from any address space in the paired tenant. For example, an SBC with the name sbc1.contoso.com can receive and send the PSTN traffic for users with addresses user@contoso.com and user@fabrikam.com as long as these SIP address spaces are registered in the same tenant.  

 > [!NOTE]
 > SBC FQDN in Azure Communication Services direct routing must be different from SBC FQDN in Teams Direct Routing.
  
## Public trusted certificate for the SBC

Microsoft recommends that you request the certificate for the SBC by generating a certification signing request (CSR). For specific instructions on generating a CSR for an SBC, see the interconnection instructions or documentation provided by your SBC vendors.

> [!NOTE]
> Most Certificate Authorities (CAs) require the private key size to be at least 2048. Keep this in mind when generating the CSR.

The certificate needs to have the SBC FQDN as the common name (CN) or the subject alternative name (SAN) field.

Alternatively, Direct Routing supports a wildcard in the CN and/or SAN, and the wildcard needs to conform to standard [RFC HTTP Over TLS](https://tools.ietf.org/html/rfc2818#section-3.1).

An example would be using \*.contoso.com, which would match the SBC FQDN sbc.contoso.com, but wouldn't match with sbc.test.contoso.com.

Direct Routing SIP interface will only trust certificates that are signed by Certificate Authorities (CAs) that are part of the Microsoft Trusted Root Certificate Program. Make sure that a CA that is part of the program signs your SBC certificate. Also make sure that the Extended Key Usage (EKU) extension of your certificate includes Server Authentication and Client Authentication.

For more information, see
[Program Requirements - Microsoft Trusted Root Program](/security/trusted-root/program-requirements) and [Included CA Certificate List](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT).

> [!NOTE]
> At the end of August 2023, Microsoft 365 will update its services to use TLS certificates issued by the new CA "DigiCert Global Root G2". To avoid errors that may impact your service, you must update your SBC's certificate root store to include the new Root CA. For more information, see [SIP Certificate To MSPKI Certificate Authority Change](direct-routing-whats-new.md#sip-certificate-to-mspki-certificate-authority-change).
  
 For Direct Routing in Office 365 GCCH and DoD environments, one of the following root certificate authorities needs to generate the certificate:

- DigiCert Global Root CA
- DigiCert High Assurance EV Root CA

> [!NOTE]
> If Mutual TLS (MTLS) support is enabled for the Teams connection on the SBC, then you must install the Baltimore CyberTrust Root and the DigiCert Global Root G2 certificates in the SBC Trusted Root Store of the Teams TLS context. (This is because the Microsoft service certificates use one of these two root certificates.) To download these root certificates, see [Microsoft 365 Encryption chains](/microsoft-365/compliance/encryption-office-365-certificate-chains). For more information, see [Office TLS Certificate Changes](/microsoft-365/compliance/encryption-office-365-tls-certificates-changes).
  
To verify that the MTLS connection originates from Teams infrastructure, the SBC should be configured to implement the following checks on the Teams server-side certificate:

- Check that the certificate issuance chain originates from one of the following root CAs:
  - [Baltimore CyberTrust Root](/microsoft-365/compliance/encryption-office-365-certificate-chains#baltimore-cybertrust-root)
  - [DigiCert Global Root G2](/microsoft-365/compliance/encryption-office-365-certificate-chains#digicert-global-root-g2)

- Check that the certificate "Subject Alternative Name" includes "sip.pstnhub.microsoft.com".

## SIP signaling: FQDNs, ports, failover mechanism

Direct Routing is offered in the following environments:

- Microsoft 365 or Office 365
- Office 365 GCC
- Office 365 GCC High
- Office 365 DoD

For more information about government environments, such as GCC, GCC High, and DoD, see [Office 365 and US Government environments](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

The following sections describe information about FQDNs, ports, and failover mechanisms.

### SIP signaling: FQDNs

The following sections describe the FQDN connection points for various Microsoft cloud environments.

#### Microsoft 365, Office 365, and Office 365 GCC environments

In these environments, the connection points for Direct Routing are the following three FQDNs:

- **sip.pstnhub.microsoft.com** – Global FQDN – must be tried first. When the SBC sends a request to resolve this name, the Microsoft Azure DNS servers return an IP address pointing to the primary Azure datacenter assigned to the SBC. The assignment is based on performance metrics of the datacenters and geographical proximity to the SBC. The IP address returned corresponds to the primary FQDN.

- **sip2.pstnhub.microsoft.com** – Secondary FQDN – geographically maps to the second priority region.

- **sip3.pstnhub.microsoft.com** – Tertiary FQDN – geographically maps to the third priority region.

Placing these three FQDNs in order is required to:

- Provide optimal experience (less loaded and closest to the SBC datacenter assigned by querying the first FQDN).

- Provide failover when connection from an SBC is established to a datacenter that is experiencing a temporary issue. For more information, see [Failover mechanism](#sip-signaling-failover-mechanism).  

The FQDNs sip.pstnhub.microsoft.com, sip2.pstnhub.microsoft.com, and sip3.pstnhub.microsoft.com are resolved to IP addresses from the following subnets:

- 52.112.0.0/14
- 52.122.0.0/15
  
You need to open ports for all these IP address ranges in your firewall to allow incoming and outgoing traffic to and from the addresses for signaling.

Note: Inbound SIP traffic to the SBCs from Teams SIP endpoints can originate from any IPs in these subnets--not only from IPs that resolve from the previously mentioned FQDNs. For more information on how to set up SIP peering, see your SBC documentation. 

#### Office GCC DoD environment

In the Office GCC DoD environment, the connection point for Direct Routing is the following FQDN:

**sip.pstnhub.dod.teams.microsoft.us** – Global FQDN. As the Office 365 DoD environment exists only in the US data centers, there's no secondary and tertiary FQDNs.

The FQDN sip.pstnhub.dod.teams.microsoft.us is resolved to an IP address from the following subnet: 52.127.64.0/21

To allow incoming and outgoing traffic to and from the addresses for signaling, you need to open ports for all these IP addresses in your firewall.

#### Office 365 GCC High environment

In the Office 365 GCC High environment, the connection point for Direct Routing is the following FQDN:

**sip.pstnhub.gov.teams.microsoft.us** – Global FQDN. As the GCC High environment exists only in the US data centers, there's no secondary and tertiary FQDNs.

The FQDN sip.pstnhub.gov.teams.microsoft.us is resolved to an IP address from the following subnet:  52.127.88.0/21

To allow incoming and outgoing traffic to and from the addresses for signaling, you need to open ports for all these IP addresses in your firewall.

### SIP signaling: Ports

You must use the following ports for Microsoft 365 or Office 365 environments where Direct Routing is offered:

|Traffic|From|To|Source port|Destination port|
|:--- |:--- |:--- |:--- |:--- |
|SIP/TLS|SIP Proxy|SBC|1024 – 65535|Defined on the SBC (For Office 365 GCC High/DoD only port 5061 must be used)|
SIP/TLS|SBC|SIP Proxy|Defined on the SBC|5061|


### SIP signaling: Failover mechanism

To resolve sip.pstnhub.microsoft.com, the SBC makes a DNS query. Based on the SBC location and the datacenter performance metrics, the primary datacenter is selected. 

If the primary datacenter experiences an issue, the SBC tries sip2.pstnhub.microsoft.com, which resolves to the second assigned datacenter. In the rare case that datacenters in two regions aren't available, the SBC retries the last FQDN (sip3.pstnhub.microsoft.com), which provides the tertiary datacenter IP.

The following table summarizes the relationships between primary, secondary, and tertiary datacenters:

|If the primary datacenter is|EMEA|NOAM|ASIA|
|:--- |:--- |:--- |:--- |
|The secondary datacenter (sip2.pstnhub.microsoft.com)|US|EU|US|
|The tertiary datacenter (sip3.pstnhub.microsoft.com)|ASIA|ASIA|EU|


## Media traffic: port ranges, media processors, CODECS

### Media traffic: port ranges

If you want to deploy Direct Routing without media bypass, the following requirements apply. For firewall requirements for media bypass, see [Plan for media bypass with Direct Routing](./direct-routing-plan-media-bypass.md).

The media traffic flows to and from a separate service in the Microsoft Cloud. The IP address ranges for media traffic are as follows.

> [!NOTE]
> IP ranges presented in this document are specific to Direct Routing and may differ from the ones advised for Teams client.

#### Microsoft 365, Office 365, and Office 365 GCC environments

In the Microsoft 365, Office 365, and Office 365 GCC environments, the IP address ranges are:

- 52.112.0.0/14 (IP addresses from 52.112.0.0 to 52.115.255.255)
- 52.120.0.0/14 (IP addresses from 52.120.0.0 to 52.123.255.255)

#### Office 365 DoD environment

In the Office 365 DoD environment, the IP address ranges are:

- 52.127.64.0/21

#### Office 365 GCC High environment

In the Office 365 GCC High environment, the IP address ranges are:

- 52.127.88.0/21

#### All environments

The port ranges of the media processors are shown in the following table:

|Traffic|From|To|Source port|Destination port|
|:--- |:--- |:--- |:--- |:--- |
|UDP/SRTP|Media Processor|SBC|3478-3481 and 49152 – 53247|Defined on the SBC|
|UDP/SRTP|SBC|Media Processor|Defined on the SBC|3478-3481 and 49152 – 53247|

> [!NOTE]
 > Microsoft recommends at least two ports per concurrent call on the SBC.

### Media traffic: processors geography

Media traffic flows through components called media processors. Media processors are placed in the same datacenters as SIP proxies as follows:

- NOAM (US South Central, two in US West and US East datacenters)
- Europe (UK South, France Central, Amsterdam, and Dublin datacenters)
- Asia (Singapore datacenter)
- Japan (JP East and West datacenters)
- Australia (AU East and Southeast datacenters)
- LATAM (Brazil South)

### Media traffic: Codecs

The following sections describe the codecs for media traffic.

### Leg between SBC and Cloud Media Processor or Microsoft Teams client

Applies to both media bypass case and non-bypass cases.

The Direct Routing interface on the leg between the Session Border Controller and Cloud Media Processor (without media bypass) or between the Teams client and the SBC (if media bypass is enabled) can use the following codecs:

- Non-Media bypass (SBC to Cloud media processor): SILK, G.711, G.722, G.729
- Media bypass (SBC to Teams client):  SILK, G.711, G.722, G.729

You can force use of the specific codec on the Session Border Controller by excluding undesirable codecs from the offer.

### Leg between Microsoft Teams client and Cloud media processor

Applies to non-media bypass case only. With media bypass, the media flows directly between the Teams client and the SBC.

On the leg between the Cloud media processor and the Teams client, either SILK or G.722 is used. The codec choice on this leg is based on Microsoft algorithms, which take into consideration multiple parameters.

> [!NOTE]
> Media re-targeting isn't supported. During a call, if Direct Routing SBC SIP re-Invite (Offer) contains a new media IP address, port, or transport, media isn't sent from PSTN Hub to the new target. Per RFC 3264 8.3.1, media re-target support is optional (not required). 

## Supported Session Border Controllers (SBCs)

Microsoft only supports certified SBCs to pair with Direct Routing. Because Enterprise Voice is critical for businesses, Microsoft runs intensive tests with the selected SBCs, and works with the SBC vendors to ensure the two systems are compatible.

Devices that are validated are listed as Certified for Teams Direct Routing. The certified devices are guaranteed to work in all scenarios.

For more information about supported SBCs, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

## Support boundaries

Microsoft only supports Teams Phone with Direct Routing when used with certified devices. If there are issues, you must contact your SBC vendor's customer support first. If needed, the SBC vendor escalates the issue to Microsoft through internal channels. Microsoft reserves the right to reject support cases where a non-certified device is connected to Teams Phone through Direct Routing. If Microsoft determines that a customer's Direct Routing issue is with a vendor's SBC device, the customer needs to re-engage the SBC vendor for support.

## See also

- [Configure Direct Routing](direct-routing-configure.md)
- Video session: [Direct Routing in Microsoft Teams](https://aka.ms/teams-direct-routing).
