---
title: "Skype Meetings App minimum network requirements"
ms.author: serdars
author: SerdarSoysal
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 6/4/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: d9666787-e72b-41e1-ba37-aec5fb849a10
description: "Summary: Information for organizations who don't use Microsoft 365 or Office 365 and need to access meetings hosted by organizations that do."
---

# Skype Meetings App minimum network requirements

**Summary:** Information for organizations who don't use Microsoft 365 or Office 365 and need to access meetings hosted by organizations that do. This article is not intended for Office 365 or Microsoft 365 end-users.

Users of the Skype Meetings App in organizations that don't use Microsoft 365 or Office 365 might need to attend meetings hosted in Skype for Business Online. To attend these meetings, their network administrators need to allow the following FQDNs, IP addresses, and ports through their firewall.

## Requirements for Skype Meetings App connectivity

The information listed here is a subset of the information in [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges). That topic is much more in-depth, and will always be current.

|App|Destination FQDNs|IP Addresses|Ports|
|---|---------|---------|---------|
|**Skype Meetings App**|\*.lync.com <br/>\*.infra.lync.com<br/>\*.pipe.aria.microsoft.com<br/>\*.sfbassets.com<br/>\*.msecnd.net<br/>\*broadcast<span></span>.officeapps.live.com <br/>\*powerpoint<span></span>.officeapps.live.com <br/>\*.office.live.com<br/>\*.cdn.office.net<br/>*.s-microsoft.com<br/>|These IP addresses are frequently updated. See [Skype for Business and Microsoft Teams IP ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) as well as [Office IP Ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges)|TCP: 80 & 443<br/>UDP: 3478-3481|
|**Teams**|\*<span></span>.microsoft.com <br/>\*<span></span>.skype.com|These IP addresses are frequently updated. See [Skype for Business and Microsoft Teams IP ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) as well as [Office IP Ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges)|TCP: 443 <br/> UDP: 3478-3481|

## See also
<a name="BKMK_Conferencing"> </a>

[Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md)

[Deploy Web downloadable clients in Skype for Business Server](../../deploy/deploy-clients/deploy-web-downloadable-clients.md)

[Supported platforms for Skype Meetings App](https://support.office.com/client/results?Shownav=true&amp;lcid=1033&amp;ns=SKFBWA&amp;version=15&amp;omkt=en-US&amp;ver=15&amp;HelpID=SfBWebApp4001)
