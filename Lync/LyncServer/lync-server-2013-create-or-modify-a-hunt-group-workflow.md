---
title: 'Lync Server 2013: Create or modify a hunt group workflow'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify a hunt group workflow
ms:assetid: dcb9effb-5d12-4dee-80fc-ab9654222d5a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205321(v=OCS.15)
ms:contentKeyID: 48185596
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a hunt group workflow in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-09-11_

Use one of the following procedures to create or modify a hunt group workflow.

<div>


> [!NOTE]  
> You can use Lync Server Management Shell or the Response Group Configuration Tool to create and modify hunt group workflows. You can access the Response Group Configuration Tool from Lync Server Control Panel, or by opening the webpage directly from a web browser by typing the following URL: <STRONG>https://</STRONG>&lt;webPoolFqdn&gt;<STRONG>/RgsConfig</STRONG>.



</div>

<div>

## To use Response Group Configuration Tool to create or modify a hunt group workflow

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Response Groups**, and then click **Workflow**.

4.  On the **Workflow** page, click **Create or edit a workflow**.

5.  In the **Select a Service** search field, type all or part of the name of the **ApplicationServer** service that hosts the workflow that you want to create or change. In the resulting list of services, click the service that you want, and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > The Response Group Configuration Tool opens. You can also open the Response Group Configuration Tool directly from a web browser by typing the following URL: <STRONG>https://</STRONG>&lt;webPoolFqdn&gt;<STRONG>/RgsConfig</STRONG>.

    
    </div>

6.  Do one of the following:
    
      - Under **Create a New Workflow**, next to **Hunt Group, click Create**.
    
      - Under **Manage an Existing Workflow**, locate the workflow you want to change, and then under **Action**, click **Edit**.

7.  If you are ready for users to start calling the workflow, select **Activate the workflow**.
    
    <div>
    

    > [!NOTE]  
    > If you are to creating a managed workflow, you need to select <STRONG>Activate the workflow</STRONG>. After you save the active, managed workflow, you can then modify and deactivate it.

    
    </div>

8.  To allow federated users to call the group, select the **Enable for federation** check box. You must also have an external access policy that applies to the Response Group application configured for federation.
    
    <div>
    

    > [!NOTE]  
    > The global external access policy applies to the Response Group application. You can configure the global policy for response group federation by using Lync Server Control Panel or by using the <STRONG>Set-CsExternalAccessPolicy</STRONG> cmdlet to set the EnableOutsideAccess parameter to True. Keep in mind that global policy settings apply to all users unless they are assigned a site or user policy. Therefore, before changing this setting for response groups, make sure that the federation setting meets the requirements of your organization. For details about how policies apply to users, see <A href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Manage external access policy in Lync Server 2013</A>. For details about the federation setting, see <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsExternalAccessPolicy">Set-CsExternalAccessPolicy</A>.

    
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
    
    <div>
    

    > [!NOTE]  
    > The primary URI for a workflow is how the workflow is identified and referenced. The SIP URI that you enter is created as a contact object in Active Directory Domain Services. To create the URI, the object must be unique in Active Directory.

    
    </div>

11. In **Display name**, type the name that you want to display for the workflow (for example, Sales Response Group).
    
    <div>
    

    > [!NOTE]  
    > Do not include the "&lt;" or "&gt;" characters in the display name. Do not use the following display names because they are reserved: <STRONG>RGS Presence Watcher</STRONG> or <STRONG>Announcement Service</STRONG>.

    
    </div>

12. Under **Telephone number**, type the line URI for the response group (for example, +14255550165).

13. In **Display number**, type the number as you want it to appear for the response group (for example, +1 (425) 555-0165).

14. (Optional) In **Description**, type a description for the workflow as you want it to appear on the contact card in Lync client.

15. In **Workflow Type**, select **Managed** if this workflow will be managed by a Response Group Manager. Do the following to assign Response Group Managers to the workflow:
    
    1.  Type the SIP URI of a manager for this workflow, and click **Add**.
    
    2.  Type the SIP URI of additional managers to add to the workflow, and click **Add**.
    
    <div>
    

    > [!IMPORTANT]  
    > Every user who is designated as a manager of a response group must be assigned the CsResponseGroupManager role. If users are not assigned this role, they cannot manage response groups.

    
    </div>

16. Under **Step 2 Select a Language**, click the language that you want to use for speech recognition and text-to-speech.

17. If you want to configure a welcome message, under **Step 3 Configure a Welcome Message**, select the **Play a welcome message** check box, and then do one of the following:
    
      - To enter the welcome message as text that is converted to speech for callers, click **Use text-to-speech**, and then type the welcome message in the text box.
        
        <div>
        

        > [!NOTE]  
        > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message.

        
        </div>
    
      - To use a wave (.wav) or Windows Media audio (.wma) file recording for the welcome message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the audio file that you want to use, and then click **Open**. Click **Upload** to load the audio file.
        
        <div>
        

        > [!NOTE]  
        > All user-provided audio files must meet certain requirements. For details about supported file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

18. Under **Step 4 Specify Your Business Hours**, in **Your time zone**, click the time zone for the workflow.
    
    <div>
    

    > [!NOTE]  
    > The time zone is the time zone where the callers and agents of the workflow reside. It is used to calculate the open and close hours. For example, if the workflow is configured to use the North American Eastern Time zone and the workflow is scheduled to open at 7:00 A.M. and close at 11:00 P.M., the open and close times are assumed to be 7:00 Eastern Time and 23:00 Eastern Time respectively. (You must enter the times in 24-hour time notation.)

    
    </div>

19. Select the type of business hours schedule you want to use by doing one of the following:
    
      - To use a predefined schedule of business hours, click **Use a preset schedule**, and then select the schedule you want to use from the drop-down list.
        
        <div>
        

        > [!NOTE]  
        > You must have defined at least one preset schedule previously to be able to select this option. You define preset schedules by using the <STRONG>New-CSRgsHoursOfBusiness</STRONG> cmdlet. For details, see <A href="lync-server-2013-optional-define-response-group-business-hours.md">(Optional) Define Response Group business hours in Lync Server 2013</A>.

        
        </div>
        
        <div>
        

        > [!NOTE]  
        > When you select a preset schedule, <STRONG>Day</STRONG>, <STRONG>Open</STRONG>, and <STRONG>Close</STRONG> are automatically filled with the days and hours that the response group is available.

        
        </div>
    
      - To use a custom schedule that applies only to this workflow, click **Use a custom schedule**.

20. If you are creating a custom schedule for this workflow, click the check boxes for the days of the week that the response group is available.

21. If you are creating a custom schedule, type the **Open** and **Close** hours for each day of the week that the response group available.
    
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
        > All user-provided audio files must meet certain requirements. For details about supported audio file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

23. Specify how to handle calls after the message is played (if a message is configured):
    
      - To disconnect the call, click **Disconnect Call**.
    
      - To forward the call to voice mail, click **Forward to voice mail**, and then type the voice mail address. The format for the voice mail address is \<username\>@\<domainName\> (for example, bob@contoso.com).
    
      - To forward the call to another user, click **Forward to SIP URI**, and then type a user address. The format for the user address is \<username\>@\<domainName\>.
    
      - To forward the call to another telephone number, click **Forward to telephone number**, and then type the telephone number. The format for the telephone number is \<number\>@\<domainName\> (for example, +14255550121@contoso.com). The domain name is used to route the caller to the correct destination.

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
    
      - To forward the call to voice mail, click **Forward to voice mail**, and then type the voice mail address. The format for the voice mail address is \<username\>@\<domainName\> (for example, bob@contoso.com).
    
      - To forward the call to another user, click **Forward to SIP URI**, and then type a user address. The format for the user address is \<username\>@\<domainName\>.
    
      - To forward the call to another telephone number, click **Forward to telephone number**, and then type the telephone number. The format for the telephone number is \<number\>@\<domainName\> (for example, +14255550121@contoso.com). The domain name is used to route the caller to the correct destination.

27. Under **Step 6 Configure a Queue**, in **Select the queue that will receive the calls**, select the queue that you want to hold callers until an agent becomes available.

28. Under **Step 7 Configure Music on Hold**, choose the music you want callers to listen to while waiting for an agent by doing one of the following:
    
      - To use the default music-on-hold recording, click **Use default**.
    
      - To use an audio file recording for the music on hold, click **Select a music file**. If you want to upload a new audio file, click the **a music file** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file.
        
        <div>
        

        > [!NOTE]  
        > All user provided audio files must meet certain requirements. For details about supported audio file formats, see <A href="lync-server-2013-technical-requirements-for-response-group.md">Technical requirements for Response Group in Lync Server 2013</A>.

        
        </div>

29. Click **Deploy**.

</div>

<div>

## To use Windows PowerShell to create or modify a hunt group workflow

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Create the prompt to be played for the welcome message, and save it in a variable. At the command line, run:
    
        $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    For example:
    
        $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to Contoso. Please wait for an available agent."
    
    <div>
    

    > [!NOTE]  
    > To use an audio file for the prompt, use the <STRONG>Import-CsRgsAudioFile</STRONG> cmdlet. For details, see <A href="https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile">Import-CsRgsAudioFile</A>.

    
    </div>

4.  Get the identity of the queue or question where the calls will be directed. At the command line, run:
    
        $qid = (Get-CsRgsQueue -Name "Help Desk").Identity
    
    For details about creating the queue, see [New-CsRgsQueue](https://docs.microsoft.com/powershell/module/skype/New-CsRgsQueue).

5.  Define the default action to be taken when a workflow is opened during business hours, and save it in a variable. At the command line, run:
    
        $actionWM = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken> -QueueID $qid
    
    <div>
    

    > [!NOTE]  
    > For hunt group workflows, the default action must direct the call to a queue. This is parameter is required for active workflows. It is not required for inactive workflows.

    
    </div>
    
    For example:
    
        $actionWM = New-CsRgsCallAction -Prompt $promptWM -Action TransferToQueue -QueueID $qid.Identity

6.  If you want to define business hours and holidays, you need to create them before you create or modify the workflow. For details, see [(Optional) Define Response Group business hours in Lync Server 2013](lync-server-2013-optional-define-response-group-business-hours.md) and [(Optional) Define Response Group holiday sets in Lync Server 2013](lync-server-2013-optional-define-response-group-holiday-sets.md).

7.  If you want to have prompts for calls that are received out of business hours or on holidays, use the **New-CsRgsPrompt** cmdlet to define the prompt, and use the **New-CsRgsCallAction** to define the action to be taken after the prompt. For details, see [New-CsRgsPrompt](https://docs.microsoft.com/powershell/module/skype/New-CsRgsPrompt) and [New-CsRgsCallAction](https://docs.microsoft.com/powershell/module/skype/New-CsRgsCallAction).

8.  Retrieve the service name for the Lync Server Response Group service and assign it to a variable. At the command, run:
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -like "*RGS*"}).ServiceId;

9.  Create or modify the workflow. To create a workflow, use **New-CsRgsWorkflow**. To modify a workflow, use **Set-CsRgsWorkflow**. At the command line, type:
    
        $workflowHG = New-CsRgsWorkflow -Parent <service ID for the Response Group service> -Name "<hunt group name>" [-Description "<hunt group description>"] -PrimaryUri "<SIP address for the workflow>" [-LineUri "<Phone number for the workflow>"] [-DisplayNumber "<Phone number displayed in Lync>"] [-Active <$true | $false>] [-Anonymous <$true | $false>] [-DefaultAction <variable from preceding step>] [-EnabledForFederation <$true | $false>] [-Managed <$true | $false>] [-MangersByUri <SIP addresses for Response Group Managers who can manage the workflow>]
    
    For example:
    
        $workflowHG = New-CsRgsWorkflow -Parent $serviceID -Name "Human Resources" -Description "Human Resources workflow" -PrimaryUri "sip:humanresources@contoso.com" -LineUri "TEL:+14255551219" -DisplayNumber "555-1219" -Active $true -Anonymous $true -DefaultAction $actionWM -EnabledForFederation $false -Managed $true -ManagersByUri "sip:bob@contoso.com", "mindy@contoso.com"
    
    <div>
    

    > [!IMPORTANT]  
    > All users who are designated managers for workflows must be assigned the CsResponseGroupManager role.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > For details about additional optional parameters, see <A href="https://docs.microsoft.com/powershell/module/skype/New-CsRgsWorkflow">New-CsRgsWorkflow</A> or <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsRgsWorkflow">Set-CsRgsWorkflow</A>

    
    </div>

</div>

<div>

## See Also


[(Optional) Define Response Group holiday sets in Lync Server 2013](lync-server-2013-optional-define-response-group-holiday-sets.md)  


[(Optional) Define Response Group business hours in Lync Server 2013](lync-server-2013-optional-define-response-group-business-hours.md)  


[New-CsRgsWorkflow](https://docs.microsoft.com/powershell/module/skype/New-CsRgsWorkflow)  
[Set-CsRgsWorkflow](https://docs.microsoft.com/powershell/module/skype/Set-CsRgsWorkflow)  
[New-CsRgsPrompt](https://docs.microsoft.com/powershell/module/skype/New-CsRgsPrompt)  
[New-CsRgsCallAction](https://docs.microsoft.com/powershell/module/skype/New-CsRgsCallAction)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

