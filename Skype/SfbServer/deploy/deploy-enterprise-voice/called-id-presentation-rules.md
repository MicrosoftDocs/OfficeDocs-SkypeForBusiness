---
title: "Create or modify a translation rule for called ID presentation in Skype for Business Server"
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
ms.assetid: ba112df8-3bb4-48e4-a353-4bf9110ccd71
description: "Summary: Learn how to define a translation rule by using the Build a Translation Rule tool in Skype for Business Server."
---

# Create or modify a translation rule for called ID presentation in Skype for Business Server

**Summary:** Learn how to define a translation rule by using the Build a Translation Rule tool in Skype for Business Server.

Follow these steps if you want to define a translation rule by entering a set of values in the **Build a Translation Rule** tool and enabling Skype for Business Server Control Panel to generate the corresponding matching pattern and translation rule for you. Alternatively, you can a write regular expression manually to define the matching pattern and translation rule. For details, see [Create or Modify a Translation Rule Manually](https://technet.microsoft.com/library/049d1db3-af58-48c5-be89-52e1d068a4bd.aspx).

### To define a rule by using the Build a Translation Rule tool

1. Open Skype for Business Server Control Panel.

2. To begin defining a translation rule, follow the steps in [Configure a trunk with media bypass in Skype for Business Server](configure-trunk-with-media-bypass.md) through step 10 or [Configure a trunk without media bypass in Skype for Business Server](configure-trunk-without-media-bypass.md) through step 9.

3. Under **Name** on the **New Translation Rule** or **Edit Translation Rule** page, type a name that describes the number pattern being translated.

4. (Optional) Under **Description**, type a description of the translation rule, for example US International long-distance dialing.

5. In the **Build a Translation Rule** section of the dialog box, enter values in the following fields:

   - **Starting digits**: (Optional) Specify the leading digits of numbers you want the pattern to match. For example, enter + in this field to match numbers in E.164 format (which begin with +).

   - **Length**: Specify the number of digits in the matching pattern and select whether you want the pattern to match numbers that are this length exactly, at least this length, or any length. For example, enter 11 and selectAt least in the drop-down list to match numbers that are at least 11 digits in length.

   - **Digits to remove**: (Optional) Specify the number of starting digits to be removed. For example, enter 1 to strip out the+ from the beginning of the number.

   - **Digits to add**: (Optional) Specify digits to be prepended to the translated numbers. For example, enter 011 if you want 011 to be prepended to the translated numbers when the rule is applied.

     The values you enter in these fields are reflected in the **Pattern to match** and **Translation rule** fields. For example, if you specify the preceding example values, the resulting regular expression in the **Pattern to match** field is:

     ^\+(\d{9}\d+)$

     The **Translation rule** field specifies a pattern for the format of translated numbers. This pattern has two parts:

   - A value (for example, $1) that represents the number of digits in the matching pattern

   - (Optional) A value that you can prepend by entering it in the **Digits to add** field

     Using the preceding example values, 011$1 appears in the **Translation rule** field.

     When this translation rule is applied, +441235551010 becomes 011441235551010.

6. Click **OK** to save the translation rule.

7. Click **OK** to save the trunk configuration.

8. On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**.

   > [!NOTE]
   > Whenever you create or modify a translation rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

### To define a translation rule manually

1. Open Skype for Business Server Control Panel

2. To begin defining a translation rule, follow the steps in [Configure a trunk with media bypass in Skype for Business Server](configure-trunk-with-media-bypass.md) through step 10 or [Configure a trunk without media bypass in Skype for Business Server](configure-trunk-without-media-bypass.md) through step 9.

3. In the **Name** field on the **New Translation Rule** or **Edit Translation Rule** page, type a name that describes the number pattern being translated.

4. (Optional) In **Description**, type a description of the translation rule, for example US International long-distance dialing.

5. Click **Edit** at the bottom of the **Build a Translation Rule** section.

6. Enter the following in **Type a Regular Expression**:

   - In **Match this pattern**, specify the pattern that will be used to match the numbers to be translated.

   - In **Translation rule**, specify a pattern for the format of translated numbers.

     For example, if you enter ^\+(\d{9}\d+)$ in **Match this pattern** and011$1 in **Translation rule**, the rule will translate +441235551010 to 011441235551010.

7. Click **OK** to save the translation rule.

8. Click **OK** to save the trunk configuration.

9. On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Whenever you create or modify a translation rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

## See also

[Configure a trunk with media bypass in Skype for Business Server](configure-trunk-with-media-bypass.md)

[Configure a trunk without media bypass in Skype for Business Server](configure-trunk-without-media-bypass.md)

[Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md)

[Deploy media bypass in Skype for Business Server](deploy-media-bypass.md)

