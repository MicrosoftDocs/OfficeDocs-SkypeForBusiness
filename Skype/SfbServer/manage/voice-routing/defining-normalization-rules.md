---
title: "Defining normalization rules in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Skype for Business Server normalization rules use .NET Framework regular expressions to translate dialed phone numbers to E.164 format; in other words, normalization rules take the phone number dialed by a user and convert that number to the format used internally by Skype for Business Server. Each dial plan must be assigned one or more normalization rules."
---

# Defining normalization rules in Skype for Business Server

Skype for Business Server normalization rules use .NET Framework regular expressions to translate dialed phone numbers to E.164 format; in other words, normalization rules take the phone number dialed by a user and convert that number to the format used internally by Skype for Business Server. Each dial plan must be assigned one or more normalization rules.

For details about normalization rules, see [Dial plans and normalization rules](https://technet.microsoft.com/en-us/library/gg413082(v=ocs.15).aspx).

For details about how to write regular expressions, see [.NET Framework Regular Expressions](http://go.microsoft.com/fwlink/p/?linkId=140927).

You can use either of the following methods to define or edit a normalization rule:
- [Use the **Build a Normalization Rule** tool](#create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule) to specify values for the starting digits, length, digits to remove and digits to add, and then let Skype for Business Server Control Panel generate the corresponding matching pattern and translation rule for you.
- [Write regular expressions manually](#create-or-modify-a-normalization-rule-manually) to define the matching pattern and translation rule. 

## Create or modify a normalization rule by using Build a Normalization Rule

Complete the following steps if you want to create or modify a normalization rule in Skype for Business Server Control Panel. 

**To define a rule by using Build a Normalization Rule**

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions](https://technet.microsoft.com/en-us/library/gg412735(v=ocs.15).aspx).
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. (Optional) Follow the steps in [Create a dial plan](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-enterprise-voice/dial-plans#to-create-a-dial-plan) through step 11 or [Modify a dial plan](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-enterprise-voice/dial-plans#to-modify-a-dial-plan) through step 10. 
4. In **New Normalization Rule** or **Edit Normalization Rule**, type a name that describes the number pattern being normalized in **Name** (for example, **5DigitExtension**).
5. (Optional) In **Description**, type a description of the normalization rule (for example, "Translates 5-digit extensions").
6. In **Build a Normalization Rule**, enter values in the following fields:
    - **Starting digits**:   (Optional) Specify the leading digits of dialed numbers you want the pattern to match. For example, type **425** if you want the pattern to match dialed numbers beginning with 425.
    - **Length**:   Specify the number of digits in the matching pattern and select whether you want the pattern to match this length exactly, match dialed numbers that are at least this length, or match dialed numbers of any length.
    - **Digits to remove**:   (Optional) Specify the number of starting digits to be removed from dialed numbers you want the pattern to match.
    - **Digits to add**:   (Optional) Specify digits to be added to dialed numbers you want the pattern to match.
    
    The values you enter in these fields are reflected in **Pattern to match** and **Translation rule**. For example, if you leave **Starting digits** empty, type **7** into the **Length** field select **Exactly**, and specify **0** in **Digits to remove**, the resulting regular expression in the **Pattern to match** is:

    **^(\d{7})$**

7. In **Translation rule**, specify a pattern for the format of translated E.164 phone numbers as follows:
    - A value that represents the number of digits specified in the matching pattern. For example, if the matching pattern is **^(\d{7})$**, then $1 in the translation rule represents 7-digit dialed numbers.
    - (Optional) Type a value into the **Digits to add** field to specify digits to be prepended to the translated number (for example, **+1425**).
    
    For example, if **Pattern to match** contains **^(\d{7})$** as the pattern for dialed numbers and **Translation rule** contains **+1425$1** as the pattern for E.164 phone numbers, the rule normalizes 5550100 to +14255550100.

8. (Optional) If the normalization rule results in a phone number that is internal to your organization, select **Internal extension**.
9. (Optional) Enter a number to test the normalization rule, and then click **Go**. The test results are displayed under **Enter a number to test**.
    > [!Note] 
    > You can save a normalization rule that does not yet pass the test and then reconfigure it later. For details, see [Test voice routing](https://technet.microsoft.com/en-us/library/gg398915(v=ocs.15).aspx). 

10. Click **OK** to save the normalization rule.
11. Click **OK** to save the dial plan.
12. On the **Dial Plan** page, click **Commit**, and then click **Commit all**. 
    > [!Note]
    > Whenever you create or change a normalization rule, you must run the Commit all command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration](https://technet.microsoft.com/en-us/library/gg413088(v=ocs.15).aspx). 

## Create or modify a normalization rule manually

Complete the following steps if you want to create or modify a normalization rule manually.

**To define a normalization rule manually**

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions](https://technet.microsoft.com/en-us/library/gg412735(v=ocs.15).aspx).
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. (Optional) Follow the steps in [Create a dial plan](GET LINK AFTER MIGRATION) through step 11 or [Modify a dial plan](GET LINK AFTER MIGRATION) through step 10.  
4. In **New Normalization Rule** or **Edit Normalization Rule**, type a name that describes the number pattern being normalized in **Name** (for example, name the normalization rule **5DigitExtension**).
5. (Optional) In **Description**, type a description of the normalization rule (for example, "Translates 5-digit extensions").
6. In **Build a Normalization Rule**, click **Edit**.
7. Enter the following in Type a Regular Expression:
    - In **Match this pattern**, specify the pattern that you want to use to match the dialed phone number.
    - In **Translation rule**, specify a pattern for the format of translated E.164 phone numbers.

    For example, if you enter **^(\d{7})$** in **Match this pattern** and **+1425$1** in **Translation rule**, the rule normalizes 5550100 to +14255550100.

8. (Optional) If the normalization rule results in a phone number that is internal to your organization, select **Internal extension**.
9. (Optional) Enter a number to test the normalization rule, and then click **Go**. The test results are displayed under **Enter a number to test**.

    > [!Note]
    > You can save a normalization rule that does not yet pass the test and then reconfigure it later. For details, see [Test voice routing](https://technet.microsoft.com/en-us/library/gg398915(v=ocs.15).aspx). 

10. Click **OK** to save the normalization rule.
11. Click **OK** to save the dial plan.
12. On the **Dial Plan** page, click **Commi**t, and then click **Commit all**. 
