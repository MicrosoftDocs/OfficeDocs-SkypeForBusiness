---
title: "Federation Route Settings Expander"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.FederationRouteSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 22aa11b8-80ba-4c6a-9396-d11166903066
ROBOTS: NOINDEX, NOFOLLOW
description: "To set a site federation route assignment, you must first have federation enabled on the Edge Server or Edge Server pool. If federation is not enabled on the Edge Server or pool, the federation route assignment settings for the site will not be available for modification."
---

# Federation Route Settings Expander
 
To set a site federation route assignment, you must first have federation enabled on the Edge Server or Edge Server pool. If federation is not enabled on the Edge Server or pool, the federation route assignment settings for the site will not be available for modification.

If the federation setting at the Edge Server or pool has been configured, you can configure the following options: 
  
- **Allow federation route assignments to all sites** This setting will affect all sites. Be sure that the setting that you are configuring at this site is appropriate for all sites.
    
- **Enable SIP federation** Select this option to enable a SIP federation route, and then select a Director or Edge pool as the federation route.
    
- **Enable XMPP federation** Select this option to enable an XMPP federation route, and then select a Director or Edge pool as the federation route.
- 
  > [!NOTE]
  > XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information.
    

