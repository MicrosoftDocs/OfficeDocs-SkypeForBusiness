---
title: "Create or modify a hunt group workflow in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dcb9effb-5d12-4dee-80fc-ab9654222d5a
description: "Use one of the following procedures to create or modify a hunt group workflow."
---

# Create or modify a hunt group workflow in Lync Server 2013
[]
Use one of the following procedures to create or modify a hunt group workflow.
  
> [!NOTE]
> You can use Lync Server Management Shell or the Response Group Configuration Tool to create and modify hunt group workflows. You can access the Response Group Configuration Tool from Lync Server Control Panel, or by opening the webpage directly from a web browser by typing the following URL: https:// _\<webPoolFqdn\>_/RgsConfig. 
  
## To use Response Group Configuration Tool to create or modify a hunt group workflow

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Response Groups**, and then click **Workflow**.
    
4. On the **Workflow** page, click **Create or edit a workflow**.
    
5. In the **Select a Service** search field, type all or part of the name of the **ApplicationServer** service that hosts the workflow that you want to create or change. In the resulting list of services, click the service that you want, and then click **OK**.
    
    > [!NOTE]
    > The Response Group Configuration Tool opens. You can also open the Response Group Configuration Tool directly from a web browser by typing the following URL: https:// _\<webPoolFqdn\>_/RgsConfig. 
  
6. Do one of the following:
    
  - Under **Create a New Workflow**, next to **Hunt Group, click Create**.
    
  - Under **Manage an Existing Workflow**, locate the workflow you want to change, and then under **Action**, click **Edit**.
    
7. If you are ready for users to start calling the workflow, select **Activate the workflow**.
    
    > [!NOTE]
    >  If you are to creating a managed workflow, you need to select **Activate the workflow**. After you save the active, managed workflow, you can then modify and deactivate it. 
  
8. To allow federated users to call the group, select the **Enable for federation** check box. You must also have an external access policy that applies to the Response Group application configured for federation. 
    
    > [!NOTE]
    > The global external access policy applies to the Response Group application. You can configure the global policy for response group federation by using Lync Server Control Panel or by using the **Set-CsExternalAccessPolicy** cmdlet to set the EnableOutsideAccess parameter to True. Keep in mind that global policy settings apply to all users unless they are assigned a site or user policy. Therefore, before changing this setting for response groups, make sure that the federation setting meets the requirements of your organization. For details about how policies apply to users, see [Manage external access policy in Lync Server 2013](manage-external-access-policy-for-your-organization.md). For details about the federation setting, see [Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md). 
  
    > [!NOTE]
    > Users who are hosted in Skype for Business Online can't place calls to response groups that are hosted in an on-premise deployment. This is true in both hybrid deployments and in cases where an on-premise deployment is federated with a Skype for Business Online deployment. 
  
9. To hide the identity of agents during calls, select the **Enable agent anonymity** check box. 
    
    > [!NOTE]
    > Anonymous calls cannot start with instant messaging (IM) or video, although the agent or the caller can add IM and video after the call is established. An anonymous agent can also put calls on hold, transfer calls (both blind and consultative transfers), and park and retrieve calls. Anonymous calls do not support conferencing, application sharing and desktop sharing, file transfer, whiteboarding and data collaboration, and call recording. Agents using the Lync VDI Plugin can receive incoming calls anonymously, but they cannot make outgoing calls anonymously. 
  
10. Under **Enter the address of the group that will receive the calls**, type the primary SIP uniform resource identifier (URI) address of the group that will answer calls to the workflow.
    
    > [!NOTE]
    > The primary URI for a workflow is how the workflow is identified and referenced. The SIP URI that you enter is created as a contact object in Active Directory Domain Services. To create the URI, the object must be unique in Active Directory. 
  
11. In **Display name**, type the name that you want to display for the workflow (for example, Sales Response Group).
    
    > [!NOTE]
    > Do not include the "<" or ">" characters in the display name. Do not use the following display names because they are reserved: **RGS Presence Watcher** or **Announcement Service**. 
  
12. Under **Telephone number**, type the line URI for the response group (for example, +14255550165).
    
13. In **Display number**, type the number as you want it to appear for the response group (for example, +1 (425) 555-0165).
    
14. (Optional) In **Description**, type a description for the workflow as you want it to appear on the contact card in Lync client.
    
15. In **Workflow Type**, select **Managed** if this workflow will be managed by a Response Group Manager. Do the following to assign Response Group Managers to the workflow: 
    
1. Type the SIP URI of a manager for this workflow, and click **Add**.
    
2. Type the SIP URI of additional managers to add to the workflow, and click **Add**.
    
    > [!IMPORTANT]
    > Every user who is designated as a manager of a response group must be assigned the CsResponseGroupManager role. If users are not assigned this role, they cannot manage response groups. 
  
16. Under **Step 2 Select a Language**, click the language that you want to use for speech recognition and text-to-speech.
    
17. If you want to configure a welcome message, under **Step 3 Configure a Welcome Message**, select the **Play a welcome message** check box, and then do one of the following: 
    
  - To enter the welcome message as text that is converted to speech for callers, click **Use text-to-speech**, and then type the welcome message in the text box.
    
    > [!NOTE]
    > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message. 
  
  - To use a wave (.wav) or Windows Media audio (.wma) file recording for the welcome message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the audio file that you want to use, and then click **Open**. Click **Upload** to load the audio file. 
    
    > [!NOTE]
    > All user-provided audio files must meet certain requirements. For details about supported file formats, see [Technical requirements for Response Group in Lync Server 2013](technical-requirements-for-response-group.md). 
  
18. Under **Step 4 Specify Your Business Hours**, in **Your time zone**, click the time zone for the workflow.
    
    > [!NOTE]
    > The time zone is the time zone where the callers and agents of the workflow reside. It is used to calculate the open and close hours. For example, if the workflow is configured to use the North American Eastern Time zone and the workflow is scheduled to open at 7:00 A.M. and close at 11:00 P.M., the open and close times are assumed to be 7:00 Eastern Time and 23:00 Eastern Time respectively. (You must enter the times in 24-hour time notation.) 
  
19. Select the type of business hours schedule you want to use by doing one of the following:
    
  - To use a predefined schedule of business hours, click **Use a preset schedule**, and then select the schedule you want to use from the drop-down list.
    
    > [!NOTE]
    > You must have defined at least one preset schedule previously to be able to select this option. You define preset schedules by using the **New-CSRgsHoursOfBusiness** cmdlet. For details, see [(Optional) Define Response Group business hours in Lync Server 2013](optional-define-response-group-business-hours.md). 
  
    > [!NOTE]
    > When you select a preset schedule, **Day**, **Open**, and **Close** are automatically filled with the days and hours that the response group is available. 
  
  - To use a custom schedule that applies only to this workflow, click **Use a custom schedule**.
    
20. If you are creating a custom schedule for this workflow, click the check boxes for the days of the week that the response group is available.
    
21. If you are creating a custom schedule, type the **Open** and **Close** hours for each day of the week that the response group available. 
    
    > [!NOTE]
    > The **Open** and **Close** hours must be in 24-hour time notation. For example, if your office works a 9-to-5 work day and closes at noon for lunch, the business hours are specified as **Open** 9:00, **Close** 12:00, **Open** 13:00, and **Close** 17:00. 
  
22. If you want to play a message when the office is not open, select the **Play a message when the response group is outside of business hours** check box, and then specify the message to play by doing one of the following: 
    
  - To enter the message as text that is converted to speech for the caller, click **Use text-to-speech**, and then type the message in the text box.
    
    > [!NOTE]
    > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message. 
  
  - To use an audio file recording for the message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file. 
    
    > [!NOTE]
    > All user-provided audio files must meet certain requirements. For details about supported audio file formats, see [Technical requirements for Response Group in Lync Server 2013](technical-requirements-for-response-group.md). 
  
23. Specify how to handle calls after the message is played (if a message is configured):
    
  - To disconnect the call, click **Disconnect Call**.
    
  - To forward the call to voice mail, click **Forward to voice mail**, and then type the voice mail address. The format for the voice mail address is  _\<username\>_@ _\<domainName\>_ (for example, bob@contoso.com). 
    
  - To forward the call to another user, click **Forward to SIP URI**, and then type a user address. The format for the user address is  _\<username\>_@ _\<domainName\>_.
    
  - To forward the call to another telephone number, click **Forward to telephone number**, and then type the telephone number. The format for the telephone number is  _\<number\>_@ _\<domainName\>_ (for example, +14255550121@contoso.com). The domain name is used to route the caller to the correct destination. 
    
24. Under **Step 5 Specify Your Holidays**, click the check boxes for one or more sets of holidays that define the days when the response group is closed for business.
    
    > [!NOTE]
    > You need to define holidays and holiday sets before you configure the workflow. Use the **New-CsRgsHoliday** and **New-CsRgsHolidaySet** cmdlets to define holidays and holiday sets. For details, see [(Optional) Define Response Group holiday sets in Lync Server 2013](optional-define-response-group-holiday-sets.md). 
  
25. If you want to play a message on holidays, select the **Play a message during holidays** check box, and then specify the message to play by doing one of the following: 
    
  - To enter the message as text that is converted to speech for the caller, click **Use text-to-speech**, and then type the message in the text box.
    
    > [!NOTE]
    > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message. 
  
  - To use an audio file recording for the message, click **Select a recording**. If you want to upload a new audio file, click the **a recording** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file. 
    
    > [!NOTE]
    > All user-provided audio files must meet certain requirements. For details about supported audio file formats, see [Technical requirements for Response Group in Lync Server 2013](technical-requirements-for-response-group.md). 
  
26. Specify how to handle calls after the message is played (if a message is configured):
    
  - To disconnect the call, click **Disconnect Call**.
    
  - To forward the call to voice mail, click **Forward to voice mail**, and then type the voice mail address. The format for the voice mail address is  _\<username\>_@ _\<domainName\>_ (for example, bob@contoso.com). 
    
  - To forward the call to another user, click **Forward to SIP URI**, and then type a user address. The format for the user address is  _\<username\>_@ _\<domainName\>_.
    
  - To forward the call to another telephone number, click **Forward to telephone number**, and then type the telephone number. The format for the telephone number is  _\<number\>_@ _\<domainName\>_ (for example, +14255550121@contoso.com). The domain name is used to route the caller to the correct destination. 
    
27. Under **Step 6 Configure a Queue**, in **Select the queue that will receive the calls**, select the queue that you want to hold callers until an agent becomes available.
    
28. Under **Step 7 Configure Music on Hold**, choose the music you want callers to listen to while waiting for an agent by doing one of the following:
    
  - To use the default music-on-hold recording, click **Use default**.
    
  - To use an audio file recording for the music on hold, click **Select a music file**. If you want to upload a new audio file, click the **a music file** link. In the new browser window, click **Browse**, select the file that you want to use, and then click **Open**. Click **Upload** to load the audio file. 
    
    > [!NOTE]
    > All user provided audio files must meet certain requirements. For details about supported audio file formats, see [Technical requirements for Response Group in Lync Server 2013](technical-requirements-for-response-group.md). 
  
29. Click **Deploy**.
    
## To use Windows PowerShell to create or modify a hunt group workflow

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Create the prompt to be played for the welcome message, and save it in a variable. At the command line, run:
    
  ```
  $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
  ```

    For example:
    
  ```
  $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to Contoso. Please wait for an available agent."
  ```

    > [!NOTE]
    > To use an audio file for the prompt, use the **Import-CsRgsAudioFile** cmdlet. For details, see [Import-CsRgsAudioFile](import-csrgsaudiofile.md). 
  
4. Get the identity of the queue or question where the calls will be directed. At the command line, run:
    
  ```
  $qid = (Get-CsRgsQueue -Name "Help Desk").Identity
  ```

    For details about creating the queue, see [New-CsRgsQueue](new-csrgsqueue.md).
    
5. Define the default action to be taken when a workflow is opened during business hours, and save it in a variable. At the command line, run:
    
  ```
  $actionWM = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken> -QueueID $qid
  ```

    > [!NOTE]
    > For hunt group workflows, the default action must direct the call to a queue. This is parameter is required for active workflows. It is not required for inactive workflows. 
  
    For example:
    
  ```
  $actionWM = New-CsRgsCallAction -Prompt $promptWM -Action TransferToQueue -QueueID $qid.Identity
  ```

6. If you want to define business hours and holidays, you need to create them before you create or modify the workflow. For details, see [(Optional) Define Response Group business hours in Lync Server 2013](optional-define-response-group-business-hours.md) and [(Optional) Define Response Group holiday sets in Lync Server 2013](optional-define-response-group-holiday-sets.md).
    
7. If you want to have prompts for calls that are received out of business hours or on holidays, use the **New-CsRgsPrompt** cmdlet to define the prompt, and use the **New-CsRgsCallAction** to define the action to be taken after the prompt. For details, see [New-CsRgsPrompt](new-csrgsprompt.md) and [New-CsRgsCallAction](new-csrgscallaction.md).
    
8. Retrieve the service name for the Lync Server Response Group service and assign it to a variable. At the command, run:
    
  ```
  $serviceId="service:"+(Get-CSService | ?{$_.Applications -like "*RGS*"}).ServiceId;
  ```

9. Create or modify the workflow. To create a workflow, use **New-CsRgsWorkflow**. To modify a workflow, use **Set-CsRgsWorkflow**. At the command line, type: 
    
  ```
  $workflowHG = New-CsRgsWorkflow -Parent <service ID for the Response Group service> -Name "<hunt group name>" [-Description "<hunt group description>"] -PrimaryUri "<SIP address for the workflow>" [-LineUri "<Phone number for the workflow>"] [-DisplayNumber "<Phone number displayed in Lync>"] [-Active <$true | $false>] [-Anonymous <$true | $false>] [-DefaultAction <variable from preceding step>] [-EnabledForFederation <$true | $false>] [-Managed <$true | $false>] [-MangersByUri <SIP addresses for Response Group Managers who can manage the workflow>]
  ```

    For example:
    
  ```
  $workflowHG = New-CsRgsWorkflow -Parent $serviceID -Name "Human Resources" -Description "Human Resources workflow" -PrimaryUri "sip:humanresources@contoso.com" -LineUri "TEL:+14255551219" -DisplayNumber "555-1219" -Active $true -Anonymous $true -DefaultAction $actionWM -EnabledForFederation $false -Managed $true -ManagersByUri "sip:bob@contoso.com", "mindy@contoso.com"
  ```

    > [!IMPORTANT]
    > All users who are designated managers for workflows must be assigned the CsResponseGroupManager role. 
  
    > [!NOTE]
    > For details about additional optional parameters, see [New-CsRgsWorkflow](new-csrgsworkflow.md) or [Set-CsRgsWorkflow](set-csrgsworkflow.md)
  
## See also

#### 

[(Optional) Define Response Group holiday sets in Lync Server 2013](optional-define-response-group-holiday-sets.md)
#### 

[(Optional) Define Response Group business hours in Lync Server 2013](optional-define-response-group-business-hours.md)
#### 

[New-CsRgsWorkflow](new-csrgsworkflow.md)
  
[Set-CsRgsWorkflow](set-csrgsworkflow.md)
  
[New-CsRgsPrompt](new-csrgsprompt.md)
  
[New-CsRgsCallAction](new-csrgscallaction.md)

