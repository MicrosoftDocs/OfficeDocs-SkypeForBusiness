---
title: "Create or modify a dial plan in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: d2fef3d0-7e78-4591-b712-d62ac71d71a5
description: "Summary: Learn how to create or modify a dial plan by using the Skype for Business Server Control Panel."
---

# Create or modify a dial plan in Skype for Business Server

**Summary:** Learn how to create or modify a dial plan by using the Skype for Business Server Control Panel.

### To create a dial plan

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Voice Routing** and then click **Dial Plan**.

3. On the **Dial Plan** page, click **New** and select a scope for the dial plan:

   - **Site dial plan** applies to an entire site, except any users or groups that are assigned to a user dial plan. If you select **Site** for a dial plan's scope, you must choose the site from the **Select a Site** dialog box. If a dial plan has already been created for a site, the site does not appear in the **Select a Site** dialog box.

   - **Pool dial plan** can apply to a public switched telephone network (PSTN) gateway or a Registrar. If you select **Pool** for a dial plan's scope, choose the PSTN gateway or Registrar from the **Select a Service** dialog box. If a dial plan has already been created for a service (PSTN gateway or Registrar), the service does not appear in the list.

   - **User dial plan** can be applied to specified users or groups.

     > [!NOTE]
     > After you select the dial plan scope, it cannot be changed.

4. If you are creating a user dial plan, enter a descriptive name in the **Name** field on the **New Dial Plan** dialog box. After this name is saved, it cannot be changed.

    > [!NOTE]
    > For site dial plans, the **Name** field is prepopulated with the site name and cannot be changed.> For pool dial plans, the **Name** field is prepopulated with the PSTN gateway or Registrar name and cannot be changed.

5. The **Simple name** field is prepopulated with the same name that appears in the **Name** field. You can optionally edit this field to specify a more descriptive name that reflects the site, service, or user to which the dial plan applies.

   > [!IMPORTANT]
   > The **Simple name** must be unique among all dial plans in your deployment. It cannot exceed 256 Unicode characters, each of which can be an alphabetic or numeric character, a hyphen (-), a period (.), or an underscore (_).> Characters **not supported** include spaces and Reserved characters as defined in RFC 3966 (<http://www.ietf.org/rfc/rfc3966.txt>). Reserved characters that are **not supported** in the **Simple Name** include the following:> ";" "/" "?" ":" "@" "&amp;" "=" "+" "$" ","

6. (Optional) In the **Description** field, you can type additional descriptive information about the dial plan.

7. (Optional) If you want to use this dial plan as a region for dial-in access numbers, specify a **Dial-in conferencing region**. If you do not want to use this dial plan for dial-in access numbers, leave this field empty.

    > [!NOTE]
    > Dial-in conferencing regions are required to associate dial-in conferencing access numbers with one or more dial plans.

8. (Optional) In the **External access prefix** field, specify a value only if users need to dial one or more additional leading digits (for example, 9) to get an external line. You can type in a prefix value of up to four characters (#, *, and 0-9).

    > [!NOTE]
    > If you specify an external access prefix, you do not need to create a new normalization rule to accommodate the prefix.

9. Associate and configure normalization rules for the dial plan as follows:

    - To choose one or more rules from a list of all normalization rules available in your Enterprise Voice deployment, click **Select**. In **Select Normalization Rules**, highlight the rules you want to associate with the dial plan and then click **OK**.

   - To define a new normalization rule and associate it with the dial plan, click **New**. For details about defining a new rule, see [Create or modify a normalization rule in Skype for Business](normalization-rules.md).

   - To edit a normalization rule that is already associated with the dial plan, highlight the rule name and click **Show details**.

   - To copy an existing normalization rule to use as a starting point for defining a new rule, highlight the rule name and click **Copy**, and then click **Paste**.

   - To remove a normalization rule from the dial plan, highlight the rule name and click **Remove**.

     > [!NOTE]
     > Each dial plan must have at least one associated normalization rule. For information about how to determine all of the normalization rules a dial plan requires, see [Plan for outbound voice routing in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/outbound-voice-routing.md) in the Planning documentation.

10. Verify that the dial plan's normalization rules are arranged in the correct order. To change a rule's position in the list, highlight the rule name and then click the up or down arrow.

    > [!IMPORTANT]
    > Skype for Business Server traverses the normalization rule list from the top down and uses the first rule that matches the dialed number. If you configure a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones. > The default **Keep All** normalization rule^(\d{11})$ matches any 11-digit number. For example, if you add a normalization rule that matches 11-digit numbers that start with 1425, make sure that **Keep All** is sorted below the more restrictive^(1425\d{7})$ rule.

11. (Optional) Enter a number to test the dial plan and then click **Go**. The test results are displayed under **Enter a number to test**.

12. Click **OK**.

13. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Any time you create a dial plan, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

### To modify a dial plan

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Voice Routing** and then click **Dial Plan**.

4. On the **Dial Plan** page, double-click a dial plan name.

    > [!NOTE]
    > The dial plan scope and name were set when the dial plan was created. They cannot be changed.

5. (Optional) In **Edit Dial Plan**, edit the **Simple name** field, which is prepopulated with the same name that appears in the **Name** field to specify a more descriptive name that reflects the site, service, or user to which the dial plan applies.

    > [!IMPORTANT]
    > The **Simple name** must be unique among all dial plans within the Lync Server 2013 deployment. It cannot exceed 256 Unicode characters, each of which can be an alphabetic or numeric character, a hyphen (-), a period (.), a plus sign (+), or an underscore (_).> Spaces are not allowed in the **Simple name** field.

6. (Optional) In the **Description** field, type descriptive information about the dial plan.

7. (Optional) If you want to use this dial plan as a region for dial-in access numbers, specify a **Dial-in conferencing region**. If you do not want to use this dial plan for dial-in access numbers, leave this field empty.

    > [!NOTE]
    > Dial-in conferencing regions are required to associate dial-in conferencing access numbers with one or more dial plans.

8. (Optional) In the **External access prefix** field, specify a value only if users need to dial one or more additional leading digits to get an external line (for example, 9). You can type in a prefix value of up to four characters (that is, #, *, and 0-9).

    > [!NOTE]
    > If you specify an external access prefix, you do not need to create a new normalization rule to accommodate the prefix.

9. Associate and configure normalization rules for the dial plan:

   - To choose one or more rules from a list of all normalization rules available in your Enterprise Voice deployment, click **Select**. In the **Select Normalization Rules** dialog box, highlight the rules that you want to associate with the dial plan and then click **OK**.

   - To define a new normalization rule and associate it with the dial plan, click **New**. For details about defining a new rule, see [Create or modify a normalization rule in Skype for Business](normalization-rules.md).

   - To edit a normalization rule that is already associated with the dial plan, highlight the rule name and click **Show details**.

   - To copy an existing normalization rule to use as a starting point for defining a new rule, highlight the rule name and click **Copy**, and then click **Paste**.

   - To remove a normalization rule from the dial plan, highlight the rule name and click **Remove**.

     > [!NOTE]
     > Each dial plan must have at least one associated normalization rule. For details about how to determine all of the normalization rules a dial plan requires, see [Plan for outbound voice routing in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/outbound-voice-routing.md) in the Planning documentation.

10. Verify that the dial plan's normalization rules are arranged in the correct order. To change a rule's position in the list, highlight the rule name and then click the up or down arrow.

    > [!IMPORTANT]
    > Skype for Business Server traverses the normalization rule list from the top down and uses the first rule that matches the dialed number. If you configure a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones. > The default **Keep All** normalization rule^(\d{11})$ matches any 11-digit number. If, for example, you add a normalization rule that matches 11-digit numbers that start with 1425, make sure that **Keep All** is sorted below the more restrictive^(1425\d{7})$ rule.

11. (Optional) Enter a number to test the dial plan and then click **Go**. The test results are displayed under **Enter a number to test**.

    > [!NOTE]
    > You can save a dial plan that does not yet pass the test and then reconfigure it later. For details, see [Testing Voice Routing](https://technet.microsoft.com/library/d3aae909-fef6-440f-b144-0b62dc82bf5d.aspx).

12. Click **OK**.

13. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.

    > [!NOTE]
    > Any time you create or modify a dial plan, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.

## See also

[Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md)

