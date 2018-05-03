---
title: "Verify federation and remote access for external users"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a383fefb-c428-4462-93fd-15ba540fa867
description: "After transitioning the federation route to the Lync Server 2013 Edge Server, you should perform some functional tests to verify that federation performs as expected. Tests for external user access should include each type of external user that your organization supports, including any or all of the following."
---

# Verify federation and remote access for external users
[]
After transitioning the federation route to the Lync Server 2013 Edge Server, you should perform some functional tests to verify that federation performs as expected. Tests for external user access should include each type of external user that your organization supports, including any or all of the following.
  
### Test Connectivity of External Users and External access

- Users from at least one federated domain, an internal user on Lync Server 2013, and a user on Lync Server 2010. Test instant messaging (IM), presence, audio/video (A/V), and desktop sharing.
    
- Users of each public IM service provider that your organization supports (and for which provisioning has been completed) communicating with a user on Lync Server 2013 and a user on Lync Server 2010. 
    
- Verify that anonymous users are able to join conferences.
    
- A user hosted on Lync Server 2010 using remote user access (logging into Lync Server 2010 from outside the intranet but without VPN) with a user on Lync Server 2013, and a user on Lync Server 2010. Test IM, presence, A/V, and desktop sharing.
    
- A user hosted on Lync Server 2013 using remote user access (logging into Lync Server 2013 from outside the intranet but without VPN) with a user on Lync Server 2013, and a user on Lync Server 2010. Test IM, presence, A/V, and desktop sharing.
    

