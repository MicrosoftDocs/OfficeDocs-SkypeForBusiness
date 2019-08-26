---
title: "Change simple URLs after migration"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Skype for Business Server supports simple URLs."
---

# Change simple URLs after migration

Skype for Business Server supports three simple URLs:
  
- **Meet** is used as the base URL for all conferences in the site or organization. With the Meet simple URL, links to join meetings are easy to comprehend, and easy to communicate and distribute. 
    
- **Dial-in** enables access to the Dial-in Conferencing Settings webpage. The Dial-in simple URL is included in all meeting invitations so that users who want to dial in to the meeting can access the necessary phone number and PIN information. 
    
- **Admin** enables quick access to the Skype for Business Server Control Panel. The Admin simple URL is internal to your organization. 
    
After migrating to Skype for Business Server, you must be aware of how the change impacts your DNS records and certificates for simple URLs. If the legacy Skype for Business Server Director remains in use in the topology, no changes to your simple URLs are required. If the Skype for Business Server Director is removed from the topology after migration, the simple URL DNS records must be updated to point to one of the Skype for Business Server pools. Whenever you change a simple URL name, however, you must run Enable-CsComputer on each Director and Front End Server to register the change.

## To update the Meet simple URL

1. In Topology Builder, right-click the top node **Skype for Business Server**, and then click **Edit Properties**.
    
2. Select **Simple URLs** in the left pane, then below **Meeting URLs:** select the Meet URL and then click **Edit URL**.
    
3. Update the URL to the value you want, and then click **OK** to save the edited URL. 
    
## To update the Admin simple URL

1. In Topology Builder, right-click the top node **Skype for Business Server**, and then click **Edit Properties**.
    
2. Select **Simple URLs** in the left pane, then below **Administrative access URL** box, enter the simple URL you want for administrative access to Skype for Business Server Control Panel, and then click **OK**.
    
   > [!TIP]
   > We recommend using the simplest possible URL for the Admin URL. The simplest option is https://admin.<em>\<domain\></em>. 
  
## See also

[DNS requirements for simple URLs in Skype for Business Server](../../SfbServer/plan-your-deployment/network-requirements/simple-urls.md)
