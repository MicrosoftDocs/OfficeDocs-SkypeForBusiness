---
title: "Configure XMPP gateway access policies and certificates"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol (XMPP). An XMPP configuration allows users access to XMPP domain users by:"
---

# Configure XMPP gateway access policies and certificates
[]
XMPP federation defines an external deployment based on the eXtensible Messaging and Presence Protocol (XMPP). An XMPP configuration allows Lync users access to XMPP domain users by:
  
- IM and Presence - person to person only
    
- Creation of XMPP federated contacts in the Lync client
    
When you configure policies for support of extensible messaging and presence protocol (XMPP) federated partners, the policies apply to users of XMPP federated domains, but not to users of session initiation protocol (SIP) instant messaging (IM) service providers, or SIP federated domains. You configure an XMPP Federated Partner for each XMPP federated domain that you want to allow your users to add contacts and communicate with. Once the policies are in place, you need to configure the XMPP Gateway certificates. 
  
> [!NOTE]
> To begin the XMPP Gateway migration, you need to deploy the Skype for Business Server 2019 XMPP Gateway, and configure access policies to enable users for Skype for Business Server 2019 XMPP Gateway. All users must be moved to the Skype for Business Server 2019 deployment before you perform these steps. For details, see [Configure XMPP gateway on Skype for Business Server 2019](configure-xmpp-gateway.md). 
  
### Configure an External Access Policy to Enable Users for Skype for Business Server 2019 XMPP Gateway

1. Open Lync Server Control Panel.
    
2. In the left navigation bar, click **Federation and External Access**, and then click **External Access Policy**.
    
3. Click **New** and then click **User policy**.
    
4. Enter a name for the external access user policy.
    
5. Provide a description for external access user policy.
    
6. Select **Enable communications with federated users**.
    
7. Select **Enable communications with XMPP federated users**.
    
8. Click **Commit** to save your changes to the site or user policy. 
    

