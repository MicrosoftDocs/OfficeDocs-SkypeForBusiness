---
title: "Create or modify an unassigned number range in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: a102b226-0460-4d5c-82f9-79b8444fa958
description: "Create, modify or delete unassigned number ranges for Announcement application in Skype for Business Server Enterprise Voice. This affects how calls to unassigned numbers are handled."
---

# Create or modify an unassigned number range in Skype for Business Server
 
Create, modify or delete unassigned number ranges for Announcement application in Skype for Business Server Enterprise Voice. This affects how calls to unassigned numbers are handled.
  
Skype for Business Server enables you to say what happens to incoming calls to phone numbers that are valid for your organization, but are not assigned to a user or a phone. To handle such calls, you set up an unassigned number table. You can use the table to route the calls to an Announcement application or to an Exchange UM server.
  
How you configure the unassigned number table depends on how you want to use it. You can configure the table with all the valid extensions for your organization, with only unassigned extensions, or with a combination of both types of numbers. The unassigned number table can include both assigned and unassigned numbers, but it is invoked only when a caller dials a number that is not currently assigned. If you include all the valid extensions in the unassigned number table, you can specify the action that occurs whenever someone leaves your organization, without needing to reconfigure the table. If you include unassigned extensions in the table, you can modify the action that occurs for specific numbers. For example, if you change the extension for your customer service desk, you can include the old customer service number in the table and then assign it to an announcement that provides the new number.
  
## Configure unassigned phone numbers

Use one of the following procedures to configure unassigned number ranges for the Announcement application.
  
> [!IMPORTANT]
> Before you configure the unassigned number table, your system must already either have Announcements defined or an Exchange Unified Messaging (UM) Auto Attendant set up. 
  
> [!TIP]
> When someone calls an unassigned number, Skype for Business Server searches the unassigned number table from top to bottom and uses the first matching range. Therefore, an action that you want to be performed as a last resort should be specified for the last range in the table. 
  
### To use Skype for Business Server Control Panel to configure unassigned phone numbers

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Voice Features**, and then click **Unassigned Number**.
    
4. On the **Unassigned Number** page, do one of the following:
    
   - To create a new number range, click **New**. In **Name**, type an identifying name for this range of numbers.
    
     > [!NOTE]
     > After you commit the new unassigned number range to the database, you cannot change this name. 
  
   - To modify an existing number range, type all or part of the name of the number range in the search field. In the resulting list of number ranges, click the name you want, click **Edit**, and then click **Show details**.
    
5. In the first **Number range** field, type the beginning number of the range, and in the second **Number range** field, type the ending number of the range.
    
   - The beginning number of the range must be less than or equal to the ending number of the range.
    
   - If the beginning number of the range or the ending number of the range includes an extension number, both the beginning number and the ending number of the range must include an extension, and the extension number must be the same for both the beginning number and the ending number.
    
   - The number must match the regular expression (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. This means the number may begin with the string tel: (if you don't specify that string, it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by an extension in the format ;ext= followed by the extension number.
    
6. In **Announcement service**, do one of the following: 
    
   - Click **Announcement**.
    
   - Click **Exchange UM**.
    
7. If, in the previous step, you clicked **Announcement**, do the following:
    
    a. Under **FQDN of destination server**, click **Select**, click the service ID of the Application service that runs the Announcement application that will handle incoming calls to this range of unassigned numbers, and then click **OK**.
    
    b. In **Announcement**, click the announcement to be played for this range of unassigned numbers.
    
8. If, in the previous step, you clicked **Exchange UM**, under **Auto Attendant phone number**, click **Select**, click the phone number to be used for this range of unassigned numbers, and then click **OK**.
    
9. Click **OK**.
    
10. On the **Unassigned Number** page, be sure that the unassigned number ranges are arranged in the order that you want. To change a range's position in the table, click one or more consecutive names in the list of ranges, and then click the up arrow or the down arrow.
    
    > [!TIP]
    > Skype for Business Server searches the unassigned number table from top to bottom and uses the first range that matches the unassigned number. If you have overlapping ranges and one range specifies a last resort action, make sure that range is at the bottom of the list. 
  
11. When you have the unassigned number ranges in the order that you want, click **Commit all**.
    
### To use Skype for Business Server Management Shell to configure unassigned phone numbers

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Use **New-CsUnassignedNumber** to create a new unassigned number range. Use **Set-CsUnassignedNumber** to modify an existing unassigned number range.
    
    > [!TIP]
    > If you have overlapping ranges and want the ranges to be applied in a specific order, include the Priority parameter. The range with the highest priority will be applied to the call. The value 0 represents the highest priority.
  
    At the command line, do one of the following:
    
   - To create a number range for an Announcement service, run:
    
     ```
     New-CsUnassignedNumber -Identity <unique identifier for unassigned number range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -AnnouncementName <announcement name> -AnnouncementService <FQDN or service ID of the Announcement service>
     ```

   - Or, to create a number range for Exchange UM Auto Attendant, run:
    
     ```
     New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <phone number> -Identity <unique identifier for unassigned number range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range>
     ```

     For example:
    
     ```
     New-CsUnassignedNumber -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100" -AnnouncementName "Welcome Announcement" -AnnouncementService ApplicationServer:Redmond.contoso.com
     ```

     Or
    
     ```
     New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber "+12065551234" -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100"
     ```

     The following example shows how to modify the numbers in an existing unassigned number range:
    
     ```
     Set-CsUnassignedNumber -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"
     ```

## Delete an unnasigned number range

### To use Skype for Business Server Control Panel to delete an unassigned number range

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Voice Features** and then click **Unassigned Number**.
    
4. On the **Unassigned Number** page, in the search field, type all or part of the name of the unassigned number range you want to delete.
    
5. In the resulting list of number ranges, click the name, click **Edit**, and then click **Delete**.
    
6. Click **Commit all**.
    
### To use Skype for Business Server Management Shell to delete an unassigned number range

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. At the command line, type:
    
   ```
   Remove-CsUnassignedNumber -Identity "<name of unassigned number range>" 
   ```

    For example:
    
   ```
   Remove-CsUnassignedNumber -Identity "Unassigned range 1"
   ```

    > [!NOTE]
    > For details about more options, see [Remove-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/remove-cscallparkorbit?view=skype-ps). 
  
## See also

[New-CsUnassignedNumber](https://docs.microsoft.com/powershell/module/skype/new-csunassignednumber?view=skype-ps)
  
[Set-CsUnassignedNumber](https://docs.microsoft.com/powershell/module/skype/set-csunassignednumber?view=skype-ps)
  
[Get-CsUnassignedNumber](https://docs.microsoft.com/powershell/module/skype/get-csunassignednumber?view=skype-ps)
