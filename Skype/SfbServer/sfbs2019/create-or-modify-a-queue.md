---
title: "Create or modify a queue in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b9d6366a-839f-4651-a01d-9254546cadeb
description: "Use one of the following procedures to create or modify a queue."
---

# Create or modify a queue in Lync Server 2013
[]
Use one of the following procedures to create or modify a queue.
  
### To use Lync Server Control Panel to create or modify a queue

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
    > [!NOTE]
    > If you are one of the delegated Response Group Managers for a managed workflow, you can create or modify response group queues and assign them to the workflows that you manage. 
  
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Response Groups**, and then click **Queue**.
    
4. On the **Queue** page, do one of the following: 
    
  - To create a new queue, click **New**. In **Select a Service**, type part or all of the name of the **ApplicationServer** service where you want to add the queue in the search field. In the resulting list of services, click the service that you want, and then click **OK**.
    
  - To modify an existing queue, type all or part of the queue name in the search field. In the resulting list of queues, click the queue that you want, click **Edit**, and then click **Show details**.
    
5. In **Name**, type an identifying name for the queue.
    
6. In **Description**, type a description for the queue.
    
7. In **Groups**, specify the groups you want to assign to the queue. Do one of the following: 
    
  - To add a group to the queue, click **Select**. In the **Select Groups** search field, type all or part of the name of the agent group that you want to assign to the queue, click the agent group that you want, and then click **OK**.
    
  - To remove a group from the queue, in the list of agent groups, click the group that you want to remove, and then click **Remove**.
    
  - To change the order in which agents are searched, in the list of agent groups, click a group, and then click the up arrow or down arrow.
    
    > [!NOTE]
    > When the server searches for an available agent for the queue, it uses group order. That is, the first group in the list is searched first, followed by the second group in the list, and so on. 
  
8. To specify a maximum period of time for a caller to wait on hold before an agent answers the call, select the **Enable queue time-out** check box, and then do the following: 
    
1. In **Time-out period (seconds)**, specify the maximum number of seconds a caller waits for an agent to answer the call.
    
2. In **Call Action**, select the action that occurs when a call times out as follows:
    
  - To disconnect the call after the timeout, click **Disconnect**.
    
  - To forward the call to voice mail, click **Forward to voice mail**, and then in the **SIP address** field, type a voice mail address in the format sip:  _\<username\>_@ _\<domainname\>_ (for example, sip:bob@contoso.com). 
    
  - To forward the call to another telephone number, click **Forward to telephone number**, and then in the **SIP address** field, type the telephone number in the format sip:  _\<number\>_@ _\<domainname\>_ (for example, sip:+14255550121@contoso.com). 
    
  - To forward the call to another user, click **Forward to SIP address**, and then in the **SIP address** field, type the URI for the user in the format sip:  _\<username\>_@ _\<domainname\>_.
    
  - To forward the call to another queue, click **Forward to another queue**, and then browse to the queue that you want to use.
    
9. To specify a maximum number of calls that the queue can hold, select the **Enable queue overflow** check box, and then do the following: 
    
1. In **Maximum number of calls**, select the maximum number of calls that you want the queue to hold. 
    
2. In **Forward the call**, select which call is to be forwarded when the queue is full: **Newest Call** or **Oldest Call**.
    
3. In **Call action**, select the action that occurs when the overflow threshold is met as follows:
    
  - To disconnect the call after the timeout, click **Disconnect**.
    
  - To forward the call to voice mail, click **Forward to voice mail**, and then in the **SIP address** field, type a voice mail address in the format sip:  _\<username\>_@ _\<domainname\>_ (for example, sip:bob@contoso.com). 
    
  - To forward the call to another telephone number, click **Forward to telephone number**, and then in the **SIP address** field, type the telephone number in the format sip:  _\<number\>_@ _\<domainname\>_ (for example, sip:+14255550121@contoso.com). 
    
  - To forward the call to another user, click **Forward to SIP address**, and then in the **SIP address** field, type the URI for the user in the format sip:  _\<username\>_@ _\<domainname\>_.
    
  - To forward the call to another queue, click **Forward to another queue**, and then browse to the queue that you want to use.
    
10. Click **Commit**.
    
### To use Windows PowerShell to create or modify a queue

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
    > [!NOTE]
    > If you are one of the delegated Response Group Managers for a managed workflow, you will be able to create agent groups and queues, and assign agent groups to queues. 
  
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Create the prompt to be played when the queue timeout threshold is met, and save it in a variable. At the command line, run:
    
  ```
  $promptTO = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
  ```

    For example:
    
  ```
  "All agents are currently busy. Please call back later."
  ```

    > [!NOTE]
    > To use an audio file for the prompt, use the **Import-CsRgsAudioFile** cmdlet. For details, see [Import-CsRgsAudioFile](import-csrgsaudiofile.md). 
  
4. Define the action to be taken when the queue timeout threshold is met, and save it in a variable. At the command line, run:
    
  ```
  $actionTO = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
  ```

    > [!NOTE]
    > For details about possible actions and their syntax, see [New-CsRgsCallAction](new-csrgscallaction.md). 
  
    For example:
    
  ```
  $action = New-CsRgsCallAction -Prompt $promptTO -Action Terminate
  ```

5. Create the prompt to be played when the queue overflow threshold is met, and save it in a variable. At the command line, run:
    
  ```
  $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
  ```

    For example:
    
  ```
  $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "Too many calls are waiting. Please call back later."
  ```

    > [!NOTE]
    > To use an audio file for the prompt, use the **Import-CsRgsAudioFile** cmdlet. For details, see [Import-CsRgsAudioFile](import-csrgsaudiofile.md). 
  
6. Define the action to be taken when the queue overflow threshold is met, and save it in a variable. At the command line, run:
    
  ```
  $actionOV = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
  ```

    > [!NOTE]
    > For details about possible actions and their syntax, see [New-CsRgsCallAction](new-csrgscallaction.md). 
  
    For example:
    
  ```
  $action = New-CsRgsCallAction -Prompt $promptOV -Action Terminate
  ```

7. Retrieve the service name for the Response Group service and assign it to a variable. At the command line, run:
    
  ```
  $serviceId="service:"+(Get-CSService | ?{$_.Applications -Like "*RGS*"}).ServiceId;
  ```

8. Get the identity of the agent group to be assigned to the queue. At the command line, run:
    
  ```
  $agid = (Get-CsRgsAgentGroup -Name "Help Desk").Identity;
  ```

    > [!NOTE]
    > For details about creating the agent group, see [New-CsRgsAgentGroup](new-csrgsagentgroup.md)
  
9. Create the queue. At the command line, run:
    
  ```
  $q = New-CsRgsQueue -Parent <saved service ID from previous step> -Name "<name of queue>" [-Description "<description for queue>"] [-TimeoutThreshold <# seconds before call times out>] [-TimeoutAction <saved timeout action>] [-OverflowThreshold <# calls queue can hold>] [-OverflowCandidate <call to be acted on when overflow threshold met>] [-OverflowAction <saved overflow action>] [-AgentGroupIDList(<agent group identity>)];
  ```

    For example:
    
  ```
  $q = New-CsRgsQueue -Parent $serviceId -Name "Help Desk" -Description "Contoso Help Desk" -TimeoutThreshold 300 -TimeoutAction $actionTO -OverflowThreshold 10 -OverflowCandidate NewestCall -OverflowAction $actionOV -AgentGroupIDList($agid.Identity;
  ```

10. Confirm that the queue is created. Run:
    
  ```
  Get-CsRgsQueue -Name "Help Desk"
  ```

## See also

#### 

[New-CsRgsQueue](new-csrgsqueue.md)
  
[Set-CsRgsQueue](set-csrgsqueue.md)
  
[New-CsRgsPrompt](new-csrgsprompt.md)
  
[New-CsRgsCallAction](new-csrgscallaction.md)
  
[Get-CsRgsQueue](get-csrgsqueue.md)
  
[Import-CsRgsAudioFile](import-csrgsaudiofile.md)
  
[Remove-CsRgsQueue](remove-csrgsqueue.md)

