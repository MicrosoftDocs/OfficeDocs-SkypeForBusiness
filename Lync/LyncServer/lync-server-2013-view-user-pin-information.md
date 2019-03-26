---
title: 'Lync Server 2013: View user PIN information'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: View user PIN information
ms:assetid: 59e38117-8112-4851-82ac-a746ffa0f89d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688067(v=OCS.15)
ms:contentKeyID: 49733661
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View user PIN information in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

To join a dial-in conference as an authenticated user, a Lync Server 2013 user with Active Directory Domain Services (AD DS) credentials requires a personal identification number (PIN). You can view a user’s PIN information from Lync Server 2013 Control Panel.

<div>


> [!NOTE]  
> You can view PIN status information such as whether the PIN has been set or when the PIN was last changed, but you cannot see the current PIN by looking at the PIN status. If a user has lost their PIN, you can reset it by following the procedures in <A href="lync-server-2013-set-a-user-s-dial-in-conferencing-pin.md">Set a user's dial-in conferencing PIN in Lync Server 2013</A>



</div>

<div>

## To view a user’s PIN in Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  Use one of the following methods to locate a user:
    
      - In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account, and then click **Find**.
    
      - If you have a saved query, click the **Open query** icon, use the **Open** dialog box to retrieve the query (a .usf file), and then click **Find**.

5.  (Optional) Specify additional search criteria to narrow the results:
    
    1.  Click **Add Filter**.
    
    2.  Enter the user property by typing it or by clicking the arrow in the drop-down list to select the property.
    
    3.  In the **Equal to** drop-down list, click the operator (for example, **Equal to** or **Not equal to**).
    
    4.  Depending on the user property you selected, enter the criteria that you want to use to filter the search results by typing it or by clicking the arrow in the drop-down list.
        
        <div>
        

        > [!TIP]  
        > To add additional search clauses to your query, click <STRONG>Add Filter</STRONG>.

        
        </div>
    
    5.  Click **Find**.
    
    <div>
    

    > [!NOTE]  
    > If the PIN is locked, you must unlock the PIN before you can set it. To unlock the PIN, click the user, click <STRONG>Action</STRONG>, and then click <STRONG>Unlock PIN</STRONG>.

    
    </div>

6.  Click a user in the search results, click **Action**, and then click **View PIN status**.

</div>

<div>

## Viewing User PIN Information by Using Windows PowerShell cmdlets

You can view user PIN information by using the Get-CsClientPinInfo cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To view user PIN information

  - To view PIN information for a user, type a command similar to the following in the Lync Server Management Shell and then press ENTER:
    
        Get-CsClientPinInfo -Identity "Ken Myer"
    
    That will return information similar to this:
    
        Identity          : sip:kenmyer@litwareinc.com
        IsPinSet          : False
        IsLockedOut       : False
        LastPinChangeTime : 9/25/2012 1:35:03 PM
        PinExpirationTime :

</div>

For more information, see the help topic for the [Get-CsConferenceDisclaimer](https://docs.microsoft.com/powershell/module/skype/Get-CsConferenceDisclaimer) cmdlet.

</div>

<div>

## See Also


[Set a user's dial-in conferencing PIN in Lync Server 2013](lync-server-2013-set-a-user-s-dial-in-conferencing-pin.md)  
[Lock or unlock a user PIN in Lync Server 2013](lync-server-2013-lock-or-unlock-a-user-pin.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

