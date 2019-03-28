---
title: "Create or modify a Call Park orbit range in Skype for Business"
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
ms.assetid: 549ec118-eee5-4333-9416-80929ec057e0
description: "Create or modify a Call Park orbit range table in Skype for Business Server Enterprise Voice."
---

# Create or modify a Call Park orbit range in Skype for Business

Create or modify a Call Park orbit range table in Skype for Business Server Enterprise Voice.

Call Park uses orbits for parking calls. Before users can park and retrieve calls, you must configure the Call Park orbit table. You need to specify the ranges of extension numbers (orbits) that your organization will reserve for parking calls and define the routing for those ranges by specifying which Call Park pool handles each range. When you define orbit ranges, the goal is to have enough orbits so that any one orbit is not reused too quickly, but not so many orbits that you limit the number of extensions available for users or other services. You can create multiple Call Park orbit ranges for each Skype for Business Server pool where the Call Park application is deployed. Each Call Park orbit range must have a globally unique name and a unique set of extensions.

> [!IMPORTANT]
> An orbit range typically encompasses 100 or fewer orbits. Each range can be much larger, as long as it is smaller than the maximum of 10,000 orbits per range and you have fewer than 50,000 orbits per pool. If a range is too small, the orbits are reused more quickly.

Use blocks of virtual extensions (extensions that have no user or phone assigned to them) for your orbit ranges.

> [!NOTE]
> Assigning Direct Inward Dialing (DID) numbers as orbit numbers in the Call Park orbit table is not supported.

Use one of the following procedures to create or modify a call park orbit range.

### To use Skype for Business Server Control Panel to create or modify a range of numbers for parking calls

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Voice Features** and then click **Call Park**.

4. On the **Call Park** page, do one of the following:

   - To create a new orbit range, click **New**. In **Name**, type an identifying name for this range of numbers.

     > [!NOTE]
     > After you commit the orbit range to the database, you cannot change this name.

   - To modify an existing orbit range, type all or part of the name of the orbit range in the search field. In the resulting list of orbits, click the orbit you want, click **Edit**, and then click **Show details**.

5. In the first **Number range** field, type the beginning number of the range of extensions for this call park orbit, and in the second **Number range** field, type the ending number of the range. Be aware:

   - The beginning number of the range must be less than or equal to the ending number of the range.

   - The value of the beginning number of the range must be the same length as the ending number of the range.

   - The orbit range must be unique. This range cannot overlap with any other range.

   - If the orbit range begins with the character \* or #, the range must be greater than 100.

   - Valid values: Must match the regular expression string ([\\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). This means the value must be a string beginning with either the character \* or # or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or #, the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters (for example, "#6000", "\*92000", "\*95551212", and "915551212"). If the first character is not \* or #, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9 (for example, "915551212", "41212", "300").

   - You should not have more than a total of 50,000 orbits per pool. Each orbit range typically encompasses 100 or fewer orbits, but it can be much larger as long as it includes fewer than 10,000 orbits. For example, instead of specifying a starting number of "7000000" and an ending number of "8000000," consider specifying a starting number of "7000000" and an ending number of "7000100."

6. In **FQDN of destination server**, click the fully qualified domain name (FQDN) or service ID of the Application service that hosts the Call Park application. All calls parked to numbers within the range specified by the start number and end number in the orbit range will be routed to this server or pool.

7. Click **Commit**.

### To use Skype for Business Server Management Shell to create or modify a range of numbers for parking calls

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.

2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

3. Use **New-CsCallParkOrbit** to create a new range of orbit numbers. Use **Set-CsCallParkOrbit** to modify an existing range of orbit numbers.

    At the command line, run:

   ```
   New-CsCallParkOrbit -Identity <name of orbit range> -NumberRangeStart <first number in orbit range> -NumberRangeEnd <last number in orbit range> -CallParkService <FQDN or service ID of the Application service that hosts the Call Park application>
   ```

    For example:

   ```
   New-CsCallParkOrbit -Identity "Redmond orbit 1" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService redmond-applicationserver-1
   ```

    The following example shows how to modify the numbers in an existing orbit range,

   ```
   Set-CsCallParkOrbit -Identity "Redmond orbit 1" -NumberRangeStart 500 -NumberRangeEnd 699
   ```

## See also

[New-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/new-cscallparkorbit?view=skype-ps)

[Set-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/set-cscallparkorbit?view=skype-ps)

[Delete a Call Park Orbit Range](https://technet.microsoft.com/library/85e9f916-062d-450d-ac0a-aeaefc0f7cdc.aspx)
