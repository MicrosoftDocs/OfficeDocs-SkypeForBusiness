---
title: 'Using Start for the Centralized Logging Service to capture logs'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using Start for the Centralized Logging Service to capture logs
ms:assetid: 0512b9ce-7f5b-48eb-a79e-f3498bacf2de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687958(v=OCS.15)
ms:contentKeyID: 49733543
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Start for the Centralized Logging Service to capture logs in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

To capture trace logs using the Centralized Logging Service, you issue a command to begin logging on one or more computers and pools. You also issue parameters that define which computers or pools, what scenarios to run (for example, AlwaysOn, another predefined scenario, or a scenario you have created), what Lync Server components (for example, S4, SipStack) to trace.

To capture the right information, you need to make sure you use the right scenario to collect information that is relevant to the problem. In the Centralized Logging Service, a scenario is the concept of turning logging on based on a collection of server components, logging levels, and flags, which is much more efficient and useful than having to define these elements on a per-server basis. You define and specify a scenario to run and the scenario is run consistently across all servers and pools in the scope of the infrastructure.

The default scenario is called **AlwaysOn**. The intended purpose for AlwaysOn is to run the scenario constantly, as the name of the scenario implies. The AlwaysOn scenario collects Info level information (note that Info logging level includes Fatal, Error, and Warning in addition to Info messages) for many of the most common server components. AlwaysOn collects information before, during, and after a problem occurs. This differs dramatically from the typical behavior of previous logging tools such as OCSLogger. You ran OCSLogger after the problem had already occurred, making your troubleshooting efforts more difficult because the data that you have is reactive, not proactive. If AlwaysOn does not contain the information that you are looking for in order to point to the problem component and indicate a course of action to fix it (which is not likely given the breadth and depth of providers in AlwaysOn), it will indicate a reasonable level of information to determine what else you need to do, such as creating a new scenario, gather other information, run a different search to collect more focused details, and so on.

The Centralized Logging Service provides two ways to issue commands. A number of topics have been focused squarely on using Windows PowerShell through the Lync Server Management Shell. The ability to use a number of complex configurations and commands favors Windows PowerShell for Centralized Logging Service use. Because Windows PowerShell through the Lync Server Management Shell is nearly ubiquitous for all functions in Lync Server, only the Windows PowerShell commands are discussed.

<div>


> [!NOTE]
> If you decide to use the limited command set available from the command line, you can get help with CLSController.exe by typing <CODE>ClsController.exe</CODE>. By default, <STRONG>ClsController.exe</STRONG> is installed in the directory C:\Program Files\Microsoft Lync Server 2013\ClsAgent.



</div>

<div>

## To run Start-CsClsLogging with Windows PowerShell using basic commands

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Start a logging scenario with the Centralized Logging Service by typing the following:
    
        Start-CsClsLogging -Scenario <name of scenario>
    
    For example, to start the **AlwaysOn** scenario, type:
    
        Start-CsClsLogging -Scenario AlwaysOn
    
    <div>
    

    > [!NOTE]
    > The AlwaysOn scenario has no default duration. This scenario will run until you explicitly stop it with the <STRONG>Stop-CsClsLogging</STRONG> cmdlet. For details, see <A href="https://technet.microsoft.com/en-us/library/JJ619180(v=OCS.15)">Stop-CsClsLogging</A>. For all other scenarios, the default duration is 4 hours.

    
    </div>

3.  Press Enter to run the command.
    
    <div>
    

    > [!NOTE]
    > It may take a short amount of time (30 to 60 seconds) for the commands to run and to receive the status back from the computers in your deployment.

    
    </div>
    
    ![Running Start-CsClsLogging.](images/JJ687958.c5be7413-8cef-4de7-9712-944d20cc2fa4(OCS.15).jpg "Running Start-CsClsLogging.")

4.  To start another scenario, use the **Start-CsClsLogging** cmdlet with the name of the additional scenario to run as follows (for example, the scenario **Authentication**):
    
        Start-CsClsLogging -Scenario Authentication
    
    <div>
    

    > [!IMPORTANT]
    > You can have a total of two scenarios running on any given computer at any time. If the command is global in scope, all of the computers in your deployment will run the scenario or scenarios. To start a third scenario, you must stop logging on the computer, pool, site, or global scope that you want to run the new scenario on. If you have started a global scope, you can stop logging for one or both of the scenarios on one or more computers and pools. For details about managing which scenarios are running, see <A href="lync-server-2013-using-stop-for-the-centralized-logging-service.md">Using Stop for the Centralized Logging Service in Lync Server 2013</A> and <A href="https://technet.microsoft.com/en-us/library/JJ619180(v=OCS.15)">Stop-CsClsLogging</A>.

    
    </div>

</div>

<div>

## To run Start-CsClsLogging with Windows PowerShell using advanced commands

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Additional parameters are available to manage the logging commands. You can use –Duration to adjust the length of time for the scenario to run. You also can define –Computers, a list of computer fully qualified domain names (FQDNs) separated by a comma, or –Pools, a comma separated list of FQDNs for pools that you want to run logging on.
    
    You start a logging session for the *UserReplicator* scenario on the pool "pool01.contoso.net". You also define the duration of the logging session at 8 hours. To do this, type:
    
        Start-CsClsLogging -Scenario UserReplicator -Duration 8:00 -Pools "pool01.contoso.net"
    
    The successful execution of this scenario returns a result like the following:
    
    ![Running Start-CsClsLogging.](images/JJ687958.399f0c2e-c08c-40ab-b6c6-381dddc12fe9(OCS.15).jpg "Running Start-CsClsLogging.")
    
    Note that in this example, the AlwaysOn scenario is running and the UserReplicator scenario is running.

</div>

<div>

## See Also


[Overview of the Centralized Logging Service in Lync Server 2013](lync-server-2013-overview-of-the-centralized-logging-service.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

