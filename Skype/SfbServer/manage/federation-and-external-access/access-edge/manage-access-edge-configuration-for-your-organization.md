---
title: 'Manage Access Edge Configuration for your organization'
ms.reviewer: 
ms:assetid: 0145eb08-984f-4ecd-bf9c-364817619c2a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ552443(v=OCS.15)
ms:contentKeyID: 48679555
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After deploying one or more Edge Servers, you must enable the types of external domain or provider access, remote user access, and anonymous user access to conferences through the Edge Servers that will be supported for your organization."
---

# Manage Access Edge Configuration for your organization

After deploying one or more Edge Servers, you must enable the types of external domain or provider access, remote user access, and anonymous user access to conferences through the Edge Servers that will be supported for your organization.

These options include the following types of access that can be configured through the **Access Edge Configuration** page:

  - **Enable federation and public IM connectivity**   Enable this if you want to support user access to federated partner domains. This setting applies to SIP federation configured for global, site, or user scopes on the **External Access Policy** page. For federation settings to apply, you must configure federation support on both pages.
    
    Two options exist that are optional settings for how federated partners are discovered, and whether archiving disclaimers (notification to federated contacts that you communicate with that your deployment has archiving enabled and that the communications details will be archived) will be sent to contacts:
    
      - **Enable partner domain discovery**   Selecting this option enables the automatic discovery of domains that you can federate with. Skype for Business Server uses Domain Name System (DNS) records to try to discover domains not listed in the allowed domains list, automatically evaluating incoming traffic from discovered federated partners and limiting or blocking that traffic based on trust level, amount of traffic, and administrator settings. If you do not select this option, federated user access is enabled only for users in the domains that you include on the allowed domains list. Whether or not you select this option, you can specify that individual domains to be blocked or allowed, including restricting access to specific servers running the Access Edge service in the federated domain. For details, see [Configure support for allowed external domains](../sip-domains/manage-sip-federated-domains-for-your-organization.md#configure-support-for-allowed-external-domains-in-skype-for-business-server).
    
      - **Send archiving disclaimer to federated partners**   Selecting this option enables the sending of an archiving disclaimer message to federated partners that advises them that communications details are recorded. If you archive external communications with federated partner domains, you should enable the archiving disclaimer notification to warn partners that their messages and communications details are being archived by your deployment. For details on archiving, see [Enable or disable sending an Archiving disclaimer to federated partner](enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md).

  - **Enable remote user access**   Enable this option if you want users in your organization who are outside your firewall, such as telecommuters and users who are traveling, to be able to connect to Skype for Business Server. For details, see [Enable or disable remote user access](enable-or-disable-remote-user-access.md).

  - **Enable anonymous users to access conferences**   Enable this option if you want internal users to invite external anonymous users to conferences that they organize. Enabling this setting only allows anonymous users for conferences.

> [!NOTE]  
> In addition to enabling external user access support, you also configure policies to control the use of remote user access in your organization before any type of external user access is available to users. For details about creating, configuring, and applying policies for external user access, see [Manage external access policy for your organization](../external-access-policies/manage-external-access-policy-for-your-organization.md).

**Viewing Access Edge configuration information by using Windows PowerShell cmdlets**

  - Access Edge configuration information can be viewed by using Windows PowerShell and the **Get-CsAccessEdgeConfiguration** cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 
    
    To view information about all your Access Edge configuration settings, type the following command in the Skype for Business Server Management Shell and then press ENTER:
    
     `Get-CsAccessEdgeConfiguration`
    
    That will return information similar to this:
    
        Identity                               : Global
        AllowAnonymousUsers                    : False
        AllowFederatedUsers                    : False
        AllowOutsideUsers                      : True
        BeClearingHouse                        : False
        EnablePartnerDiscovery                 : False
        EnableArchivingDisclaimer              : False
        EnableUserReplicator                   : True
        KeepCrlsUpToDateForPeers               : True
        MarkSourceVerifiableOnOutgoingMessages : True
        OutgoingTlsCountForFederatedPartners   : 4
        DiscoveredPartnerStandardRate          : 20
        EnableDiscoveredPartnerContactsLimit   : True
        MaxContactsPerDiscoveredPartner        : 1000
        DiscoveredPartnerReportPeriodMinutes   : 60
        MaxAcceptedCertificatesStored          : 1000
        MaxRejectedCertificatesStored          : 500
        CertificatesDeletedPercentage          : 20
        RoutingMethod                          : UseDnsSrvRouting

