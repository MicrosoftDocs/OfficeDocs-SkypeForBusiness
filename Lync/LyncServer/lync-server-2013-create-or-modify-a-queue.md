---
title: 'Lync Server 2013: Create or modify a queue'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a queue
ms:assetid: b9d6366a-839f-4651-a01d-9254546cadeb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205207(v=OCS.15)
ms:contentKeyID: 48185247
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a queue in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Use one of the following procedures to create or modify a queue.

<div>

## To use Lync Server Control Panel to create or modify a queue

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
    <div>
    

    > [!NOTE]  
    > If you are one of the delegated Response Group Managers for a managed workflow, you can create or modify response group queues and assign them to the workflows that you manage.

    
    </div>

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Response Groups**, and then click **Queue**.

4.  On the **Queue** page, do one of the following:
    
      - To create a new queue, click **New**. In **Select a Service**, type part or all of the name of the **ApplicationServer** service where you want to add the queue in the search field. In the resulting list of services, click the service that you want, and then click **OK**.
    
      - To modify an existing queue, type all or part of the queue name in the search field. In the resulting list of queues, click the queue that you want, click **Edit**, and then click **Show details**.

5.  In **Name**, type an identifying name for the queue.

6.  In **Description**, type a description for the queue.

7.  In **Groups**, specify the groups you want to assign to the queue. Do one of the following:
    
      - To add a group to the queue, click **Select**. In the **Select Groups** search field, type all or part of the name of the agent group that you want to assign to the queue, click the agent group that you want, and then click **OK**.
    
      - To remove a group from the queue, in the list of agent groups, click the group that you want to remove, and then click **Remove**.
    
      - To change the order in which agents are searched, in the list of agent groups, click a group, and then click the up arrow or down arrow.
        
        <div>
        

        > [!NOTE]  
        > When the server searches for an available agent for the queue, it uses group order. That is, the first group in the list is searched first, followed by the second group in the list, and so on.

        
        </div>

8.  To specify a maximum period of time for a caller to wait on hold before an agent answers the call, select the **Enable queue time-out** check box, and then do the following:
    
    1.  In **Time-out period (seconds)**, specify the maximum number of seconds a caller waits for an agent to answer the call.
    
    2.  In **Call Action**, select the action that occurs when a call times out as follows:
    
    <!-- end list -->
    
      - To disconnect the call after the timeout, click **Disconnect**.
    
      - To forward the call to voice mail, click **Forward to voice mail**, and then in the **SIP address** field, type a voice mail address in the format sip:\<username\>@\<domainname\> (for example, sip:bob@contoso.com).
    
      - To forward the call to another telephone number, click **Forward to telephone number**, and then in the **SIP address** field, type the telephone number in the format sip:\<number\>@\<domainname\> (for example, sip:+14255550121@contoso.com).
    
      - To forward the call to another user, click **Forward to SIP address**, and then in the **SIP address** field, type the URI for the user in the format sip:\<username\>@\<domainname\>.
    
      - To forward the call to another queue, click **Forward to another queue**, and then browse to the queue that you want to use.

9.  To specify a maximum number of calls that the queue can hold, select the **Enable queue overflow** check box, and then do the following:
    
    1.  In **Maximum number of calls**, select the maximum number of calls that you want the queue to hold.
    
    2.  In **Forward the call**, select which call is to be forwarded when the queue is full: **Newest Call** or **Oldest Call**.
    
    3.  In **Call action**, select the action that occurs when the overflow threshold is met as follows:
    
    <!-- end list -->
    
      - To disconnect the call after the timeout, click **Disconnect**.
    
      - To forward the call to voice mail, click **Forward to voice mail**, and then in the **SIP address** field, type a voice mail address in the format sip:\<username\>@\<domainname\> (for example, sip:bob@contoso.com).
    
      - To forward the call to another telephone number, click **Forward to telephone number**, and then in the **SIP address** field, type the telephone number in the format sip:\<number\>@\<domainname\> (for example, sip:+14255550121@contoso.com).
    
      - To forward the call to another user, click **Forward to SIP address**, and then in the **SIP address** field, type the URI for the user in the format sip:\<username\>@\<domainname\>.
    
      - To forward the call to another queue, click **Forward to another queue**, and then browse to the queue that you want to use.

10. Click **Commit**.

</div>

<div>

## To use Windows PowerShell to create or modify a queue

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
    <div>
    

    > [!NOTE]  
    > If you are one of the delegated Response Group Managers for a managed workflow, you will be able to create agent groups and queues, and assign agent groups to queues.

    
    </div>

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Create the prompt to be played when the queue timeout threshold is met, and save it in a variable. At the command line, run:
    
        $promptTO = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    For example:
    
        "All agents are currently busy. Please call back later."
    
    <div>
    

    > [!NOTE]  
    > To use an audio file for the prompt, use the <STRONG>Import-CsRgsAudioFile</STRONG> cmdlet. For details, see <A href="https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile">Import-CsRgsAudioFile</A>.

    
    </div>

4.  Define the action to be taken when the queue timeout threshold is met, and save it in a variable. At the command line, run:
    
        $actionTO = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
    
    <div>
    

    > [!NOTE]  
    > For details about possible actions and their syntax, see <A href="https://docs.microsoft.com/powershell/module/skype/New-CsRgsCallAction">New-CsRgsCallAction</A>.

    
    </div>
    
    For example:
    
        $action = New-CsRgsCallAction -Prompt $promptTO -Action Terminate

5.  Create the prompt to be played when the queue overflow threshold is met, and save it in a variable. At the command line, run:
    
        $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    For example:
    
        $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "Too many calls are waiting. Please call back later."
    
    <div>
    

    > [!NOTE]  
    > To use an audio file for the prompt, use the <STRONG>Import-CsRgsAudioFile</STRONG> cmdlet. For details, see <A href="https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile">Import-CsRgsAudioFile</A>.

    
    </div>

6.  Define the action to be taken when the queue overflow threshold is met, and save it in a variable. At the command line, run:
    
        $actionOV = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
    
    <div>
    

    > [!NOTE]  
    > For details about possible actions and their syntax, see <A href="https://docs.microsoft.com/powershell/module/skype/New-CsRgsCallAction">New-CsRgsCallAction</A>.

    
    </div>
    
    For example:
    
        $action = New-CsRgsCallAction -Prompt $promptOV -Action Terminate

7.  Retrieve the service name for the Response Group service and assign it to a variable. At the command line, run:
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -Like "*RGS*"}).ServiceId;

8.  Get the identity of the agent group to be assigned to the queue. At the command line, run:
    
        $agid = (Get-CsRgsAgentGroup -Name "Help Desk").Identity;
    
    <div>
    

    > [!NOTE]  
    > For details about creating the agent group, see <A href="https://docs.microsoft.com/powershell/module/skype/New-CsRgsAgentGroup">New-CsRgsAgentGroup</A>

    
    </div>

9.  Create the queue. At the command line, run:
    
        $q = New-CsRgsQueue -Parent <saved service ID from previous step> -Name "<name of queue>" [-Description "<description for queue>"] [-TimeoutThreshold <# seconds before call times out>] [-TimeoutAction <saved timeout action>] [-OverflowThreshold <# calls queue can hold>] [-OverflowCandidate <call to be acted on when overflow threshold met>] [-OverflowAction <saved overflow action>] [-AgentGroupIDList(<agent group identity>)];
    
    For example:
    
        $q = New-CsRgsQueue -Parent $serviceId -Name "Help Desk" -Description "Contoso Help Desk" -TimeoutThreshold 300 -TimeoutAction $actionTO -OverflowThreshold 10 -OverflowCandidate NewestCall -OverflowAction $actionOV -AgentGroupIDList($agid.Identity;

10. Confirm that the queue is created. Run:
    
        Get-CsRgsQueue -Name "Help Desk"

</div>

<div>

## See Also


[New-CsRgsQueue](https://docs.microsoft.com/powershell/module/skype/New-CsRgsQueue)  
[Set-CsRgsQueue](https://docs.microsoft.com/powershell/module/skype/Set-CsRgsQueue)  
[New-CsRgsPrompt](https://docs.microsoft.com/powershell/module/skype/New-CsRgsPrompt)  
[New-CsRgsCallAction](https://docs.microsoft.com/powershell/module/skype/New-CsRgsCallAction)  
[Get-CsRgsQueue](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsQueue)  
[Import-CsRgsAudioFile](https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile)  
[Remove-CsRgsQueue](https://docs.microsoft.com/powershell/module/skype/Remove-CsRgsQueue)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

