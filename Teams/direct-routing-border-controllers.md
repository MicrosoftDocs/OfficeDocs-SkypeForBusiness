---
title: "Session Border Controllers certified for Direct Routing"
ms.author: crowe
ms.reviewer: FilippSe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
hideEdit: true
f1.keywords:
- NOCSH
description: Admin can learn about which Session Border Controllers (SBCs) have been certified for Direct Routing.
ms.custom: seo-marvel-apr2020
---

# List of Session Border Controllers certified for Direct Routing

Microsoft partners with selected Session Border Controllers (SBC) vendors to certify that their SBCs work with Direct Routing.

Microsoft works with each vendor to:

- Jointly work on the SIP interconnection protocols.
- Perform intense tests using a third-party lab. Only devices that pass the tests are certified.
- Run daily tests with all certified devices in production and pre-production environments. Validating the devices in pre-production environments guarantees that new versions of Direct Routing code in the cloud will work with certified SBCs.
- Establish a joint support process with the SBC vendors.

  > [!NOTE]
  > Microsoft only supports Phone System if a certified device or devices are connected through Direct Routing. Microsoft reserves the right to reject support cases where a non-certified device is connected to the Phone System through Direct Routing. If Microsoft determines that a customer’s Direct Routing issue is with a vendor’s SBC device, the customer will need to engage the SBC vendor for support.

The tables that follow list devices certified for Direct Routing. (For information about which SBC vendors support Local Media Optimization, see [Configure Local Media Optimization for Direct Routing](direct-routing-media-optimization-configure.md).)

[Learn more about Direct Routing](https://aka.ms/dr).
If you have any questions about the SBC certification program for Direct Routing, please contact drsbccertification@microsoft.com.
<br/>

#### [Certified SBC vendors A-M](#tab/CertifiedSBCvendorsA-M/)

#### [Atos](#tab/Atos/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Atos](https://unify.com/en/solutions/voice-platforms/session-border-controller)|    Atos Unify OpenScape Session Border Controller   |     &#10004;     |          |      V10R1.2       |     |    |

#### [**AudioCodes**](#tab/AudioCode/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
| [AudioCodes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams) |   Mediant 500 SBC   |     &#10004;     |   &#10004;    |  Supported 7.20A.250 (Recommended 7.20A.258)   | <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li> [Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul> |  &#10004;  |
|                                                                                                                     |   Mediant 800 SBC   |     &#10004;     |   &#10004;     |  Supported 7.20A.250 (Recommended 7.20A.258)   | <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>  |  &#10004;  |
|                                                                                                                     |  Mediant 2600 SBC   |     &#10004;     |   &#10004;    |  Supported 7.20A.250 (Recommended 7.20A.258)   |   <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>  |  &#10004;  |
|                                                                                                                     |  Mediant 4000 SBC   |     &#10004;     |   &#10004;     |  Supported 7.20A.250 (Recommended 7.20A.258)   |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>  |  &#10004;  |
|                                                                                                                     | Mediant 1000B  SBC  |     &#10004;     |   Pending     |  Supported 7.20A.250 (Recommended 7.20A.258)  |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>  |  &#10004;  |
|                                                                                                                     | Mediant 9000  SBC  |     &#10004;     |   &#10004;     |  Supported 7.20A.250 (Recommended 7.20A.258)   | <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>    |  &#10004;  |
|                                                                                                                     | Virtual Edition SBC |     &#10004;     |   &#10004;     |  Supported 7.20A.250 (Recommended 7.20A.258) |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>   |  &#10004;  |

#### [Avaya](#tab/Avaya/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Avaya](https://support.avaya.com/products/P0997/avaya-session-border-controller-for-enterprise/8.1.x)|    Avaya Session Border Controller for Enterprise ( ASBCE)    |     &#10004;     |           |       Release 8.1.1       |     |    |

#### [Cataleya](#tab/Cataleya/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Cataleya](https://cataleya.com/orchidplatforms/)|    Orchid Link    |     &#10004;     |           |      3.1        |     |    |

#### [Cisco](#tab/Cisco/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Cisco](https://www.cisco.com/c/en/us/solutions/enterprise/interoperability-portal/networking_solutions_products_genericcontent0900aecd805bd13d.html)                               |     Cisco Unified Border Element (CUBE) for 1000 Series Integrated Services Routers        |     &#10004;   | &#10004; |      Supported IOS XE Amsterdam 17.2.1r (Recommended 17.3.2)         |    <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>    |   |  
|                                   |     Cisco Unified Border Element (CUBE) for 4000 Series Integrated Services Routers        |     &#10004;   | &#10004; |   Supported IOS XE Amsterdam 17.2.1r (Recommended 17.3.2)         |   <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>     |    |  
|                                   |     Cisco Unified Border Element (CUBE) for 1000V Series Cloud Services Router       |     &#10004;   | &#10004; |      Supported IOS XE Amsterdam 17.2.1r (Recommended 17.3.2)         |    <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>    |    |  
|                                 |     Cisco Unified Border Element (CUBE) for 1000 Series Aggregation Services Routers      |     &#10004;   | &#10004; |      Supported IOS XE Amsterdam 17.2.1r (Recommended 17.3.2)         |    <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>    |    |
|                                 |     Cisco Unified Border Element (CUBE) for Catalyst 8000 Edge Platforms      |     &#10004;   | &#10004; |      IOS XE Amsterdam 17.3.2      |    <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>    |    |

#### [Ericsson](#tab/Ericsson/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Ericsson](https://www.ericsson.com/en/portfolio/digital-services/cloud-communication/enterprise-communication/business-communication-services-and-enablers/sip-trunking)|    vSBC 2.16     |     &#10004;     |           |              |     |    |

#### [Italtel](#tab/Italtel/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Italtel](https://www.italtel.com/italtel-provides-direct-routing-sbc-for-microsoft-teams/)|    NetMatch-S CI     |     &#10004;     |           |       Supported 5.0  (Recommended 5.1)     |     |    |

#### [Metaswitch](#tab/Metaswitch/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Metaswitch](https://www.metaswitch.com/products/core-network/perimeta-sbc)                               |     Perimeta SBC        |     &#10004;   |  |      4.7      |     |    |  

* * *

### Direct Routing tables N-Z

#### [Nokia](#tab/Nokia/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Nokia](https://documentation.nokia.com/aces/cgi-bin/chk_access.cgi/3TB30222GBAAACZZA.zip)|    Nokia Session Border Controller    |     &#10004;     |           |       19.5 (1908)       |     |    |
|                     |    Nokia Session Border Controller    |     &#10004;     |           |       20.8       |      <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>       |    |

#### [Oracle](#tab/Oracle/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Oracle](https://www.oracle.com/industries/communications/enterprise-session-border-controller/microsoft.html)                      |    AP 1100      |    &#10004;     |    &#10004;    |   8.3.0.0.1 |   <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>   |  &#10004;  |
|    |    AP 3900           |    &#10004;     |    &#10004;   |   8.3.0.0.1  |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>  |  &#10004;  |
|                                                                                                                    |      AP 4600         |    &#10004;   |    &#10004;     |     8.3.0.0.1  |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>  |  &#10004;  |
|                                                                                                                    |      AP 6300         |    &#10004;   |    &#10004;     |     8.3.0.0.1  |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> </ul>   |  &#10004;  |
|                                                                                                                   |      AP 6350           |    &#10004;   |    &#10004;    |     8.3.0.0.1  |   <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>  |  &#10004;  |

#### [**Ribbon Communications**](#tab/RibbonCommunications/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|  [Ribbon Communications](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-skype-business)  |      SBC 5100/5110       |     &#10004;     |   &#10004;    |       Supported 8.2 and 7.2 (Recommended 9.2)       | <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul> |    |
|                                                                                                                     |      SBC 5200/5210       |     &#10004;     |  &#10004;    |       Supported 8.2 and 7.2 (Recommended 9.2)       |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li></ul> |    |
|                                                                                                                     |      SBC 5400       |     &#10004;     |   &#10004;   |       Supported 8.2 and 7.2 (Recommended 9.2)       |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li><li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li></ul>  ||
|                                                                                                                     |      SBC 7000       |     &#10004;     |   &#10004;    |       Supported 8.2 and 7.2 (Recommended 9.2)       |   <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li></ul> |  |
|                                                                                                                     |       SBC SWe       |     &#10004;     |   &#10004;   |       Supported 8.2 and 7.2 (Recommended 9.2)          |   <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul> |    |
|                                                                                                                     |      SBC 1000       |     &#10004;     |   &#10004;    |      8.x or 9.x     |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li> [Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> </ul>   |  &#10004;   |
|                                                                                                                     |      SBC 2000       |     &#10004;     |   &#10004;   |     8.x or 9.x     |  <ul> <li>[Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li> [Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> </ul>   |     &#10004;     |
|                                                                                                                     |    SBC SWe Lite     |     &#10004;     |  &#10004;    |      8.x or 9.x    |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li> [Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> </ul>    |     &#10004;     |
| | EdgeMarc Series |  &#10004; | | 15.6.1 |

#### [Sansay Inc](#tab/SansayInc/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|[Sansay Inc.](https://www.sansay.com/solutions/microsoft-teams/)|    vmVSXi   |     &#10004;     |     &#10004;     |      10.5.1.354-vm-S-x64      |     |    |

#### [TE-SYSTEMS](#tab/TE-SYSTEMS/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|[TE-SYSTEMS](https://www.anynode.de/anynode-and-microsoft-teams/)                               |     anynode         |     &#10004;   |  &#10004;   |      Supported 3.20 (Recommended 4.0)        |  <ul> <li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li> <li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>   |  &#10004;   |  
|                     [TE-SYSTEMS](https://www.anynode.de/anynode-and-microsoft-teams/)                               |     anynode         |     &#10004;   |  &#10004;   |      Supported 3.20 (Recommended 4.0)        |  <ul><li> [Bandwidth Dynamic Location Routing](https://www.bandwidth.com/partners/microsoft-teams-direct-routing) </li><li>[Intrado Emergency Routing Service (ERS)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/) </li> <li>[Intrado Emergency Gateway (EGW)](https://www.west.com/safety-services/enterprise-e911-solutions/microsoft-teams-e911-solutions/)</li>  </ul>   |  &#10004;   |

#### [Trinkets](#tab/Thinktel/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [Thinktel](https://www.thinktel.ca/services/think-365/think-365-overview/)                      |    Think 365 SBC    |     &#10004;     |           |       1.4       |     |    |

#### [ULTATEL](#tab/ULTATEL/)

|                                                       Vendor                                                        |       Product       | Non-media bypass | Media bypass | Software version | Validated with E911 providers | ELIN capable
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|--------------|------------------|-----------------|------------------|
|                     [ULTATEL](https://www.ultatel.com/services/direct-routing-teams-sbc)|    Teams SBC    |     &#10004;     |     &#10004;      |      1.6        |     |    |

* * *

### Direct routing and analog devices interoperability

The following table lists devices that are verified for interoperability between Direct Routing and Analog Devices.

|                                                       Vendor                                                        |       Product       | Verified
|---------------------------------------------------------------------------------------------------------------------|---------------------|------------------|
| [AudioCodes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams) |   [ATA-1](https://www.audiocodes.com/media/2373/mp-1xx-and-mp-124-datasheet.pdf)   |     &#10004;     |
| [AudioCodes](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams) |   [ATA-2](https://www.audiocodes.com/media/2399/mediapack-20x-mp-20x-analog-telephone-adapters-datasheet.pdf)   |     &#10004;     |
| [Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions) |   [SBC 1000. Software version: 8.1.1 (build 527)](https://support.sonus.net/display/UXDOC81/Connect+SBC+Edge+to+Microsoft+Teams+Direct+Routing+to+Support+Analog+Devices)   |     &#10004;     |
| [Ribbon](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions) |   [SBC 2000. Software version: 8.1.1 (build 527)](https://support.sonus.net/display/UXDOC81/Connect+SBC+Edge+to+Microsoft+Teams+Direct+Routing+to+Support+Analog+Devices)   |     &#10004;     |
| [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html) |   AP1100 Software Version 8.3.0.1.2 |     &#10004;     |
  | [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html) |  AP3900 Software Version 8.3.0.1.2|     &#10004;     |
  | [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html) |  AP4600 Software Version 8.3.0.1.2|     &#10004;     |
  | [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html) |  AP6300 Software Version 8.3.0.1.2|     &#10004;     |
  | [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html) |  AP6350 Software Version 8.3.0.1.2|     &#10004;     |
  | [Oracle](https://www.oracle.com/technical-resources/documentation/acme-packet.html) |  VME Software Version 8.3.0.1.2 |     &#10004;     |
  | [TE-SYSTEMS](https://www.anynode.de/anynode-and-microsoft-teams/) |  anynode with Grandstream GXW42xx (V1.0.7.10) |     &#10004;     |
  | [Cisco](https://www.cisco.com/c/en/us/products/collateral/unified-communications/ata-190-series-analog-telephone-adapters/datasheet-c78-740013.html) |  ATA 191 Multiplatform Analog Telephone Adapter |     &#10004;     |
  
To give us product feedback about Teams, such as ideas for new features, see [Uservoice](https://microsoftteams.uservoice.com).
Note the certification granted to a major version. That means that firmware with any number in the SBC firmware following the major version is supported.
