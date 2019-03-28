---
title: Teams experience in an Office 365 OneDrive and SharePoint Online Multi-Geo-enabled tenancy
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: snigdhav
description: Learn about using Teams in an Office 365 OneDrive and SharePoint Online Multi-Geo-enabled tenancy.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Teams experience in an Office 365 OneDrive and SharePoint Online Multi-Geo-enabled tenancy
===========================================

Microsoft Teams is group chat software, the hub for teamwork in Office 365. It is powered by the Office 365 Groups service along with SharePoint Online and OneDrive for Business for its files experience. In a OneDrive for Business/SharePoint Online Multi-Geo tenancy, in which the tenant is extended to many geographic locations such as North America, Europe, and Australia, the underlying files experience is Multi-Geo aware, so the Teams experience with file collaboration is also Multi-Geo aware. This is a key leading-edge capability for Teams to surface files hosted across multiple Geos in its native files experience.

For example, in a Contoso tenancy with Europe as a satellite Geo and North America as the central Geo, a European satellite user will see his or her OneDrive files under the Files tab in left pane, although the files are hosted in the Europe data location and the United States is the tenant’s central location. Also, the user can access the most recently used files under the Recent view blade. Recent files may include files shared with the user from users in other Geos and might be mastered in other Geo locations that the tenant is extended to. 

A given Team’s group site is also Multi-Geo aware. That is, if a European satellite user is creating a Team, the corresponding Groups site will be created in the Europe location and the files associated with that Team group will be kept at rest in that location. Any subsequent experiences, such as uploading a new file or editing the file, will be targeted to that European location, keeping the promise of data residency for those files. This is all made possible by the underlying foundation Office 365 Groups becoming Multi-Geo aware.

Because a Multi-Geo tenancy is a single global tenant, during @ mentions satellite users will be able to see their colleagues from across the globe, no matter where they reside. 

Note that conversations in chats and meeting IM notes within the Teams experience are not Multi-Geo aware and are all kept only inside the central location of the tenant. Typically, chat conversations aren’t applied to data residency needs.

For more information about Office 365 Multi-Geo, refer to the [Microsoft Multi-Geo capabilities page](https://aka.ms/multi-geo).