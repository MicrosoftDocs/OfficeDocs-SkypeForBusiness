---
title: "Create or modify a translation rule for caller ID presentation in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 6a643961-a0a1-41d1-96ba-6c428a89d82e
description: "Summary: Learn how to configure Caller ID by using the Skype for Business Server Control Panel."
---

# Create or modify a translation rule for caller ID presentation in Skype for Business Server

**Summary:** Learn how to configure Caller ID by using the Skype for Business Server Control Panel.

With Skype for Business Server, the called party's phone number (that is, the phone number called) can be translated from E.164 format to the local dialing format that is required by the  _trunk peer_ (that is, the associated gateway, private branch exchange (PBX), or SIP trunk). To do this, you must define one or more translation rules to translate the Request URI before routing it to the trunk peer.

Skype for Business Server also gives you the option to also translate the calling party's phone number (that is, the phone number that the caller is calling from) from E.164 format to the local dialing format that is required by the trunk peer. For example, you can write a translation rule to remove +44 from the beginning of a dial string and replace it with 0144.

### To configure Caller ID by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Voice Routing**, and then click **Trunk Configuration**.

3. On the **Trunk Configuration** page, double-click an existing trunk (for example, the **Global** trunk) to display the **Edit Trunk Configuration** dialog box.

4. To configure caller ID presentation:

   - To choose one or more rules from a list of all translation rules available in your Enterprise Voice deployment, click **Select**. In **Calling number translation rules**, click the rules that you want to associate with the trunk, and then click **OK**.

   - To define a new translation rule and associate it with the trunk, click **New**. For details about defining a new rule, see  [Defining Translation Rules](https://technet.microsoft.com/library/4f6b975a-77e6-474c-9171-b139d84138c2.aspx) in the Deployment documentation.

   - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**. For details, see [Defining Translation Rules](https://technet.microsoft.com/library/4f6b975a-77e6-474c-9171-b139d84138c2.aspx) in the Deployment documentation.

   - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name and click **Copy**, and then click **Paste**. For details, see [Defining Translation Rules](https://technet.microsoft.com/library/4f6b975a-77e6-474c-9171-b139d84138c2.aspx).

   - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.

     > [!CAUTION]
     > Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict.


