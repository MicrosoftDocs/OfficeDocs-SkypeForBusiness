---
title: "Session Border Controllers certified for Direct Routing"
ms.author: crowe
ms.reviewer: FilippSe
ms.date: 06/12/2024
author: CarolynRowe
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: high
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - Tier1
appliesto:
  - Microsoft Teams
hideEdit: true
f1.keywords:
- NOCSH
description: Learn about which Session Border Controllers (SBCs) have been certified for Microsoft Direct Routing.
ms.custom: seo-marvel-apr2020
---

# Session Border Controllers certified for Direct Routing

Microsoft partners with selected Session Border Controllers (SBC) vendors to certify that their SBCs work with Direct Routing.

Microsoft works with each vendor to:

- Jointly work on the SIP interconnection protocols.
- Perform intense tests using a third-party lab. Only devices that pass the tests are certified.
- Run daily tests with all certified devices in production and pre-production environments. Validating the devices in pre-production environments guarantees that new versions of Direct Routing code in the cloud works with certified SBCs.
- Establish a joint support process with the SBC vendors.

  > [!NOTE]
  > Microsoft only supports Phone System with Direct Routing when used with certified devices. In case of issues, you must contact your SBC vendor's customer support first. If needed, the SBC vendor will escalate the issue to Microsoft via internal channels. Microsoft reserves the right to reject support cases where a non-certified device is connected to Phone System through Direct Routing. If Microsoft determines that a customer's Direct Routing issue is with a vendor's SBC device, the customer will need to re-engage the SBC vendor for support.
  >
  > The certification is granted to specific SBC firmware versions. Any SBC firmware version documented in this article is both certified and supported. Firmware versions that are higher than what is documented are supported as long as the major.minor version is the same.
  >
  > Example:
  >
  > - Supported 6.10.258 - In this case, Microsoft supports firmware versions 6.10.(258 or higher).
  > - Recommended 6.20.100 - In this case, Microsoft recommends firmware versions 6.20.(100 or higher).
  > - For supportability questions about specific version, reach out to your SBC vendor.

The tables that follow list devices certified for Direct Routing. (For information about which SBC vendors support Local Media Optimization, see [Configure Local Media Optimization for Direct Routing](direct-routing-media-optimization-configure.md).)

For more information about Direct Routing, see [Plan Direct Routing](direct-routing-plan.md).  

Note that we're not accepting new nominations for certification until further notice.

## Certified SBC vendors

|Vendor|Product|Non-media bypass|Media bypass|Software version|911 Service Provider Capable*|ELIN capable|
|---|---|---|---|---|---|---|
|[Microsoft](https://azure.microsoft.com/products/communications-gateway/)|Azure Communications Gateway |&#10004;|&#10004;|2023-01-31|&#10004;|&#10004;|
|[AudioCodes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)|Mediant 500 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant 500 Li SBC|&#10004;|&#10004;|Supported 7.2x.xxx (Recommended 7.40A.400)|&#10004;|&#10004;|
||Mediant 800 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant 2600 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant 4000 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant 1000B  SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant 9000  SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Virtual Edition SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant Cloud Edition SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||Mediant 3100|&#10004;|&#10004;|Supported 7.20A.250 (Recommended 7.40A.500)|&#10004;|&#10004;|
|[Ribbon Communications](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-skype-business)|SBC 5400|&#10004;|&#10004;|Supported on available versions of 11.1 and later, 10.1, 9.2, and 7.2 (Recommend latest version)|&#10004;||
||SBC 7000|&#10004;|&#10004;|Supported on available versions of 11.1 and later, 10.1, 9.2, and 7.2 (Recommend latest version)|&#10004;||
||All SBC SWe variants, including hosted offers|&#10004;|&#10004;|Supported on available versions of 11.1 and later, 10.1, 9.2, and 7.2 (Recommend latest version)|&#10004;||
||SBC 1000|&#10004;|&#10004;|Supported on available versions of 12.x and later, 11.x, or 9.x (Recommend latest version)|&#10004;|&#10004;|
||SBC 2000|&#10004;|&#10004;|Supported on available versions of 12.x and later, 11.x, or 9.x (Recommend latest version)|&#10004;|&#10004;|
||SBC SWe Edge (formerly SWe Lite)|&#10004;|&#10004;|Supported on available versions of 12.x and later, 11.x, or 9.x (Recommend latest version)|&#10004;|&#10004;|
||Edge 8000 (w/SBC SWe Edge)|&#10004;|&#10004;|23.06 or higher|&#10004;|&#10004;|
||EdgeMarc Series|&#10004;|&#10004;|16.3.2|||
|[Thinktel](https://thinktel.ca/services/complete-your-microsoft-teams-voice-solution-with-think365-cloud-voice/)|Think 365 SBC|&#10004;||1.4|||
|[Oracle](https://www.oracle.com/communications/partner-microsoft/)|AP 1100|&#10004;|&#10004;|Supported 8.3.0.0.1 &  Recommended 8.4.x & 9.x|&#10004;|&#10004;|
||AP 3900|&#10004;|&#10004;|Supported 8.3.0.0.1 &  Recommended 8.4.x & 9.x|&#10004;|&#10004;|
||AP 4600|&#10004;|&#10004;|Supported 8.3.0.0.1 &  Recommended 8.4.x & 9.x|&#10004;|&#10004;|
||AP 6300|&#10004;|&#10004;|Supported 8.3.0.0.1 &  Recommended 8.4.x & 9.x|&#10004;|&#10004;|
||AP 6350|&#10004;|&#10004;|Supported 8.3.0.0.1 &  Recommended 8.4.x & 9.x|&#10004;|&#10004;|
||VME|&#10004;|&#10004;|Supported 8.3.0.0.1 &  Recommended 8.4.x & 9.x|&#10004;|&#10004;|
||AP 3950|&#10004;|&#10004;|Supported 9.x|&#10004;|&#10004;|
||AP 4900|&#10004;|&#10004;|Supported 9.x|&#10004;|&#10004;|
|[TE-SYSTEMS](https://www.anynode.de/anynode-and-microsoft-teams/)|anynode|&#10004;|&#10004;|Supported 3.20 (Recommended 4.0)|&#10004;|&#10004;|
|[Metaswitch](https://www.metaswitch.com/products/core-network/perimeta-sbc)|Perimeta SBC|&#10004;|&#10004;|4.7 (4.9 for Media Bypass)|&#10004;|&#10004;|
|[Cisco](https://www.cisco.com/c/en/us/solutions/enterprise/interoperability-portal/networking_solutions_products_genericcontent0900aecd805bd13d.html)|Cisco Unified Border Element (CUBE) for 1000 Series Integrated Services Routers|&#10004;|&#10004;|Supported IOS XE Amsterdam 17.2.1r (Recommended 17.6.1a)|&#10004;||
||Cisco Unified Border Element (CUBE) for 4000 Series Integrated Services Routers|&#10004;|&#10004;|Supported IOS XE Amsterdam 17.2.1r (Recommended 17.6.1a)|&#10004;||
||Cisco Unified Border Element (CUBE) for 1000V Series Cloud Services Router|&#10004;|&#10004;|Supported IOS XE Amsterdam 17.2.1r (Recommended 17.3.3)|&#10004;||
||Cisco Unified Border Element (CUBE) for 1000 Series Aggregation Services Routers|&#10004;|&#10004;|Supported IOS XE Amsterdam 17.2.1r (Recommended 17.6.1a)|&#10004;||
||Cisco Unified Border Element (CUBE) for Catalyst 8000 Edge Platforms|&#10004;|&#10004;|Supported IOS XE Amsterdam 17.3.2 (Recommended 17.6.1a)|&#10004;||
|[Avaya](https://support.avaya.com/products/P0997/avaya-session-border-controller-for-enterprise/8.1.x)|Avaya Session Border Controller for Enterprise (ASBCE)|&#10004;|&#10004;|Release 8.1.1 or higher (8.1.2 or higher for Media Bypass)|||
|[Nokia](https://documentation.nokia.com/aces/cgi-bin/chk_access.cgi/3TB30222GBAAACZZA.zip)|Nokia Session Border Controller|&#10004;|&#10004;|23.8|&#10004;||
|[Italtel](https://www.italtel.com/italtel-provides-direct-routing-sbc-for-microsoft-teams/)|NetMatch-S CI|&#10004;|&#10004;|Supported 5.8 (Recommended the latest version)|&#10004;|&#10004;|
|[Ericsson](https://www.ericsson.com/en/portfolio/digital-services/cloud-communication/enterprise-communication/business-communication-services-and-enablers/sip-trunking)|vSBC 2.16|&#10004;|||||
|[Cataleya](https://cataleya.com/cataleya-launches-orchid-cloud-revolutionary-cloud-based-wholesale-voice-business-platform/)|Orchid Link|&#10004;||3.1|||
|[ULTATEL](https://www.ultatel.com/services/direct-routing-teams-sbc)|Teams SBC|&#10004;|&#10004;|1.6|||
|[Mitel](https://unify.com/en/solutions/voice-platforms/session-border-controller)|Unify OpenScape Session Border Controller|&#10004;|&#10004;|V10R2.2.0 or higher|||
|[Sansay Inc.](https://www.sansay.com/solutions/microsoft-teams/)|vmVSXi|&#10004;|&#10004;|10.5.1.354-vm-S-x64|&#10004;||
|[Enghouse Networks](https://www.enghousenetworks.com/portfolio/network-infrastructure/cloud-native-session-border-controller-sbc/)|Dialogic BorderNet SBC|&#10004;|&#10004;|3.9.x|||
|[Patton Electronics Co.](https://www.patton.com/microsoft/)|Patton SmartNode eSBC|&#10004;||3.19.x|||
|[M5 Technologies (previously known as Media5 Corporation)](https://www.m5t.com/pages/sentinel-400-sbc-_-2023_0-2023-06-16)|Mediatrix Sentinel Series|&#10004;||DGW 48.0.2340 (Recommended DGW 48.1.2503)|||
|[Ekinops](https://www.ekinops.com/solutions/voice-data-access/microsoft-direct-routing-sbc)|Ekinops Session Border Controller (ONeSBC)|&#10004;|&#10004;|Supported 6.9.x (Recommended 6.10.x)|||
||Ekinops Virtual Session Border Controller (ONEvSBC)|&#10004;|&#10004;|Supported 6.9.x (Recommended 6.10.x)|||
|[46 Labs LLC](https://46labs.atlassian.net/wiki/spaces/peeredge/pages/61603842/Microsoft+Teams+Implementation+Guide+v1.0)|Peeredge Orchestrator|&#10004;|&#10004;|1.0.6|||
|[Frafos](https://www.frafos.com/ms-teams-abc-sbc)|ABC SBC|&#10004;||4.6|||
|[Nuera](https://www.nuera.com/sbc-media-gateway)|GX-500 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-500 Li SBC|&#10004;|&#10004;|Supported 7.2x.xxx (Recommended 7.40A.400)|&#10004;|&#10004;|
||GX-800 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-2600 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-4000 SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-1000B  SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-9000  SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-VE SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-CE SBC|&#10004;|&#10004;|Supported 7.20A.258 (Recommended 7.40A.500)|&#10004;|&#10004;|
||GX-3100|&#10004;|&#10004;|Supported 7.20A.250 (Recommended 7.40A.500)|&#10004;|&#10004;|

\* **911 service providers**

The following emergency services providers are certified and supported by Microsoft.  Microsoft reserves the right to reject support cases where a non-certified provider is used.

- [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing/)
- [Intrado Emergency Routing Service (ERS)](https://www.intrado.com/enterprise-solutions/e911/microsoft-teams)
- [Inteliquent](https://www.inteliquent.com/services/emergency-services/e911)

## Support for Local Media Optimization

The following table describes which SBC vendors support [Local Media Optimization](direct-routing-media-optimization.md).

|Vendor|Product|Software version|
|:---|:---|:---|
|[Audiocodes](https://www.audiocodes.com/media/13253/connecting-audiocodes-sbc-to-microsoft-teams-direct-routing-enterprise-model-configuration-note.pdf)|Mediant 500 SBC|7.20A.256|
||Mediant 800 SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
||Mediant 2600 SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
||Mediant 4000 SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
||Mediant 1000B SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
||Mediant 9000 SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
||Mediant Virtual Edition SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
||Mediant Cloud Edition SBC|Supported 7.20A.258 (Recommended 7.40A.100)|
|[Ribbon SBC Core](https://support.sonus.net/display/ALLDOC/SBC+8.2+-+Configure+Local+Media+Optimization)|SBC 5110|8.2 or higher SW version|
||SBC 5210|8.2 or higher SW version|
||SBC 5400|8.2 or higher SW version|
||SBC 7000|8.2 or higher SW version |
||SBC SWe|8.2 or higher SW version|
|[Ribbon SBC Edge](https://support.sonus.net/display/UXDOC81/Best+Practice+-+Configuring+Microsoft+Teams+Local+Media+Optimization)|SBC SWe Edge (formerly SWe Lite)|8.1.5 or higher SW version|
||SBC 1000|8.1.5 or higher SW version|
||SBC 2000|8.1.5 or higher SW version|
||SBC 8000 (w/SBC SWe Edge)|23.06 or higher SW version|
|[TE-SYSTEMS](https://www.anynode.de/local_media_optimization/)|anynode|4.0.1+|
|[Oracle](https://www.oracle.com/communications/partner-microsoft/)|AP 1100|8.4.0.0.0|
||AP 3900|8.4.0.0.1 &  9.x|
||AP 4600|8.4.0.0.1 &  9.x|
||AP 6300|8.4.0.0.1 &  9.x|
||AP 6350|8.4.0.0.1 &  9.x|
||VME|8.4.0.0.1 &  9.x|
||AP 3950|9.x|
||AP 4900|9.x|
|[Avaya](https://documentation.avaya.com/en-US/bundle/WorkingWithAvayaSBCEandMicrosoftTeams_r81x/page/About_Avaya_SBCE_and_MS_Teams.html)|Avaya Session Border Controller for Enterprise (ASBCE)|10.1.2 or higher|
|[Italtel](https://www.italtel.com/italtel-provides-direct-routing-sbc-for-microsoft-teams/)|NetMatch-S CI|5.7 or higher SW version|
|[Enghouse Networks](https://www.enghousenetworks.com/portfolio/network-infrastructure/cloud-native-session-border-controller-sbc/)|Enghouse BorderNet|3.9.2-XY or higher SW version|

## Direct Routing and analog devices interoperability

The following table lists devices that are verified for interoperability between Direct Routing and Analog Devices.

|Vendor|Product|Verified|
|---|---|---|
|[AudioCodes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)|[ATA-1](https://www.audiocodes.com/media/2373/mp-1xx-and-mp-124-datasheet.pdf)|&#10004;|
|[AudioCodes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)|[ATA-2](https://www.audiocodes.com/media/2399/mediapack-20x-mp-20x-analog-telephone-adapters-datasheet.pdf)|&#10004;|
|[Cisco](https://www.cisco.com/c/en/us/products/collateral/unified-communications/ata-190-series-analog-telephone-adapters/datasheet-c78-740013.html)|ATA 191 Multiplatform Analog Telephone Adapter|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 1100 Software Version Supported 8.3.0.1.2 & Recommended 8.4.x or  9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 3900 Software Version Supported 8.3.0.1.2 & Recommended 8.4.x or  9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 4600 Software Version Supported 8.3.0.1.2 & Recommended 8.4.x or  9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 6300 Software Version Supported 8.3.0.1.2 & Recommended 8.4.x or  9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 6350 Software Version Supported 8.3.0.1.2 & Recommended 8.4.x or  9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|VME Software Version Supported 8.3.0.1.2 & Recommended 8.4.x or  9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 3950 Software Version Supported 9.x|&#10004;|
|[Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html)|AP 4900 Software Version Supported 9.x|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[SBC 1000. Software version: 8.1.1 (build 527) or higher SW version](https://support.sonus.net/display/UXDOC81/Connect+SBC+Edge+to+Microsoft+Teams+Direct+Routing+to+Support+Analog+Devices)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[SBC 2000. Software version: 8.1.1 (build 527) or higher SW version](https://support.sonus.net/display/UXDOC81/Connect+SBC+Edge+to+Microsoft+Teams+Direct+Routing+to+Support+Analog+Devices)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[EdgeMarc 302. Software version: 16.1.1 or higher SW version](https://ribboncommunications.com/products/service-provider-products/cloud-and-edge/session-border-controllers/session-border-controllers-edge-appliances)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[EdgeMarc 304. Software version: 16.1.1 or higher SW version](https://ribboncommunications.com/products/service-provider-products/cloud-and-edge/session-border-controllers/session-border-controllers-edge-appliances)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[EdgeMarc 2900A. Software version: 16.1.1 or higher SW version](https://ribboncommunications.com/products/service-provider-products/cloud-and-edge/session-border-controllers/session-border-controllers-edge-appliances)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[EdgeMarc 4806. Software version: 16.1.1 or higher SW version](https://ribboncommunications.com/products/service-provider-products/cloud-and-edge/session-border-controllers/session-border-controllers-edge-appliances)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[EdgeMarc 4808. Software version: 16.1.1 or higher SW version](https://ribboncommunications.com/products/service-provider-products/cloud-and-edge/session-border-controllers/session-border-controllers-edge-appliances)|&#10004;|
|[Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions)|[EdgeMarc 6000. Software version: 16.1.1 or higher SW version](https://ribboncommunications.com/products/service-provider-products/cloud-and-edge/session-border-controllers/session-border-controllers-edge-appliances)|&#10004;|
|[TE-SYSTEMS](https://www.anynode.de/anynode-and-microsoft-teams/)|anynode with Grandstream GXW42xx (V1.0.7.10)|&#10004;|

Note the certification granted to a major version. That means that firmware with any number in the SBC firmware following the major version is supported.

To provide feedback about Teams, such as ideas for new features, see the [Microsoft feedback portal](https://feedbackportal.microsoft.com/).

> [!NOTE]
> Media re-targeting is not supported. During a Direct Routing call, if the SBC sends a new media IP to Teams Direct Routing, although it's negotiated in the SIP signaling, the media is never sent to the new IP address from Teams Direct Routing.

## See also

- [Plan Direct Routing](direct-routing-plan.md)
- [Configure Direct Routing](direct-routing-configure.md)
- [Learn more about Direct Routing](https://aka.ms/dr)
