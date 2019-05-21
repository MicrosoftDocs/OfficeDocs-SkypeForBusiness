---
title: "Create or modify a Group Call Pickup number range in Skype for Business"
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
ms.assetid: 4b442b98-df6b-4e50-8254-b3be9cde21dd
description: "Create or modify a Group Call Pickup number range in Skype for Business Server Enterprise Voice."
---

# Create or modify a Group Call Pickup number range in Skype for Business

Create or modify a Group Call Pickup number range in Skype for Business Server Enterprise Voice.

Group Call Pickup is based on the Call Park application. When you deploy Group Call Pickup, you must configure the call park orbit table with ranges of phone numbers that are designated as call pickup group numbers. These group numbers are the numbers that users dial to pick up calls that are ringing for another user.

Like call park orbit numbers, call pickup group numbers need to be virtual extensions that have no user or phone assigned to them. Each Front End pool where you deploy Group Call Pickup can have one or more ranges of call pickup group numbers. The group number ranges must be globally unique in your deployment, and must be assigned as the **GroupPickup** type.

Use the following procedure to create or modify a call pickup group number range in the call park orbit table.

> [!NOTE]
> You must use Skype for Business Server Management Shell to create, modify, remove, and view Group Call Pickup number ranges in the call park orbit table. Group Call Pickup number ranges are not available in Skype for Business Server Control Panel.

The call pickup group number ranges must comply with the following rules:

- The beginning number of the range must be less than or equal to the ending number of the range.

- The value of the beginning number of the range must be the same length as the ending number of the range.

- The number range must be unique. This range cannot overlap with any other range.

- If the number range begins with the character \* or #, the range must be greater than 100.

- Valid values: Must match the regular expression string ([\\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). This means the value must be a string beginning with either the character \* or # or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or #, the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters (for example, "#6000", "\*92000", "\*95551212", and "915551212"). If the first character is not \* or #, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9 (for example, "915551212", "41212", "300").

### To create or modify a call pickup group range

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.

2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

3. Use **New-CsCallParkOrbit** to create a new range of call pickup group numbers. Use **Set-CsCallParkOrbit** to modify an existing range of call pickup numbers.

    At the command line, run:

   ```
   New-CsCallParkOrbit -Identity <name of call pickup group range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -CallParkService <FQDN or service ID of the Application service that hosts the Call Park application> -Type GroupPickup
   ```

    For example:

   ```
   New-CsCallParkOrbit -Identity "Redmond call pickup" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService redmond-applicationserver-1 -Type GroupPickup
   ```

    The following example shows how to change a range of numbers from call park orbits to call pickup groups.

   ```
   Set-CsCallParkOrbit -Identity "Redmond call pickup" -Type GroupPickup
   ```

    > [!IMPORTANT]
    > Use this cmdlet to change the type assigned to number ranges only if you initially specified the incorrect type and the group range is not yet in use. If you change the number range from CallPark to GroupPickup or vice versa and the number range is already in use, either Call Park or Group Call Pickup will stop working for that number range. For example, if you change a number range from CallPark to GroupPick, the Call Park application can no longer use that range of orbits to park calls.

## See also

[New-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/new-cscallparkorbit?view=skype-ps)

[Set-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/set-cscallparkorbit?view=skype-ps)

[Delete a Call Park Orbit Range](https://technet.microsoft.com/library/85e9f916-062d-450d-ac0a-aeaefc0f7cdc.aspx)
