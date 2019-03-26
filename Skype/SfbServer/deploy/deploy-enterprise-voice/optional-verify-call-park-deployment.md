---
title: "(Optional) Verify Call Park deployment in Skype for Business"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: fcfe0962-1a9c-4cbd-847c-fed40e3b1480
description: "Verifying your deployment of Call Park in Skype for Business Server Enterprise Voice."
---

# (Optional) Verify Call Park deployment in Skype for Business
 
Verifying your deployment of Call Park in Skype for Business Server Enterprise Voice. 
  
After you install and configure Call Park, you need to verify the configuration to make sure that parking and retrieving calls works as expected. At minimum, verify the following:
  
- Call a user who has Call Park enabled and have the user park the call.
    
    > [!NOTE]
    > If you enabled Call Park in voice policy just before performing this test, the user who is parking the call needs to sign out of Skype for Business, and then sign back in, to be able to see the Call Park option in the transfer call list. 
  
- Dial the orbit number to retrieve the call.
    
- Park another call, let the parked call time out, and do not pick up the ringback. Verify that the timed-out call is correctly routed to the fallback destination that is specified for **OnTimeoutURI**.
    

