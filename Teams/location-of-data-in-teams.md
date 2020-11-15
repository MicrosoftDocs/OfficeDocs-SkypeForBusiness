---
title: Location of data in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
audience: admin
ms.service: msteams
ms.reviewer: anach, kehardy
description: In this article, you will learn about where does the data resides geographically in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Location of data in Microsoft Teams

Data in Teams resides in the geographic region associated with your Microsoft 365 or Office 365 organization. Currently, Teams supports the Australia, Brazil, Canada, France, Germany, India, Japan, Norway, South Africa, South Korea, Switzerland (which includes Liechtenstein), the United Arab Emirates, United Kingdom, Americas, APAC, and EMEA regions. 

> [!IMPORTANT]
> Teams currently offers data residency in Australia, Brazil, Canada, France, Germany, India, Japan, Norway, the United Arab Emirates, United Kingdom, South Korea, South Africa, and Switzerland (which includes Liechtenstein) for new tenants only. A new tenant is defined as any tenant that hasn’t had a single user from the tenant sign in to Team or its admin hasn’t logged in to the Teams Admin Center. Existing tenants from Australia, India, Japan, and South Korea will continue to have their Teams data stored in the APAC region. Existing tenants in Brazil and Canada will continue to have their data stored in the Americas. Existing tenants in France, Germany, Liechtenstein, the United Arab Emirates, the United Kingdom, South Africa, and Switzerland will have their data stored in the EMEA region.

## Where your Teams data is stored

To see which region houses data for your tenant, go to the [Microsoft 365 admin center](https://portal.office.com/adminportal/home) > **Settings** > **Organization profile**. Scroll down to **Data location**.

![Screenshot of data location table including Teams in the admin center](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image5.png)

To review the location where your customer data is stored, go to the [M365 Where your customer data is stored](https://docs.microsoft.com/en-us/microsoft-365/enterprise/o365-data-locations?view=o365-worldwide).

### Core Teams customer data

If your tenant is provisioned in Australia, Brazil, Canada, the European Union, France, Germany, India, Japan, Norway, South Africa, South Korea, Switzerland (which includes Liechtenstein), the United Arab Emirates, the United Kingdom, or the United States, Microsoft stores the following core customer data at rest only within that location. Core customer data is a term that refers to a subset of customer data including:
- Exchange Online mailbox content (email body, calendar entries, and the content of email attachments)
- SharePoint Online site content and the files stored within that site
- Files uploaded to OneDrive for Business
- Teams chat messages, including private messages, channel messages, and images used in chats



### Datacenter locations

The Teams services described in this section store data at rest in the following locations:

|Country or region  |Datacenter location |
|---------|---------|
|Australia   |Sydney and Melbourne        |
|Brazil    |Rio de Janeiro and Campinas   |
|Canada    |Quebec City and Toronto         |
|France    |Marseille and Paris         |
|Germany    |Berlin and Frankfurt      |
|India   |Chennai, Mumbai and Pune        |
|Japan    |Tokyo, Saitama and Osaka         |
|Liechtenstein   |Geneva and Zurich       |
|South Africa     |Johannesburg and Cape Town         |
|South Korea     |Seoul and Busan         |
|Switzerland    |Geneva and Zurich       |
|United Arab Emirates     |Abu Dhabi and Dubai         |
|United Kingdom     | Durham, Cardiff and London        |
|Americas – North, and South (AMER) |Bay, CA and Boydton, VA       |
|Asia Pacific (APAC)  |Singapore and Hong Kong        |
|Europe, Middle East, and Asia (EMEA)   |Dublin and Amsterdam        |

> [!NOTE]
> For Liechtenstein, data is stored at rest in the Switzerland data centers in Geneva and Zurich.

### Data stored with a third-party storage provider

Organizations who allow users to store files with a third-party storage provider are dependent on the storage location of those services and should, therefore, review the location of data at rest for those services separately.

- **Tabs**: Tabs allow users to pin information from apps and services to a channel. Thus, it varies by type of the tab where the data is stored. The tab itself doesn't store any data. For example, a SharePoint tab will store data based on where the SharePoint site collection was provisioned. A tab that includes information from a partner will store the data directly in the system used by the partner and only present a view of it.
- **Other partner apps**: Microsoft doesn't provide any data residency support for apps and services from partners that you might be using within the Teams experience. Review information from those solutions directly to learn about where their data is being stored.

## See also

- [Microsoft Teams launches United Arab Emirates Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-United-Arab-Emirates-Data-Residency/ba-p/980330)

- [Microsoft Teams launches South Korean Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-South-Korea-Data-Residency/ba-p/789171)

- [Microsoft Teams launches South African Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-South-Africa-Data-Residency/ba-p/776611)

- [Microsoft Teams Launches France Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-France-Data-Residency/ba-p/364466)

- [Microsoft Teams launches India Data Residency, other geos coming soon](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-Launches-India-Data-Residency-other-geos-coming/ba-p/154083)

- [Microsoft Teams Launches Australia and Japan Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-Launches-Australia-and-Japan-Data-Residency/ba-p/237827)

- [Microsoft Teams Launches Canada Data Residency, Australia and Japan coming soon](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-Launches-Canada-Data-Residency-Australia-and/ba-p/227178)
