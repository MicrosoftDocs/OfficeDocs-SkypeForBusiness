---
title: "Lync Server Site Settings Expander"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.SiteSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 940bd9c0-bfcf-4d15-a5c1-a09f1cd692b6
ROBOTS: NOINDEX, NOFOLLOW
description: "To edit the properties of an existing site, do the following:"
---

# Lync Server Site Settings Expander

To edit the properties of an existing site, do the following:



## Site properties

In site properties, you can change or modify the site Name (required), Description (optional), City (optional), State/Province (optional), and the Country/Region Code (optional).

For details about site properties, see [Add Branch Sites to Your Topology](https://technet.microsoft.com/library/b9c35fb0-0081-4aeb-8f95-ac2fcc6c3335.aspx).

## Federation Route properties

To set a site federation route assignment, you must first have federation enabled on an Edge Server or an Edge Server pool. If federation is not enabled on an Edge Server or pool, the federation route assignment settings for the site will not be available for modification.

If the federation setting at the Edge Server or pool has been configured, select **Enable** at the site level. Then select an Edge or a Director from the drop-down list to set as the federation route.

> [!CAUTION]
> This setting will affect all sites. Be sure that the setting that you are configuring at this site is appropriate for all sites.

## See also

For details, see [Topologies for External User Access](https://technet.microsoft.com/library/25697446-b045-4d12-9b1c-47f694b4f224.aspx).


