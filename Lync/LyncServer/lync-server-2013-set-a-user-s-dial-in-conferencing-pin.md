---
title: "Lync Server 2013: Set a user's dial-in conferencing PIN"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Set a user's dial-in conferencing PIN
ms:assetid: 4252b5a5-4267-4513-b18e-0253a8d66f72
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520985(v=OCS.15)
ms:contentKeyID: 48183970
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set a user's dial-in conferencing PIN in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-10_

To join a dial-in conference as an authenticated user, a Lync Server 2013 user with Active Directory Domain Services (AD DS) credentials requires a personal identification number (PIN). If a user forgets the dial-in conferencing PIN or has not set the PIN by using Lync Server, you can set the user’s PIN from Lync Server Control Panel. You can automatically generate the PIN or create one manually.

<div>


> [!NOTE]  
> Specific characteristics of the PIN, such as its minimum length, can be configured as a policy. In addition to the global policy, you can configure a PIN policy for individual sites or users. For details about configuring a PIN policy, see <A href="lync-server-2013-configure-dial-in-conferencing-personal-identification-number-pin-rules.md">Configure dial-in conferencing personal identification number (PIN) rules in Lync Server 2013</A>.



</div>

<div>

## To set a user’s PIN

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

6.  Click a user in the search results, click **Action**, and then click **Set PIN**.

7.  In the **Set PIN** dialog box, do one of the following:
    
      - To allow Lync Server 2013 to generate the user’s PIN, select **Automatically generate a valid PIN** (the default).
    
      - To create your own PIN, click **Manually enter a specific PIN**, click the text box, and then type a PIN that meets the PIN requirements specified in your PIN policy settings.

8.  Click **OK**.

9.  In **Set PIN**, do one of the following:
    
      - Select the **Show PIN** check box to see the PIN, and then copy the PIN and communicate it to the user using your organization's preferred method.
    
      - Click **Open my email application to send the new PIN to the user** to send the PIN by email. If Microsoft Office Outlook is your email client, the PIN is automatically copied into a new email message. If you use a different email client, select the **Show PIN** check box to see the PIN and then copy it into your email message.

10. Click **Close**.

</div>

<div>

## Assigning a User PIN by Using Windows PowerShell Cmdlets

You can assign PIN numbers can also be assigned by using the Set-CsClientPin cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To auto-assign a PIN number to a user

  - The following command assigns a PIN number to the user Ken Myer. Because the Pin parameter is not included, Lync Server will automatically generate and assign the PIN number.
    
        Set-CsClientPin -Identity "Ken Myer" 

</div>

<div>

## To assign a specific PIN number to a user

  - This command uses the Pin parameter to assign the PIN number 121989 to the user Ken Myer.
    
        Set-CsClientPin -Identity "Ken Myer" -Pin 121989

</div>

For more information, see the help topic for the [Set-CsClientPin](https://docs.microsoft.com/powershell/module/skype/Set-CsClientPin) cmdlet.

</div>

<div>

## See Also


[Dial-in Access Number](https://technet.microsoft.com/en-us/library/gg133674\(v=ocs.15\))  


[Configure dial-in conferencing personal identification number (PIN) rules in Lync Server 2013](lync-server-2013-configure-dial-in-conferencing-personal-identification-number-pin-rules.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

