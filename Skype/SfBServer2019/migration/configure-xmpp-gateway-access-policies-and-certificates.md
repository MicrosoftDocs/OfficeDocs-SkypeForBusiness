---
title: "Configure XMPP gateway access policies and certificates"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol (XMPP). An XMPP configuration allows users access to XMPP domain users by:"
---

# Configure XMPP gateway access policies and certificates

XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol (XMPP). An XMPP configuration allows users access to XMPP domain users by:
  
- IM and Presence - person to person only
    
- Creation of XMPP federated contacts in the Skype for Business client
    
When you configure policies for support of XMPP federated partners, the policies apply to users of XMPP federated domains, but not to users of session initiation protocol (SIP) instant messaging (IM) service providers, or SIP federated domains. You configure an XMPP federated partner for each XMPP federated domain that you want to allow your users to add contacts and communicate with. Once the policies are in place, you need to configure the XMPP Gateway certificates. 
  
> [!NOTE]
> XMPP functionality is deprecated in Skype for Business Server 2019, but can be continued in a legacy server in coexistence with Skype for Business Server 2019. Make sure you have already deployed the legacy server (Skype for Business Server 2015 / Lync Server 2013) XMPP Gateway, and configured the access policies to enable users for legacy XMPP Gateway. For details, see [Migrating XMPP Federation](migrating-xmpp-federation.md). 
  
### Configure an External Access Policy to Enable Users for legacy XMPP Gateway

1. Open the legacy Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Federation and External Access**, and then click **External Access Policy**.
    
3. Click **New**, and then click **User policy**.
    
4. Enter a name for the external access user policy.
    
5. Provide a description for external access user policy.
    
6. Select **Enable communications with federated users**.
    
7. Select **Enable communications with XMPP federated users**.
    
8. Click **Commit** to save your changes to the site or user policy. 
    

