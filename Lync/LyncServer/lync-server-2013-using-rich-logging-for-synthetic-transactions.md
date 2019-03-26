---
title: 'Lync Server 2013: Using rich logging for synthetic transactions'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Using rich logging for synthetic transactions
ms:assetid: 32714a71-9f42-4d5b-a508-e176d8f08bbf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204798(v=OCS.15)
ms:contentKeyID: 48183812
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using rich logging for synthetic transactions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

Synthetic transactions (introduced in Microsoft Lync Server 2010) provide a way for administrators to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests (which are packaged as a set of Lync Server Windows PowerShell cmdlets) can be conducted manually by an administrator, or they can be automatically run by an application such as System Center Operations Manager.

In Lync Server 2010, synthetic transactions proved extremely useful in helping administrators to identify problems with the system. For example, the **Test-CsRegistration** cmdlet could alert administrators to the fact that some users were having difficulty registering with Lync Server. However, the synthetic transactions were somewhat less useful in helping administrators determine why these users were having difficulty registering with Lync Server. This was due to the fact that the synthetic transactions did not provide detailed logging information that could help administrators troubleshoot problems with Lync Server. At best, the verbose output from a synthetic transaction provided step-by-step information that might enable an administrator to make an educated guess as to where a problem likely occurred.

In Microsoft Lync Server 2013, synthetic transactions have been re-architected to provide rich logging. "Rich logging" means that, for each activity that a synthetic transaction undertakes, information such as this will be recorded:

  - The time that the activity started

  - The time that the activity finished

  - The action that was performed (for example, creating, joining, or leaving a conference; signing on to Lync Server; sending an instant message; and so on)

  - Informational, verbose, warning, or error messages generated when the activity ran

  - SIP registration messages

  - Exception records or diagnostic codes generated when the activity ran

  - The net result of running the activity

This information is automatically generated each time a synthetic transaction is run. However, the information is not automatically displayed or saved to a log file. Instead, administrators who are manually running a synthetic transaction can use the OutLoggerVariable parameter to specify a Windows PowerShell variable in which the information will be stored. From there, administrators can then use a pair of methods that enable them to save and/or view the rich log in either XML or HTML format.

For example, Lync Server 2010 administrators might run the **Test-CsRegistration** cmdlet by using a command similar to the following:

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com

Administrators have the option of including the OutLoggerVariable parameter followed by a variable name of their choosing:

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -OutLoggerVariable RegistrationTest

> [!NOTE]  
> Do not preface the variable name with the $ character. Use a variable name like RegistrationTest and not $RegistrationTest.

The preceding command outputs content similar to the following:

    Target Fqdn   : atl-cs-001.litwareinc.com
    Result        : Failure
    Latency       : 00:00:00
    Error Message : This machine does not have any assigned certificates.
    Diagnosis     :

However, much more detailed information is available for this failure than just the error message shown above. To access that information in HTML format, use a command similar to this in order to save the information stored in the variable RegistrationTest to an HTML file:

    $RegistrationTest.ToHTML() | Out-File C:\Logs\Registration.html

Alternatively, you can use the ToXML() method to save the data to an XML file:

    $RegistrationTest.ToXML() | Out-File C:\Logs\Registration.xml

These files can then be viewed using Internet Explorer, Visual Studio, or any other application capable of opening HTML/XML files.

Synthetic transactions run from inside of System Center Operations Manager will automatically generate these log files for failures. However, these logs will not be generated if the execution fails before Windows PowerShell is able to load and run the synthetic transaction.

> [!IMPORTANT]  
> By default, Lync Server 2013 saves log files to a folder that is not shared. To make these logs readily accessible, you should share this folder (for example, \\\\atl-watcher-001.litwareinc.com\WatcherNode.


</div>

</div>

</div>

</div>

