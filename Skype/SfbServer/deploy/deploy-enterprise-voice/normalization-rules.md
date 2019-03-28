---
title: "Create or modify a normalization rule in Skype for Business"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: e8547d7b-f74d-4a73-9a7d-df20d7a87fcd
description: "Summary: Learn how to define, create, and modify a normalization rule in Skype for Business Server."
---

# Create or modify a normalization rule in Skype for Business

**Summary:** Learn how to define, create, and modify a normalization rule in Skype for Business Server.

Define, create, and modify normalization rules in Skype for Business Server.

### To define a normalization rule by using Build a Normalization Rule

1. Open Skype for Business Server Control Panel

2. (Optional) Follow the steps in [Create or modify a dial plan in Skype for Business Server](dial-plans.md) through step 11 or [Modify a Dial Plan](https://technet.microsoft.com/library/a91f02df-cf60-40cf-82fe-e0342c118b91.aspx) through step 10.

3. In **New Normalization Rule** or **Edit Normalization Rule**, type a name that describes the number pattern being normalized in **Name** (for example,5DigitExtension).

4. (Optional) In **Description**, type a description of the normalization rule (for example, "Translates 5-digit extensions").

5. In **Build a Normalization Rule**, enter values in the following fields:

   - **Starting digits** (Optional) Specify the leading digits of dialed numbers you want the pattern to match. For example, type425 if you want the pattern to match dialed numbers beginning with 425.

   - **Length** Specify the number of digits in the matching pattern and select whether you want the pattern to match this length exactly, match dialed numbers that are at least this length, or match dialed numbers of any length.

   - **Digits to remove** (Optional) Specify the number of starting digits to be removed from dialed numbers you want the pattern to match.

   - **Digits to add** (Optional) Specify digits to be added to dialed numbers you want the pattern to match.

     The values you enter in these fields are reflected in **Pattern to match** and **Translation rule**. For example, if you leave **Starting digits** empty, type7 into the **Length** field and select **Exactly**, and specify 0 in **Digits to remove**, the resulting regular expression in the **Pattern to match** is:

     ^(\d{7})$

6. In **Translation rule**, specify a pattern for the format of translated E.164 phone numbers as follows:

   - A value that represents the number of digits specified in the matching pattern. For example, if the matching pattern is ^(\d{7})$ then$1 in the translation rule represents 7-digit dialed numbers.

   - (Optional) Type a value into the **Digits to add** field to specify digits to be prepended to the translated number (for example,+1425).

     For example, if **Pattern to match** contains^(\d{7})$ as the pattern for dialed numbers and **Translation rule** contains+1425$1 as the pattern for E.164 phone numbers, the rule normalizes 5550100 to +14255550100.

7. (Optional) If the normalization rule results in a phone number that is internal to your organization, select **Internal extension**.

8. (Optional) Enter a number to test the normalization rule, and then click **Go**. The test results are displayed under **Enter a number to test**.

    > [!NOTE]
    > You can save a normalization rule that does not yet pass the test and then reconfigure it later. For details, see [Test Voice Routing](https://technet.microsoft.com/library/d3aae909-fef6-440f-b144-0b62dc82bf5d.aspx).

9. Click **OK** to save the normalization rule.

10. Click **OK** to save the dial plan.

11. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Whenever you create or change a normalization rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

### To define a normalization rule manually

1. Open Skype for Business Server Control Panel

2. (Optional) Follow the steps in [Create or modify a dial plan in Skype for Business Server](dial-plans.md).

3. In **New Normalization Rule** or **Edit Normalization Rule**, type a name that describes the number pattern being normalized in **Name** (for example, name the normalization rule5DigitExtension).

4. (Optional) In **Description** field, type a description of the normalization rule (for example, "Translates 5-digit extensions").

5. In **Build a Normalization Rule**, click **Edit**.

6. Enter the following in **Type a Regular Expression**:

   - In **Match this pattern**, specify the pattern that you want to use to match the dialed phone number.

   - In **Translation rule**, specify a pattern for the format of translated E.164 phone numbers.

     For example, if you enter ^(\d{7})$ in **Match this pattern** and+1425$1 in **Translation rule**, the rule normalizes 5550100 to +14255550100.

7. (Optional) If the normalization rule results in a phone number that is internal to your organization, select **Internal extension**.

8. (Optional) Enter a number to test the normalization rule and then click **Go**. The test results are displayed under **Enter a number to test**.

9. Click **OK** to save the normalization rule.

10. Click **OK** to save the dial plan.

11. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Whenever you create or change a normalization rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.


