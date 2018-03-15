---
title: "Create or edit hosted SIP federated providers Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0dd6dcb6-a88d-46b8-9c96-b35967309bcd
description: "Hosted provider instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by hosted providers, including the Microsoft Office 365 and Skype for Business Online."
---

# Create or edit hosted SIP federated providers Lync Server 2013
[]
Hosted provider instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by hosted providers, including the Microsoft Office 365 and Skype for Business Online.
  
Each hosted provider is configured with the provider's Edge server fully qualified domain name, and the default verification level **Allow users to communicate only with people on their Contacts list who use this provider**.
  
Use the following procedure to create or edit Hosted providers:
  
### To create or edit hosted providers

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Federation and External Access**, and then click **SIP Federated Providers**.
    
4. If you need to create a new Hosted provider, click **New** and then click **Hosted provider**.
    
5. If you need to edit an entry from the list of Hosted providers, select a hosted provider, click **Edit**, then click **Show details**.
    
6. On the **Edit SIP Federated Provider** page, you can type or edit the following settings: 
    
  - **Enable communications with this provider** Selecting this setting enables communications with this provider's users. 
    
  - **Provider name:** A required property, type the name of the provider as it will be reflected in the listing of SIP Federated Providers. 
    
  - **Access Edge service (FQDN):** A required property, type the fully qualified domain name of the Access Edge service of the hosted provider that you are configuring. This information should be provided by the hosted provider, and should only be changed if the hosted provider makes a change to the FQDN of the Access Edge service at the hosted provider. 
    
  - **Default verification level:** The default setting, **Allow users to communicate with people on their Contacts list who use this provider** will limit communication to contacts that you have accepted and are in your contact list. 
    
    Selecting **Allow users to communicate with everyone using this provider** removes the restriction that you must have received and accepted a contact invite. This setting does not limit who can contact you from the hosted provider's network. 
    
7. When you are done configuring the settings, click **Commit** to save, or click **Cancel** to discard your changes. 
    
## See also

#### 

[Configure policies to control public user access in Lync Server 2013](configure-policies-to-control-public-user-access.md)
  
[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md)

