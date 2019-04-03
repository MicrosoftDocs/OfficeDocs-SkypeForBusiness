---
title: 'Lync Server 2013: Create or modify a Group Call Pickup number range'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a Group Call Pickup number range
ms:assetid: 4b442b98-df6b-4e50-8254-b3be9cde21dd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945627(v=OCS.15)
ms:contentKeyID: 51541472
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a Group Call Pickup number range in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

Use the following procedure to create or modify a call pickup group number range in the call park orbit table.

<div>


> [!NOTE]  
> You must use Lync Server Management Shell to create, modify, remove, and view Group Call Pickup number ranges in the call park orbit table. Group Call Pickup number ranges are not available in Lync Server Control Panel.



</div>

<div>


> [!IMPORTANT]  
> The call pickup group number range must be assigned a type of GroupPickup. Users are enabled for Group Call Pickup only if the group number that they are assigned is type GroupPickup.



</div>

The call pickup group number ranges must comply with the following rules:

  - The beginning number of the range must be less than or equal to the ending number of the range.

  - The value of the beginning number of the range must be the same length as the ending number of the range.

  - The number range must be unique. This range cannot overlap with any other range.

  - If the number range begins with the character \* or \#, the range must be greater than 100.

  - Valid values: Must match the regular expression string (\[\\\*|\#\]?\[1-9\]\\d{0,7})|(\[1-9\]\\d{0,8}). This means the value must be a string beginning with either the character \* or \# or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or \#, the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters (for example, "\#6000", "\*92000", "\*95551212", and "915551212"). If the first character is not \* or \#, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9 (for example, "915551212", "41212", "300").

<div>

## To create or modify a call pickup group range

1.  Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Use **New-CsCallParkOrbit** to create a new range of call pickup group numbers. Use **Set-CsCallParkOrbit** to modify an existing range of call pickup numbers.
    
    At the command line, run:
    
        New-CsCallParkOrbit -Identity <name of call pickup group range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -CallParkService <FQDN or service ID of the Application service that hosts the Call Park application> -Type GroupPickup
    
    For example:
    
        New-CsCallParkOrbit -Identity "Redmond call pickup" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService redmond-applicationserver-1 -Type GroupPickup
    
    The following example shows how to change a range of numbers from call park orbits to call pickup groups.
    
        Set-CsCallParkOrbit -Identity "Redmond call pickup" -Type GroupPickup
    
    <div>
    

    > [!IMPORTANT]  
    > Use this cmdlet to change the type assigned to number ranges only if you initially specified the incorrect type and the group range is not yet in use. If you change the number range from CallPark to GroupPickup or vice versa and the number range is already in use, either Call Park or Group Call Pickup will stop working for that number range. For example, if you change a number range from CallPark to GroupPick, the Call Park application can no longer use that range of orbits to park calls.

    
    </div>

</div>

<div>

## See Also


[Delete a Call Park orbit range in Lync Server 2013](lync-server-2013-delete-a-call-park-orbit-range.md)  


[New-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/New-CsCallParkOrbit)  
[Set-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/Set-CsCallParkOrbit)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

