---
title: Location of data in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: reference
audience: admin
ms.service: msteams
ms.reviewer: anach
description: Learn about where data is stored in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Location of data in Microsoft Teams

Data in Teams resides in the geographic region associated with your Office 365 tenant. Currently, Teams supports the Australia, Canada, France, India, Japan, United Kingdom, South Korea, South Africa, Americas, APAC, and EMEA regions.

> [!IMPORTANT]
> Teams currently offers data residency in Australia, Canada, France, India, Japan, United Kingdom, South Korea, and South Africa for new tenants only.
> A new tenant is defined as any tenant that hasn’t had a single user from the tenant sign in to Teams. Existing tenants from Australia, India, Japan, and South Korea will continue to have their Teams data stored in the APAC region. Existing tenants in Canada will continue to have their data stored in the Americas. Existing tenants in France, United Kingdom, and South Africa will have their data stored in the EMEA region.

To see which region houses data for your tenant, go to the [Microsoft 365 admin center](https://portal.office.com/adminportal/home) > **Settings** > **Organization profile**. Scroll down to **Data location**.

+++++++++++++++++++++++

## Where your Teams data is stored

Your Teams data is stored differently depending on the content type. For an in-depth discussion, watch the [Ignite breakout session on Microsoft Teams architecture](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071).

**Core Teams customer data**: If you provision your tenant in Australia, Canada, the European Union, France, India, Japan, South Africa, South Korea, the United Kingdom, or the United States, Microsoft stores the following customer data at rest only within that location: (1) Teams chats, team and channel conversations, images, voicemail messages, and contacts, (2) SharePoint Online site content and the files stored within that site, and (3) files uploaded to OneDrive for Business.

- **Chat, channel messages, team structure**: Every team in Teams is backed by an Office 365 Group and its SharePoint site and Exchange mailbox. Private chats (including group chats), messages sent as part of a conversation in a channel, and the structure of teams and channels are stored in a chat service running in Azure. The data is also stored in a hidden folder in the user and group mailboxes to enable Information Protection features.
- **Voicemail and contacts**: Voicemails are stored in Exchange. Contacts are stored in Exchange-based cloud data store. Exchange and the Exchange-based cloud store already provide data residency in each of the worldwide datacenter geos. For all teams,  voicemail and contacts are stored in-country for Australia, Canada, France, South Africa, India, Japan, UK, South Korea, and the US. For all other countries, files are stored in the US, Europe, or Asia-Pacific location based on tenant affinity.
- **Images and Media**: Media used in chats (except for Giphy GIFs which aren't stored but are a reference link to the original Giphy service URL, Giphy is a non-Microsoft service) is stored in an Azure-based media service that is deployed to the same locations as the chat service.
- **Files**: Files (including OneNote and Wiki) that somebody shares in a channel are stored in the team’s SharePoint site. Files shared in a private chat or a chat during a meeting or call are uploaded and stored in the OneDrive for the Business account of the user who shares the file. Exchange, SharePoint and OneDrive already provide data residency in each of the worldwide datacenter geos. So, for existing customers, all files, OneNote notebooks, Teams wiki content, and mailboxes that are part of the Teams experience are already stored in the location based on your tenant affinity. Files are stored in-country for Australia, Canada, France, South Africa, India, Japan, UK, and South Korea. For all other countries, files are stored in the US, Europe, or Asia Pacific location based on tenant affinity.

The Teams services described above store data at rest in the following locations:

- South Africa datacenters in Johannesburg and Cape Town
- France: datacenters in Marseille and Paris
- Australia: datacenters in New South Wales and Victoria
- Japan: datacenters in Tokyo(Saitama) and Osaka
- Asia Pacific (APAC): datacenters in Singapore and Hong Kong
- Europe, Middle East, and Asia (EMEA): datacenters in Dublin and Amsterdam
- Americas – North, and South (AMER): datacenters in Bay, CA and Boydton, VA
- United Kingdom: datacenters in Cardiff and London
- India: datacenters in Chennai and Pune
- Canada: datacenters in Quebec City and Toronto
- South Korea: datacenters in Seoul and Busan

Note that customers who allow users to store files with a third-party storage provider are dependent on the storage location of those services and should, therefore, review the location of data at rest for those services separately.

- **Tabs**: Tabs allow users to pin information from apps and services to a channel. Thus, it varies by type of the tab where the data is stored. The tab itself doesn't store any data. For example, a SharePoint tab will store data based on where the SharePoint site collection was provisioned. A tab that includes information from a partner will store the data directly in the system used by the partner and only present a view of it.
- **Other partner apps**: Microsoft doesn't provide any data residency support for apps and services from partners that you might be using within the Teams experience. Review information from those solutions directly to learn about where their data is being stored.

![Screenshot of data location table including Teams in the admin center](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image5.png)

## See also

- [Microsoft Teams launches South African Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-South-Africa-Data-Residency/ba-p/776611)

- [Microsoft Teams launches South Korean Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-South-Korea-Data-Residency/ba-p/789171)

- [Microsoft Teams launches India Data Residency, other geos coming soon](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-Launches-India-Data-Residency-other-geos-coming/ba-p/154083)

- [Microsoft Teams Launches Canada Data Residency, Australia and Japan coming soon](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-Launches-Canada-Data-Residency-Australia-and/ba-p/227178)

- [Microsoft Teams Launches Australia and Japan Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-Launches-Australia-and-Japan-Data-Residency/ba-p/237827)

- [Microsoft Teams Launches France Data Residency](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Microsoft-Teams-launches-France-Data-Residency/ba-p/364466)
