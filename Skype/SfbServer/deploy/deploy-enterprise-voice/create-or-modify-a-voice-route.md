---
title: "Create or modify a voice route in Skype for Business"
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
ms.assetid: d189057d-cc9d-4622-9d10-f5385d703faf
description: "Summary: Learn how to create or modify a voice route in Skype for Business Server by using the Skype for Business Server Control Panel."
---

# Create or modify a voice route in Skype for Business
 
**Summary:** Learn how to create or modify a voice route in Skype for Business Server by using the Skype for Business Server Control Panel.
  
### To create a voice route by using the Skype for Business Server Control Panel

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Voice Routing**.
    
4. Click **Route**.
    
5. Click **New** to display the **New Voice Route** dialog box.
    
6. In **Name**, type a descriptive name for the voice route.
    
7. (Optional) In **Description**, type additional descriptive information for the voice route.
    
8. To specify the patterns that you want this route to accommodate, you can either use the **Build a pattern to match** tool to generate a regular expression, or write the regular expression manually.
    
   - To use the **Build a pattern to match** tool to generate a regular expression, enter values as follows. You can specify two types of pattern matching:
    
   - **Starting digits for numbers that you want to allow**: Enter prefix values that this route must accommodate (including the leading + if needed). For example, type +425, and then click **Add**. Repeat this for each prefix value that you want to include in the route.
    
   - **Exceptions**: If you want to specify one or more exceptions for a prefix value, highlight the prefix and click **Exceptions**. Type in one or more values for the matching patterns that you do  *not*  want this route to accommodate. For example, to exclude numbers starting with +425237 from the route, enter a value of+425237 in the **Exceptions** field, and then click **OK**.
    
   - To define the matching pattern manually, click **Edit** in the **Build a pattern to match** tool and then type in a .NET Framework regular expression to specify the matching pattern for destination phone numbers to which the route is applied. For details about how to write regular expressions, see [".NET Framework Regular Expressions"](https://go.microsoft.com/fwlink/p/?linkId=140927). 
    
9. Select **Suppress caller ID** if you do not want the ID of the phone making the outbound call to appear to the call recipient. If you select this option, you must specify an **Alternate caller ID** that will appear on the recipient's caller ID display.
    
10. To associate one or more trunks with the voice route, click **Add** and then select a trunk from the list.
    
11. To associate one or more Public Switched Telephone Network (PSTN) usages with the voice route, click **Select** and choose a record from the list of PSTN usage records that have been defined for your Enterprise Voice deployment.
    
    > [!NOTE]
    > To view the properties of each of the available PSTN usage records, see [View PSTN usage records in Skype for Business](view-pstn-usage-records.md). > To create or edit PSTN usage records, see [Create or modify a voice policy and configure PSTN usage records in Skype for Business](voice-policy-and-pstn-usage-records.md)
  
12. Arrange the PSTN usage records for optimum performance. To change a record's position in the list, highlight the record name and click the up or down arrow.
    
    > [!NOTE]
    > In contrast to a voice policy, where the order in which PSTN usage records are listed is important, the order in which PSTN usage records are listed in the voice route is insignificant. However, we recommend that you organize the list by frequency of use. For example: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup. (Skype for Business Server traverses the list from the top down.) 
  
13. (Optional) Type a value into the **Enter a translated number to test** field and click **Go**. The test results are displayed under the field.
    
14. Click **OK** to save the voice route.
    
    > [!IMPORTANT]
    > Whenever you create a voice route, you must run the **Commit All** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md). 
  
### To modify a voice route

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Voice Routing**, and then click **Route**.
    
3. On the **Route** page, use either of the following methods to modify a voice route:
    
   - Click a voice route name, click **Edit**, and then click **Show details**.
    
   - Click a voice route name, click **Edit**, click **Copy**, and then click **Paste**. Click the new copy of the voice route that you just created, click **Edit**, and then click **Show details**.
    
4. In the **Name** field on the **Edit Voice Route** page, type a descriptive name for the voice route.
    
5. (Optional) In the **Description** field, type in additional descriptive information for the voice route.
    
6. To specify the patterns you want this route to accommodate, you can either use the **Build a pattern to match** tool to generate a regular expression, or write the regular expression manually.
    
   - To use the **Build a pattern to match** tool to generate a regular expression, enter values as follows. You can specify two types of pattern matching:
    
   - **Starting digits for numbers that you want to allow**: Enter prefix values that this route must accommodate (including the leading + if needed). For example, type +425 and then click **Add**. Repeat this for each prefix value that you want to include in the route.
    
   - **Exceptions**: If you want to specify one or more exceptions for a prefix value, highlight the prefix and click **Exceptions**. Type in one or more values for the matching patterns that you do  *not*  want this route to accommodate. For example, to exclude numbers starting with +425237 from the route, enter a value of+425237 in the **Exceptions** field, and then click **OK**.
    
   - To define the matching pattern manually, click **Edit** in the **Build a pattern to match** tool and then type in a .NET Framework regular expression to specify the matching pattern for destination phone numbers to which the route is applied.For details about how to write regular expressions, see [".NET Framework Regular Expressions"](https://go.microsoft.com/fwlink/p/?linkId=140927). 
    
7. Select **Suppress caller ID** if you do not want the ID of the phone that is making the outbound call to appear to the call recipient. If you select this option, you must specify an **Alternate caller ID** that will appear on the recipient's caller ID display.
    
8. To associate one or more public switched telephone network (PSTN) trunks with the voice route, click **Add**, and then select a trunk from the list.
    
9. To associate one or more PSTN usages with the voice route, click **Select** and choose a record from the list of PSTN usage records that have been defined for your Enterprise Voice deployment.
    
    > [!NOTE]
    > To view the properties of each of the available PSTN usage records, see [View PSTN usage records in Skype for Business](view-pstn-usage-records.md). > To create or edit PSTN usage records, see [Create or modify a voice policy and configure PSTN usage records in Skype for Business](voice-policy-and-pstn-usage-records.md). 
  
10. Arrange the PSTN usage records for optimum performance. To change a record's position in the list, highlight the record name and click the up or down arrow.
    
    > [!NOTE]
    > In contrast to a voice policy where the order in which PSTN usage records are listed is important, the order of PSTN usage records in a voice route is insignificant. However, we recommend that you organize the list by frequency of use, for example: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup. (Skype for Business Server traverses the list from the top down.) 
  
11. (Optional) Type a value into the **Enter a translated number to test** field and click **Go**. The test results are displayed under the field.
    
12. Click **OK**.
    
13. On the **Route** page, click **Commit**, and then click **Commit all**. 
    
    > [!NOTE]
    > Whenever you create or modify a voice route, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.
  
## See also

[View PSTN usage records in Skype for Business](view-pstn-usage-records.md)
  
[Create or modify a voice policy and configure PSTN usage records in Skype for Business](voice-policy-and-pstn-usage-records.md)
  
[Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md)

