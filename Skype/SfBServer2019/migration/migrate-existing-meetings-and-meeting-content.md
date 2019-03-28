---
title: "Migrate existing meetings and meeting content"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "When a user account is moved from to a Skype for Business Server 2019 server, the following information is moved with that user account:"
---

# Migrate existing meetings and meeting content

When a user account is moved to a Skype for Business Server 2019 server, the following information is moved with that user account:
  
- **Meetings already scheduled by the user**. This includes moving the conferencing directories and conferencing data.
    
- **User's personal identification number (PIN)**. The user's current PIN continues to work until it expires or the user requests a new PIN.
    
The following user account information does not move to the new server.
  
- **Meeting content**. In order to move the content shared during a meeting, such as PowerPoint, Whiteboard, attachments, or poll data, use the **-MoveConferenceData** parameter as part of the **Move-CsUser** cmdlet. 
    

