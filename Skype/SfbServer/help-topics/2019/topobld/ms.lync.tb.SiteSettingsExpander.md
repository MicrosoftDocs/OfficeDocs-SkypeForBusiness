---
ms.date: 03/17/2018
title: "Lync Server Site Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.SiteSettingsExpander
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 940bd9c0-bfcf-4d15-a5c1-a09f1cd692b6
ROBOTS: NOINDEX, NOFOLLOW
description: "To edit the properties of an existing site, do the following:"
---

# Lync Server Site Settings Expander

To edit the properties of an existing site, do the following:



## Site properties

In site properties, you can change or modify the site Name (required), Description (optional), City (optional), State/Province (optional), and the Country/Region Code (optional).

For details about site properties, see [Add Branch Sites to Your Topology](/previous-versions/office/lync-server-2013/lync-server-2013-add-branch-sites-to-your-topology).

## Federation Route properties

To set a site federation route assignment, you must first have federation enabled on a Microsoft Edge Server or a Microsoft Edge Server pool. If federation isn't enabled on a Microsoft Edge Server or pool, the federation route assignment settings for the site aren't available for modification.

If the federation setting at the Microsoft Edge Server or pool is configured, select **Enable** at the site level. Then select a Microsoft Edge or a Director from the drop-down list to set as the federation route.

> [!CAUTION]
> This setting will affect all sites. Be sure that the setting that you are configuring at this site is appropriate for all sites.

## See also

For details, see [Topologies for External User Access](/previous-versions/office/lync-server-2013/lync-server-2013-scenarios-for-external-user-access).
