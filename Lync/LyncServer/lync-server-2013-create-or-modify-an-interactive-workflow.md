---
title: 'Lync Server 2013: Create or modify an interactive workflow'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify an interactive workflow
ms:assetid: bc7bb1bc-bf6a-4636-ae93-c56fa22613fa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205213(v=OCS.15)
ms:contentKeyID: 48185260
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify an interactive workflow in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-09-11_

Use one of the following procedures to create or modify an interactive workflow.

<div>


> [!NOTE]  
> You can use Lync Server Management Shell or the Response Group Configuration Tool to create and modify interactive workflows. You can access the Response Group Configuration Tool from Lync Server Control Panel, or by opening the webpage directly from a web browser by typing the following URL: <STRONG>https://</STRONG>&lt;webPoolFqdn&gt;<STRONG>/RgsConfig</STRONG>.



</div>

<div>

## To use Response Group Configuration Tool to create or modify an Interactive workflow

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Response Groups**, and then click **Workflow**.

4.  On the **Workflow** page, click **Create or edit a workflow**.

5.  In the **Select a Service** search field, type all or part of the name of the **ApplicationServer** service that hosts the workflow that you want to create or modify. In the resulting list of services, click the service that you want, and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > The Response Group Configuration Tool opens. You can also open the Response Group Configuration Tool directly from a web browser by typing the following URL: <STRONG>https://</STRONG>&lt;webPoolFqdn&gt;<STRONG>/RgsConfig</STRONG>.

    
    </div>

6.  Do one of the following:
    
      - Under **Create a New Workflow**, next to **Interactive**, click **Create**.
    
      - Under **Manage an Existing Workflow**, locate the workflow you want to change, and then under **Action**, click **Edit**.

7.  If you are not ready for users to start calling the workflow, clear the **Activate the workflow** check box.
    
    <div>
    

    > [!NOTE]  
    > If you are to creating a managed workflow, you need to select <STRONG>Activate the workflow</STRONG>. After you save the active, managed workflow, you can then modify and deactivate it.

    
    </div>

8.  To allow federated users to call the group, select the **Enable for federation** check box. You must also have an external access policy that applies to the Response Group application configured for federation.
    
    <div>
    

    > [!NOTE]  
    > The global external access policy applies to the Response Group application. You can configure the global policy for response group federation by using Lync Server Control Panel or by using the <STRONG>Set-CsExternalAccessPolicy</STRONG> cmdlet to set the EnableOutsideAccess parameter to True. Keep in mind that global policy settings apply to all users unless they are assigned a site or user policy. Therefore, before changing this setting for response groups, make sure that the federation setting meets the requirements of your organization. For details about how policies apply to users, see <A href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Manage external access policy in Lync Server 2013</A>. For details about the federation setting, see <STRONG>Set-CsExternalAccessPolicy</STRONG> in Lync Server Management Shell documentation.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > Users who are hosted in Lync Online can’t place calls to response groups that are hosted in an on-premise deployment. This is true in both hybrid deployments and in cases where an on-premise deployment is federated with a Lync Online deployment.

    
    </div>

9.  To hide the identity of agents during calls, select the **Enable agent anonymity** check box.
    
    <div>
    

    > [!NOTE]  
    > Anonymous calls cannot start with instant messaging (IM) or video, although the agent or the caller can add IM and video after the call is established. An anonymous agent can also put calls on hold, transfer calls (both blind and consultative transfers), and park and retrieve calls. Anonymous calls do not support conferencing, application sharing and desktop sharing, file transfer, whiteboarding and data collaboration, and call recording. Agents using the Lync VDI Plugin can receive incoming calls anonymously, but they cannot make outgoing calls anonymously.

    
    </div>

10. Under **Enter the address of the group that will receive the calls**, type the primary SIP uniform resource identifier (URI) address of the group that will answer calls to the workflow.

11. In **Display name**, type the name that you want to display for the workflow (for example, Sales IVR Response Group).
    
    <div>
    

    > [!NOTE]  
    > Do not include the "&lt;" or "&gt;" characters in the display name. Do not use the following display names because they are reserved: RGS Presence Watcher or Announcement Service.

    
    </div>

12. In **Telephone number**, type the line URI for the response group (for example, +14255550165).

13. In **Display number**, type the number as you want it to appear for the response group (for example, +1 (425) 555-0165).

14. (Optional) In **Description**, type a description for the workflow that you want to appear on the contact card in the Lync client.

15. In **Workflow Type**, select **Managed** if this workflow will be managed by a Response Group Manager. Do the following to assign Response Group Managers to the workflow:
    
    1.  Type the SIP URI of a manager for this workflow, and click **Add**..
    
    2.  Type the SIP URI of additional managers to add to the workflow, and click **Add**..
    
    <div>
    

    > [!IMPORTANT]  
    > Every user who is designated as a manager of a response group must be assigned the CsResponseGroupManager role. If users are not assigned this role, they cannot manage response groups.

    
    </div>

16. Under **Step 2 Select a Language**, click the language to use for speech recognition and text-to-speech.

17. If you want to configure a welcome message, under **Step 3 Configure a Welcome Message**, select the **Play a welcome message** check box, and then do one of the following:
    
      - To enter the welcome message as text that is converted to speech for callers, click **Use text-to-speech**, and then type the welcome message in the text box.
        
        <div>
        

        > [!NOTE]  
        > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message.

        
        </div>
    
      - To use a Wave or Windows Media Audio file recording for the welcome message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the audio file that you want to use, and then click **Open**. Click **Upload** to load the audio file.
        
        <div>
        

        > [!NOTE]  
        > All user-provided audio files must meet certain requirements. For details about supported file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

18. Under **Step 4 Specify Your Business Hours**, in the **Your time zone** box, click the time zone of the workflow.
    
    <div>
    

    > [!NOTE]  
    > The time zone is the time zone where the callers and agents of the workflow reside. It is used to calculate the open and close hours. For example, if the workflow is configured to use the North American Eastern Time zone and the workflow is scheduled to open at 7:00 A.M. and close at 11:00 P.M., the open and close times are assumed to be 7:00 Eastern Time and 11:00 Eastern Time respectively. (You must enter the times in 24-hour time notation.)

    
    </div>

19. Select the type of business hours schedule you want to use by doing one of the following:
    
      - To use a predefined schedule of business hours, click **Use a preset schedule**, and then select the schedule you want to use from the drop-down list.
        
        <div>
        

        > [!NOTE]  
        > You must have defined at least one preset schedule previously to be able to select this option. You define preset schedules by using the <STRONG>New-CSRgsHoursOfBusiness</STRONG> cmdlet. For details, see <A href="lync-server-2013-optional-define-response-group-business-hours.md">(Optional) Define Response Group business hours in Lync Server 2013</A>. When you select a preset schedule, <STRONG>Day</STRONG>, <STRONG>Open</STRONG>, and <STRONG>Close</STRONG> are automatically filled with the days and hours that the response group is available.

        
        </div>
    
      - To use a custom schedule that applies only to this workflow, click **Use a custom schedule**.

20. If you are creating a custom schedule for this workflow, click the check boxes for the days of the week that the response group is available.

21. If you are creating a custom schedule, type the **Open** and **Close** hours when the response group available.
    
    <div>
    

    > [!NOTE]  
    > The <STRONG>Open</STRONG> and <STRONG>Close</STRONG> hours must be in 24-hour time notation. For example, if your office works a 9-to-5 work day and closes at noon for lunch, the business hours are specified as <STRONG>Open</STRONG> 9:00, <STRONG>Close</STRONG> 12:00, <STRONG>Open</STRONG> 13:00, and <STRONG>Close</STRONG> 17:00.

    
    </div>

22. If you want to play a message when the office is not open, select the **Play a message when the response group is outside of business hours** check box, and then specify the message to play by doing one of the following:
    
      - To enter the message as text that is converted to speech for the caller, click **Use text-to-speech**, and then type the message in the text box.
        
        <div>
        

        > [!NOTE]  
        > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message.

        
        </div>
    
      - To use an audio file recording for the message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file.
        
        <div>
        

        > [!NOTE]  
        > All user-provided audio files must meet certain requirements. For details about supported file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

23. Specify how to handle calls after the message is played (if a message is configured):
    
      - To disconnect the call, click **Disconnect Call**.
    
      - To forward the call to voice mail, click **Forward to voice mail**, and then type the voice mail address. The format for the voice mail address is \<username\>@\<domainname\> (for example, bob@contoso.com).
    
      - To forward the call to another user, click **Forward to SIP URI**, and then type a user address. The format for the user address is \<username\>@\<domainname\>.
    
      - To forward the call to another telephone number, click **Forward to telephone number**, and then type the telephone number. The format for the telephone number is \<number\>@\<domainname\> (for example, +14255550121@contoso.com). The domain name is used to route the caller to the correct destination.

24. Under **Step 5 Specify Your Holidays**, click the check boxes for one or more sets of holidays that define the days when the response group is closed for business.
    
    <div>
    

    > [!NOTE]  
    > You need to define holidays and holiday sets before you configure the workflow. Use the <STRONG>New-CsRgsHoliday</STRONG> and <STRONG>New-CsRgsHolidaySet</STRONG> cmdlets to define holidays and holiday sets. For details, see <A href="lync-server-2013-optional-define-response-group-holiday-sets.md">(Optional) Define Response Group holiday sets in Lync Server 2013</A>.

    
    </div>

25. If you want to play a message on holidays, select the **Play a message during holidays** check box, and then specify the message to play by doing one of the following:
    
      - To enter the message as text that is converted to speech for the caller, click **Use text-to-speech**, and then type the message in the text box.
        
        <div>
        

        > [!NOTE]  
        > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message.

        
        </div>
    
      - To use an audio file recording for the message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file.
        
        <div>
        

        > [!NOTE]  
        > All user-provided audio files must meet certain requirements. For details about supported audio file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

26. Specify how to handle calls after the message is played (if a message is configured):
    
      - To disconnect the call, click **Disconnect Call**.
    
      - To forward the call to voice mail, click **Forward to voice mail**, and then type the voice mail address. The format for the voice mail address is \<username\>@\<domainname\> (for example, bob@contoso.com).
    
      - To forward the call to another user, click **Forward to SIP URI**, and then type a user address. The format for the user address is \<username\>@\<domainname\>.
    
      - To forward the call to another telephone number, click **Forward to telephone number**, and then type the telephone number. The format for the telephone number is \<number\>@\<domainname\> (for example, +14255550121@contoso.com). The domain name is used to route the caller to the correct destination.

27. Under **Step 6 Configure Music on Hold**, choose what you want callers to listen to while waiting for an agent by doing one of the following:
    
      - To use the default music on-hold recording, click **Use default**.
    
      - To use an audio file recording for the on-hold music, click **Select a music file**. If you want to upload a new audio file, click the **a music file** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file.
        
        <div>
        

        > [!NOTE]  
        > All user-provided audio files must meet certain requirements. For details about supported file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

28. Under **Step 7 Configure Interactive Voice Response**, under the **The user will hear the following text or recorded message** heading, specify the question to ask callers as follows:
    
      - To enter the question in text format, click **Use text-to-speech**, and type the question in the text box.
        
        <div>
        

        > [!NOTE]  
        > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message.

        
        </div>
        
        <div>
        

        > [!NOTE]  
        > The "#" symbol is translated by the text-to-speech engine as the word "number". If you need to refer to the # key, you should use the key name, rather than the symbol, in your prompt. For example, "To talk to sales, press the pound key."

        
        </div>
    
      - To use a prerecorded audio file that contains the question, click **Select a recording**, and then click the **a recording** link to upload the file. In the new browser window, click **Browse**, select the audio file, and then click **Open**. Click **Upload** to load the file, and then optionally you can type the question in the text box (this enables the question, and the caller’s response, to be forwarded to the responding agent).
        
        <div>
        

        > [!NOTE]  
        > All user-provided audio files must meet certain requirements. For details about supported file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

29. Under **Response 1**, specify the first possible answer to the question by doing the following:
    
    <div>
    

    > [!IMPORTANT]  
    > Do not use quotation marks (") in any voice responses. Quotation marks cause the IVR to fail.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > You can choose to allow callers to answer using speech, alphanumeric keypad input, or both.

    
    </div>
    
      - If you want to allow the caller to respond using speech, enter the answer in **Enter a voice response**.
    
      - If you want to allow the caller to respond by pressing a key on the keypad, in **Digit**, click the keypad digit.

30. Specify whether to route the caller to a queue, or to ask another question as follows:
    
      - To route the caller to a queue, click **Send to a queue**, and in **Select a queue**, click the queue that you want to use.
    
      - To ask another question, click **Ask another question**, and then click **Use text-to-speech** and type the question, or click **Select a recording**. Use the response groupings in this section to specify up to four possible responses to the additional question and the queue to use for each response. To specify a third or fourth possible response, click the **Response 3** check box or the **Response 4** check box.

31. Specify up to three more possible answers to the original question by repeating steps 28 and 29 to specify the possible responses and the action to take for each response. To specify a third or fourth possible answer, click the **Response 3** check box or the **Response 4** check box.

32. Click **Deploy**.

</div>

<div>

## To use Windows PowerShell to create or modify an Interactive workflow

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Retrieve the service name for the Response Group service and assign it to a variable. At the command line, run:
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -like "*RGS*"}).ServiceId;

4.  An interactive workflow requires two or more queues and two or more agent groups. First, create the agent groups. Run:
    
        $AGSupport = New-CsRgsAgentGroup -Parent $serviceId -Name "Technical Support" [-AgentAlertTime "20"] [-ParticipationPolicy "Informal"] [-RoutingMethod LongestIdle] [-AgentsByUri("sip:agent1@contoso.com", "sip:agent2@contoso.com")]
        $AGSales = New-CsRgsAgentGroup -Parent $serviceId -Name "Sales Team" [-AgentAlertTime "20"] [-ParticipationPolicy "Informal"] [-RoutingMethod LongestIdle] [-AgentsByUri("sip:bob@contoso.com", "sip:alice@contoso.com")]

5.  Create the queues. Run:
    
        $QSupport = New-CsRgsQueue -Parent $ServiceId -Name "Contoso Support" -AgentGroupIDList($AG-Support.Identity)
        $QSales = New-CsRgsQueue -Parent $ServiceId -Name "Contoso Sales" -AgentGroupIDList($AG-Sales.Identity)

6.  Create the first response group prompt. Run:
    
        $SupportPrompt = New-CsRgsPrompt -TextToSpeechPrompt "Please be patient while we connect you with Contoso Technical Support."

7.  Then create the action to be performed after the prompt. Run:
    
        $SupportAction = New-CsRgsCallAction -Prompt $SupportPrompt -Action TransferToQueue -QueueID $QSupport.Identity

8.  Create the first response group answer. Run:
    
        $SupportAnswer = New-CsRgsAnswer -Action $SupportAction [-DtmfResponse 1]

9.  Now create the second prompt, call action, and answer. First create the prompt. Run:
    
        $SalesPrompt = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we connect you with Contoso Sales."

10. Create the second call action. Run:
    
        $SalesAction = New-CsRgsCallAction -Prompt $SalesPrompt -Action TransferToQueue -QueueID $QSales.Identity

11. Create the second response group answer. Run:
    
        $SalesAnswer = New-CsRgsAnswer -Action $SalesAction [-DtmfResponse 2]

12. Create the top-level prompt. Run:
    
        $TopLevelPrompt = New-CsRgsPrompt -TextToSpeechPrompt "Thank you for calling Contoso. For Technical Support, press 1. For a Sales Representative, press 2."

13. Create the top-level question. Run:
    
        $TopLevelQuestion = New-CsRgsQuestion -Prompt $TopLevelPrompt [-AnswerList ($SupportAnswer, $SalesAnswer)]

14. Now create the workflow. Run:
    
        $IVRAction = New-CsRgsCallAction -Action TransferToQuestion [-Question $Question]
        $IVRWorkflow = New-CsRgsWorkflow -Parent $ServiceId -Name "Contoso Helpdesk" [-Description "The Contoso Helpdesk line."] -PrimaryUri "sip:helpdesk@contoso.com" [-LineUri tel:+14255554321] [-DisplayNumber "+1 (425) 555-4321"] [-Active $true] [-Anonymous $true] [-DefaultAction $IVRAction] [-Managed $true] [-ManagersByURI ("sip:mindy@contoso.com", "sip:bob@contoso.com")]
    
    <div>
    

    > [!NOTE]  
    > All users who have been designated as manager of a response group must be assigned th CsResponseGroupManager role. If users are not assigned this role, they cannot manage response groups.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

