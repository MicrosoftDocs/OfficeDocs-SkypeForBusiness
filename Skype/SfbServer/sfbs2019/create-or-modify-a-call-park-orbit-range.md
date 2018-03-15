---
title: "Create or modify a Call Park orbit range in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 549ec118-eee5-4333-9416-80929ec057e0
description: "Use one of the following procedures to create or modify a call park orbit range."
---

# Create or modify a Call Park orbit range in Lync Server 2013
[]
Use one of the following procedures to create or modify a call park orbit range. 
  
### To use Lync Server Control Panel to create or modify a range of numbers for parking calls

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Features** and then click **Call Park**.
    
4. On the **Call Park** page, do one of the following: 
    
  - To create a new orbit range, click **New**. In **Name**, type an identifying name for this range of numbers.
    
    > [!NOTE]
    > After you commit the orbit range to the database, you cannot change this name. 
  
  - To modify an existing orbit range, type all or part of the name of the orbit range in the search field. In the resulting list of orbits, click the orbit you want, click **Edit**, and then click **Show details**.
    
5. In the first **Number range** field, type the beginning number of the range of extensions for this call park orbit, and in the second **Number range** field, type the ending number of the range. 
    
    > [!NOTE]
    >  The beginning number of the range must be less than or equal to the ending number of the range. >  The value of the beginning number of the range must be the same length as the ending number of the range. >  The orbit range must be unique. This range cannot overlap with any other range. >  If the orbit range begins with the character \* or #, the range must be greater than 100. >  Valid values: Must match the regular expression string ([\\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). This means the value must be a string beginning with either the character \* or # or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or #, the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters (for example, "#6000", "\*92000", "\*95551212", and "915551212"). If the first character is not \* or #, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9 (for example, "915551212", "41212", "300"). >  You should not have more than a total of 50,000 orbits per pool. Each orbit range typically encompasses 100 or fewer orbits, but it can be much larger as long as it includes fewer than 10,000 orbits. For example, instead of specifying a starting number of "7000000" and an ending number of "8000000," consider specifying a starting number of "7000000" and an ending number of "7000100." 
  
6. In **FQDN of destination server**, click the fully qualified domain name (FQDN) or service ID of the Application service that hosts the Call Park application. All calls parked to numbers within the range specified by the start number and end number in the orbit range will be routed to this server or pool.
    
7. Click **Commit**.
    
### To use Windows PowerShell to create or modify a range of numbers for parking calls

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
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

#### 

[Delete a Call Park orbit range in Lync Server 2013](delete-a-call-park-orbit-range.md)
#### 

[New-CsCallParkOrbit](new-cscallparkorbit.md)
  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)

