---
title: "Verify federation and remote access for external users"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After transitioning the federation route to the Skype for Business Server 2019 Edge Server, you should perform some functional tests to verify that federation performs as expected. Tests for external user access should include each type of external user that your organization supports, including any or all of the following."
---

# Verify federation and remote access for external users

After transitioning the federation route to the Skype for Business Server 2019 Edge Server, you should perform some functional tests to verify that federation performs as expected. Tests for external user access should include each type of external user that your organization supports, including any or all of the following.
  
### Test connectivity of external users and external access

- Users from at least one federated domain, an internal user on Skype for Business Server 2019, and a user on the legacy install. Test instant messaging (IM), presence, audio/video (A/V), and desktop sharing.
    
- Users of each public IM service provider that your organization supports (and for which provisioning has been completed) communicating with a user on Skype for Business Server 2019 and a user on the legacy install. 
    
- Verify that anonymous users are able to join conferences.
    
- A user hosted on the legacy install using remote user access (logging i nto Lync Server/Skype for Business from outside the intranet but without VPN) with a user on Skype for Business Server 2019, and a user on the legacy install. Test IM, presence, A/V, and desktop sharing.
    
- A user hosted on Skype for Business Server 2019 using remote user access (logging in to Skype for Business Server 2019 from outside the intranet but without VPN) with a user on Skype for Business Server 2019, and a user on the legacy install. Test IM, presence, A/V, and desktop sharing.
    

