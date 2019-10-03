---
title: Create or modify a normalization rule in Microsoft Teams
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.reviewer: roykuntz, jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Calling Plans
description: Learn how to create normalization rules for dial plans in Microsoft Teams. 
---

# Create a normalization rule in Microsoft Teams

Normalization rules define how phone numbers expressed in various formats are translated. Normalization rules take the phone number dialed by a user and converts it to the format that's used internally by Teams. The same dial string may be interpreted and translated differently, depending on the location from which it is dialed and the person who makes the call. A dial plan must have at least one normalization rule associated with it.

You create normalization rules in the Microsoft Teams admin center. You can define normalizations by using a template or manually.

## Define a normalization rule by using a template

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Dial plan**.
2. Do one of the following:
    - If you're creating a normalization rule for a [new dial plan](create-and-manage-dial-plans.md), click **Add** to create a new dial plan.
    - If you're creating a normalization rule for an existing dial plan, select the dial plan by clicking to the left of it, and then click **Edit**.
3. Under **Normalization rules**, click **Add**.
4. In **Name**, type a name that describes the number pattern that's being normalized. For example, 7DigitExtension.
5. In **Description**, type a description. For example, "Translates 7-digit extensions".
6. Click **Advanced**, click **Select from a template**, and then choose a template. The template adds a regular expression to **The number dialed matches this regular expression** under **If condition**. This is the number pattern to match.
7. Under **Then do this**, specify a regular expression for number translation. This is the number pattern for the format of translated E.164 numbers. For example, if you selected the 7 digit extension template, **^(\d{7})$**, is added to **If condition** as the number pattern to match. If you specify **+1425$1** in **Then do this**, the rule normalizes 5550100 to +14255550500.
8. Under **Test this rule**, enter a number to test the rule, and then click **Test**. 
9. Click **Save**.

## Define a normalization rule manually

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Dial plan**.
2. Do one of the following:
    - If you're creating a normalization rule for a [new dial plan](create-and-manage-dial-plans.md), click **Add** to create a new dial plan.
    - If you're creating a normalization rule for an existing dial plan, select the dial plan by clicking to the left of it, and then click **Edit**.
3. Under **Normalization rules**, click **Add**.
4. In **Name**, type a name that describes the number pattern that's being normalized. For example, 5DigitExtension.
5. In **Description**, type a description. For example, "Translates 5-digit extensions".
6. 
    
## Related topics

- [Create and manage dial plans](create-and-manage-dial-plans.md)
