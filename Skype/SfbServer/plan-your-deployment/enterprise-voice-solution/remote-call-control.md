---
title: "Plan for remote call control in Skype for Business"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 688a0328-1aa7-449f-b5f7-98c876112ed2
description: "Remote call control was a feature in previous versions of Lync Server which enabled users to control their PBX phones with Lync Server. In Skype for Business Server, this feature has been replaced with Call Via Work. In the client versions for Skype for Business Server 2015 and going forward, remote call control is no longer available to configure in the client and has been removed for use."
---

# Plan for remote call control in Skype for Business
 
Remote call control was a feature in previous versions of Lync Server which enabled users to control their PBX phones with Lync Server. In Skype for Business Server, this feature has been replaced with Call Via Work.  *In the client versions for Skype for Business Server 2015 and going forward, remote call control is no longer available to configure in the client and has been removed for use.* 
  
 Remote call control users in your organization who are homed on Front End Servers running Lync Server can continue to use remote call control, even if they are using a Skype for Business client. However, for any users homed on Skype for Business Server, remote call control is not supported. See the following table for server/client combinations and whether they can support remote call control or Call via Work.
  
|&nbsp;|Skype for Business Client With Skype UI enabled|Skype for Business Client With Lync UI enabled|Skype for Business 2016 Client|Lync 2013 Client|Lync 2010 Client|
|:-----|:-----|:-----|:-----|:-----|:-----|
| Skype for Business Server  |Call via Work   |1  |Call via Work   |1  |1  |
| Lync Server 2013  |Remote Call Control   |Remote Call Control   |1  |Remote Call Control   |Remote Call Control   |
| Lync Server 2010  |Remote Call Control   |Remote Call Control   |1  |Remote Call Control   |Remote Call Control   |
   
1. Neither feature is supported.
  
For more information, see [Remote Call Control](/previous-versions/office/lync-server-2013/lync-server-2013-planning-for-remote-call-control) in the Lync Server 2013 documentation.
  
## See also

[Plan for Call Via Work in Skype for Business Server](call-via-work.md)
  
[Desktop client feature comparison for Skype for Business](../../plan-your-deployment/clients-and-devices/desktop-feature-comparison.md)

[Make a Skype for Business call but use your PBX desk phone for audio](https://support.office.com/article/Make-a-Skype-for-Business-call-but-use-your-PBX-desk-phone-for-audio-6a316c11-a05e-460c-b969-32ff0ad848e6)