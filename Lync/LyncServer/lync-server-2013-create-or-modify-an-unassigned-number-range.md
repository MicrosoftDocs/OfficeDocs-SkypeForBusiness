---
title: 'Lync Server 2013: Create or modify an unassigned number range'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify an unassigned number range
ms:assetid: a102b226-0460-4d5c-82f9-79b8444fa958
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412748(v=OCS.15)
ms:contentKeyID: 48185013
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify an unassigned number range in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Use one of the following procedures to configure unassigned number ranges for the Announcement application.

<div>


> [!IMPORTANT]  
> Before you configure the unassigned number table, you must have already defined one or more announcements or set up an Exchange Unified Messaging (UM) Auto Attendant.



</div>

<div>

## To use Lync Server Control Panel to configure unassigned phone numbers

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Features**, and then click **Unassigned Number**.

4.  On the **Unassigned Number** page, do one of the following:
    
      - To create a new number range, click **New**. In **Name**, type an identifying name for this range of numbers.
        
        <div>
        

        > [!NOTE]  
        > After you commit the new unassigned number range to the database, you cannot change this name.

        
        </div>
    
      - To modify an existing number range, type all or part of the name of the number range in the search field. In the resulting list of number ranges, click the name you want, click **Edit**, and then click **Show details**.

5.  In the first **Number range** field, type the beginning number of the range, and in the second **Number range** field, type the ending number of the range.
    
    <div>
    

    > [!NOTE]  
    > <UL>
    > <LI>
    > <P>The beginning number of the range must be less than or equal to the ending number of the range.</P>
    > <LI>
    > <P>If the beginning number of the range or the ending number of the range includes an extension number, both the beginning number and the ending number of the range must include an extension, and the extension number must be the same for both the beginning number and the ending number.</P>
    > <LI>
    > <P>The number must match the regular expression (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. This means the number may begin with the string tel: (if you don’t specify that string, it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by an extension in the format ;ext= followed by the extension number.</P></LI></UL>

    
    </div>

6.  In **Announcement service**, do one of the following:
    
      - Click **Announcement**.
    
      - Click **Exchange UM**.

7.  If, in the previous step, you clicked **Announcement**, do the following:
    
    1.  Under **FQDN of destination server**, click **Select**, click the service ID of the Application service that runs the Announcement application that will handle incoming calls to this range of unassigned numbers, and then click **OK**.
    
    2.  In **Announcement**, click the announcement to be played for this range of unassigned numbers.

8.  If, in the previous step, you clicked **Exchange UM**, under **Auto Attendant phone number**, click **Select**, click the phone number to be used for this range of unassigned numbers, and then click **OK**.

9.  Click **OK**.

10. On the **Unassigned Number** page, be sure that the unassigned number ranges are arranged in the order that you want. To change a range's position in the table, click one or more consecutive names in the list of ranges, and then click the up arrow or the down arrow.
    
    <div>
    

    > [!TIP]  
    > Lync Server searches the unassigned number table from top to bottom and uses the first range that matches the unassigned number. If you have overlapping ranges and one range specifies a last resort action, make sure that range is at the bottom of the list.

    
    </div>

11. When you have the unassigned number ranges in the order that you want, click **Commit all**.

</div>

<div>

## To use Windows PowerShell to configure unassigned phone numbers

1.  Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Use **New-CsUnassignedNumber** to create a new unassigned number range. Use **Set-CsUnassignedNumber** to modify an existing unassigned number range.
    
    <div>
    

    > [!TIP]  
    > If you have overlapping ranges and want the ranges to be applied in a specific order, include the Priority parameter. The range with the highest priority will be applied to the call.

    
    </div>
    
    At the command line, do one of the following:
    
      - To create a number range for an Announcement service, run:
        
            New-CsUnassignedNumber -Identity <unique identifier for unassigned number range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -AnnouncementName <announcement name> -AnnouncementService <FQDN or service ID of the Announcement service>
    
      - Or, to create a number range for Exchange UM Auto Attendant, run:
        
            New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <phone number> -Identity <unique identifier for unassigned number range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range>
    
    For example:
    
        New-CsUnassignedNumber -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100" -AnnouncementName "Welcome Announcement" -AnnouncementService ApplicationServer:Redmond.contoso.com
    
    Or
    
        New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber "+12065551234" -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100"
    
    The following example shows how to modify the numbers in an existing unassigned number range:
    
        Set-CsUnassignedNumber -Identity "Unassigned range 1" -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"

</div>

<div>

## See Also


[Delete an unassigned number range in Lync Server 2013](lync-server-2013-delete-an-unassigned-number-range.md)  


[New-CsUnassignedNumber](https://docs.microsoft.com/powershell/module/skype/New-CsUnassignedNumber)  
[Set-CsUnassignedNumber](https://docs.microsoft.com/powershell/module/skype/Set-CsUnassignedNumber)  
[Get-CsUnassignedNumber](https://docs.microsoft.com/powershell/module/skype/Get-CsUnassignedNumber)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

