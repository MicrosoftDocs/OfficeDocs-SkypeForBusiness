---
title: Teams experience in an Office 365 ODB and SPO Multi-Geo-enabled tenancy
author: tonysmit
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: snigdhav
description: 
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto: Learn how Microsoft Teams works with the Multi-Geo Capabilities in Office 365.
- Microsoft Teams
---

# Teams experience in an Office 365 ODB and SPO Multi-Geo-enabled tenancy

Microsoft Teams is group chat software, the hub for teamwork in Office 365. It is powered by the Office 365 Groups service along with SharePoint and OneDrive for its files experience. In a ODB/SPO Multi-Geo tenancy, in which the tenant is extended to many geo locations such as North America, Europe, and Australia, the underlying files experience is Multi-Geo aware, so the Teams experience with file collaboration is also Multi-Geo aware. This is a key leading-edge capability for Teams to surface files hosted across multiple geos in its native files experience.

For example, in a Contoso tenancy with Europe as a satellite geo and North America as the central geo, a European satellite user will see his or her OneDrive files under the Files tab in left pane, although the files are hosted in the Europe data location and the United States is the tenant’s central location. Also, the user can access the most recently used files under the Recent view blade. Recent files may include files shared with the user from other geo users and might be mastered in other geo locations that the tenant is extended to. See the screenshot below for an example.

 SCREENSHOT

A given Team’s group site is also multi-geo-aware. That is, if a European satellite user is creating a Team, the corresponding Groups site will be created in the Europe location and the files associated with that Team group will be kept at rest in that location. Any subsequent experiences, such as uploading a new file or editing the file, will be targeted to that European location, keeping the promise of data residency for those files. This is all made possible by the underlying foundation Office 365 Groups becoming multi-geo aware.

  SCREENSHOT

Because a multi-geo tenancy is a single global tenant, during @ mentions satellite users will be able to see their colleagues from across the globe, no matter where they reside. See the screenshot for an example.

 SCREENSHOT 

Note that conversations in chats and meeting IM notes within the Teams experience are not multi-geo aware and are all kept only inside the central location of the tenant. Typically, chat conversations aren’t treated toward data residency needs.

For more information about Office 365 Multi-Geo, refer to the [Microsoft Multi-Geo capabilities page](https://aka.ms/multi-geo).
