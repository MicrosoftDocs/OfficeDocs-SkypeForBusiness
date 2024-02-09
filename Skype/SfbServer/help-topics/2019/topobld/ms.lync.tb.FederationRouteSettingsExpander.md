---
ms.date: 03/17/2018
title: "Federation Route Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.FederationRouteSettingsExpander
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 22aa11b8-80ba-4c6a-9396-d11166903066
ROBOTS: NOINDEX, NOFOLLOW
description: "To set a site federation route assignment, you must first have federation enabled on the Microsoft Edge Server or Microsoft Edge Server pool. If federation isn't enabled on the Edge Server or pool, the federation route assignment settings for the site won't be available for modification."
---

# Federation Route Settings Expander
 
To set a site federation route assignment, you must first have federation enabled on the Microsoft Edge Server or Microsoft Edge Server pool. If federation isn't enabled on the Microsoft Edge Server or pool, the federation route assignment settings for the site won't be available for modification.

If the federation setting at the Edge Server or pool has been configured, you can configure the following options: 
  
- **Allow federation route assignments to all sites** This setting affects all sites. Be sure that the setting that you configure at this site is appropriate for all sites.
    
- **Enable SIP federation** Select this option to enable a SIP federation route, and then select a Director or Edge pool as the federation route.
    
- **Enable XMPP federation** Select this option to enable an XMPP federation route, and then select a Director or Edge pool as the federation route.
- 
  > [!NOTE]
  > XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. For more information, see [Migrating XMPP federation](../../../../SfBServer2019/migration/migrating-xmpp-federation.md).
    


