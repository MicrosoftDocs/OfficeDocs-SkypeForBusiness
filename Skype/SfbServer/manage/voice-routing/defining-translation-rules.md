---
title: "Defining translation rules in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Skype for Business Server Enterprise Voice routes calls based on phone numbers normalized to E.164 format. This means that all dialed strings must be normalized to E.164 format for the purpose of performing reverse number lookup (RNL) so they can be translated to their matching SIP URI. Skype for Business Server provides the ability to manipulate the called ID and the caller ID presentation."
---

# Defining translation rules in Skype for Business Server

Skype for Business Server Enterprise Voice routes calls based on phone numbers normalized to E.164 format. This means that all dialed strings must be normalized to E.164 format for the purpose of performing reverse number lookup (RNL) so they can be translated to their matching SIP URI. Skype for Business Server provides the ability to manipulate the called ID and the caller ID presentation.

With Skype for Business Server, the called party’s phone number (that is, the phone number called) can be translated from E.164 format to the local dialing format that is required by the trunk peer (that is, the associated gateway, private branch exchange (PBX), or SIP trunk). To do this, you must define one or more translation rules to translate the Request URI before routing it to the trunk peer.

## Caller ID presentation

Skype for Business Server offers the option to also translate the calling party’s phone number (that is, the phone number that the caller is calling from) from E.164 format to the local dialing format that is required by the trunk peer. For example, you can write a translation rule to remove +44 from the beginning of a dial string and replace it with 0144.

**To configure Caller ID by using the Skype for Business Server Control Panel**

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions](https://technet.microsoft.com/en-us/library/gg412735(v=ocs.15).aspx).
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. In the left navigation bar, click **Voice Routing**, and then click **Trunk Configuration**.
4. On the Trunk Configuration page, double-click an existing trunk (for example, the **Global** trunk) to display the **Edit Trunk Configuration** dialog box.
5. To configure caller ID presentation:
    - To choose one or more rules from a list of all translation rules available in your Enterprise Voice deployment, click **Select**. In **Calling number translation rules**, click the rules that you want to associate with the trunk, and then click **OK**.
    - To define a new translation rule and associate it with the trunk, click **New**. 
    - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**.
    - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name, click **Copy**, and then click **Paste**.
    - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.

> [!Warning] 
> Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict. 

## Called ID presentation

> [!Important]
> The ability to associate one or more translation rules with an Enterprise Voice trunk configuration is intended to be used as an *alternative* to configuring translation rules on the trunk peer. Do not associate translation rules with an Enterprise Voice trunk configuration if you have configured translation rules on the trunk peer because the two rules might conflict. 

You can use either of the following methods to create or modify a translation rule:

- [Use the Build a Translation Rule tool](#create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool) to specify values for the starting digits, length, digits to remove and digits to add, and then let the Skype for Business Server Control Panel generate the corresponding matching pattern and translation rule for you.
- [Write regular expressions manually](#create-or-modify-a-translation-rule-manually) to define the matching pattern and translation rule.

> [!Note]
> For information about how to write regular expressions, see [.NET Framework Regular Expressions](http://go.microsoft.com/fwlink/p/?linkId=140927). 

### Create or modify a translation rule by using the Build a Translation Rule tool

Follow these steps if you want to define a translation rule by entering a set of values in the Build a Translation Rule tool and enabling the Skype for Business Server Control Panel to generate the corresponding matching pattern and translation rule for you. 

**To define a rule by using the Build a Translation Rule tool**

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions](https://technet.microsoft.com/en-us/library/gg412735(v=ocs.15).aspx).
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. To begin defining a translation rule, follow the steps in [Configure a trunk with media bypass](GET LINK AFTER MIGRATION)through step 10 or [Configure a trunk without media bypass](GET LINK AFTER MIGRATION) through step 9.
4. Under **Name** on the **New Translation Rule** or **Edit Translation Rule** page, type a name that describes the number pattern being translated.
5. (Optional) Under **Description**, type a description of the translation rule - for example, **US International long-distance dialing**.
6. In the **Build a Translation Rule** section of the dialog box, enter values in the following fields:
    - **Starting digits**: (Optional) Specify the leading digits of numbers you want the pattern to match. For example, enter + in this field to match numbers in E.164 format (which begin with +).
    - **Length**: Specify the number of digits in the matching pattern and select whether you want the pattern to match numbers that are this length exactly, at least this length, or any length. For example, enter **11** and select **At least** in the drop-down list to match numbers that are at least 11 digits in length.
    - **Digits to remove**: (Optional) Specify the number of starting digits to be removed. For example, enter **1** to strip out the + from the beginning of the number.
    - **Digits to add**: (Optional) Specify digits to be prepended to the translated numbers. For example, enter **011** if you want 011 to be prepended to the translated numbers when the rule is applied.
    
    The values you enter in these fields are reflected in the **Pattern to match** and **Translation** rule fields. For example, if you specify the preceding example values, the resulting regular expression in the **Pattern to matc**h field is:
    
    **^\+(\d{9}\d+)$** 

    The **Translation rule** field specifies a pattern for the format of translated numbers. This pattern has two parts:
    - A value (for example, **$1**) that represents the number of digits in the matching pattern
    - (Optional) A value that you can prepend by entering it in the **Digits to add** field

    Using the preceding example values, **011$1** appears in the **Translation rule** field.
    
    When this translation rule is applied, +441235551010 becomes 011441235551010.
7. Click **OK** to save the translation rule.
8. Click **OK** to save the trunk configuration.
9. On the **Trunk Configuratio**n page, click **Commit**, and then click **Commit all**. 

> [!Note]
> Whenever you create or modify a translation rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration](https://technet.microsoft.com/en-us/library/gg413088(v=ocs.15).aspx). 

### Create or modify a translation rule manually

Follow these steps if you want to define a translation rule by writing a regular expression for the matching pattern and translation rule. 

**To define a translation rule manually**

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions](https://technet.microsoft.com/en-us/library/gg412735(v=ocs.15).aspx).
2. Open a browser window, and then enter the Admin URL to open the Control Panel. For details about the different methods you can use to start the Skype for Business Control Panel, see [Install and open administrative tools](../../management-tools/install-and-open-administrative-tools.md).
3. To begin defining a translation rule, follow the steps in [Configure a trunk with media bypass](GET LINK AFTER MIGRATION)through step 10 or [Configure a trunk without media bypass](GET LINK AFTER MIGRATION) through step 9.
4. In the **Name** field on the **New Translation Rule** or **Edit Translation Rule** page, type a name that describes the number pattern being translated.
5. (Optional) In **Description**, type a description of the translation rule; for example, **US International long-distance dialing**.
6. Click **Edit** at the bottom of the **Build a Translation Rule** section.
7. Enter the following in Type a **Regular Expression**:
    - In **Match this pattern**, specify the pattern that will be used to match the numbers to be translated.
    - In **Translation rule**, specify a pattern for the format of translated numbers.

    For example, if you enter **^\+(\d{9}\d+)$** in **Match this pattern** and **011$1** in **Translation rule**, the rule will translate +441235551010 to 011441235551010.
8. Click **OK** to save the translation rule.
9. Click **OK** to save the trunk configuration.
10. On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**. 

> [!Note] 
> Whenever you create or modify a translation rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration](https://technet.microsoft.com/en-us/library/gg413088(v=ocs.15).aspx). 
