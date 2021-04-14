---
title: Teams experience in a Microsoft 365 Multi-Geo-enabled environment
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: snigdhav
audience: admin
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - SPO_Content
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
description: In this article, you'll learn about using Teams in a Microsoft 365 Multi-Geo-enabled environment.
---

# Teams experience in a Microsoft 365 Multi-Geo-enabled tenancy

Microsoft Teams is group chat software, the hub for teamwork in Microsoft 365 and Office 365. It's powered by the Microsoft 365 Groups service along with SharePoint Online and OneDrive for Business for its files experience. In a OneDrive for Business/SharePoint Online Multi-Geo tenancy, in which the tenant is extended to many geographic locations such as North America, Europe, and Australia, the underlying files experience is Multi-Geo-aware, so the Teams experience with file collaboration is also Multi-Geo-aware. This functionality is a key leading-edge capability for Teams to surface files that are hosted across multiple Geos in its native files experience. This also includes OneNote and Wiki files.

For example, in a Contoso tenancy with Europe as a satellite Geo and North America as the central Geo, a European satellite user will see their OneDrive files under the **Files** tab in left pane, although the files are hosted in the Europe data location and the United States is the tenant’s central location. Also, the user can access the most recently used files under the **Recent** view blade. Recent files may include files shared from users in other geo locations. 

A given Team’s SharePoint site is also Multi-Geo-aware. That is, if a European satellite user is creating a Team, the corresponding SharePoint site will be created in the Europe location. The files that are associated with that Team will be kept at rest in that location. Any subsequent experiences, such as uploading a new file or editing the file, will be stored in that European location, keeping the promise of data residency for those files.

Because a Multi-Geo tenancy is a single global tenant, during @ mentions satellite users will be able to see their colleagues from across the globe, no matter where they are.

Conversations in chats, channels messages, and meeting IM notes/chats within the Teams experience aren't Multi-Geo-aware and are all kept only inside the central location of the tenant. Typically, chat conversations aren’t applied to data residency needs. For more information, see [Location of data in Microsoft Teams](location-of-data-in-teams.md).

Multi-Geo support for teams is on the [Microsoft 365 roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=70783).

For more info about Multi-Geo, refer to the [Microsoft Multi-Geo capabilities page](https://aka.ms/multi-geo).
