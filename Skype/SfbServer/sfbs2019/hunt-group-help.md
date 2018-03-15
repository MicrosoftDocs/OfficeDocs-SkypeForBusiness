---
title: "Hunt Group Help"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d9fabec2-913b-4964-a25e-8fe285e73a50
description: "In this articleStep 1 Activate and Name the WorkflowStep 2 Select a LanguageStep 3 Configure a Welcome MessageStep 4 Specify Your Business HoursStep 5 Specify Your HolidaysStep 6 Configure a QueueStep 7 Configure Music on HoldStep 8 Deploy or Cancel"
---

# Hunt Group Help
[]
 **In this article**
  
[Step 1 Activate and Name the Workflow](#sectionSection0)
  
[Step 2 Select a Language](#sectionSection1)
  
[Step 3 Configure a Welcome Message](#sectionSection2)
  
[Step 4 Specify Your Business Hours](#sectionSection3)
  
[Step 5 Specify Your Holidays](#sectionSection4)
  
[Step 6 Configure a Queue](#sectionSection5)
  
[Step 7 Configure Music on Hold](#sectionSection6)
  
[Step 8 Deploy or Cancel](#sectionSection7)
  
A hunt group workflow routes callers to a specified queue without asking the caller any questions. You specify the queue to which callers are routed. You can also choose a welcome message for the workflow, the music to play while a user is on hold, and the days and hours that the workflow is available. 
  
> [!NOTE]
> Office Communications Server 2007 R2 supported two types of hunt groups: basic and enhanced. In Lync 2013, as in Lync Server 2010, the hunt group workflow covers both of these types. 
  
You can use WMA or WAV files for settings such as messages and music that is played while users are on hold. For details about supported audio file formats, see [Technical requirements for Response Group in Lync Server 2013](technical-requirements-for-response-group.md). After you upload an audio file, you can listen to it to verify that you selected the correct file. To listen to the audio file, click the name of the file.
  
> [!NOTE]
> You must be assigned the CsAdministrator role or the CsResponseGroupAdministrator role to create workflows. You must be assigned the CsAdministrator role, the CsResponseGroupAdministrator role, or the CsResponseGroupManager role to configure workflows. 
  
## Step 1 Activate and Name the Workflow
<a name="sectionSection0"> </a>

This section contains the general settings for the workflow.
  
 **Activate the workflow**
  
> Select to enable users to call the workflow.
    
 **Enable for federation**
  
> Select to allow federated users to call the group. 
    
    > [!NOTE]
    > You must also have an external access policy that applies to the Response Group application configured for federation. The global external access policy applies to the Response Group application. You can configure the global policy for response group federation by using Lync Server Control Panel or by using the **Set-CsExternalAccessPolicy** cmdlet to set the EnableOutsideAccess parameter to True. Keep in mind that global policy settings apply to all users unless they are assigned a site or user policy. Therefore, before changing this setting for response groups, make sure that the federation setting meets the requirements of your organization. For details about how policies apply to users, see [Manage external access policy in Lync Server 2013](manage-external-access-policy-for-your-organization.md). For details about the federation setting, see [Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md) in Lync Server Management Shell documentation. 
  
 **Enable agent anonymity**
  
> Select to hide the identity of the agent, whether the agent receives an incoming call or the agent makes an outgoing call on behalf of the response group. When you make agents anonymous, calls cannot start with instant messaging (IM) or video, although the agent or the caller can add IM and video after the call is established. An anonymous agent can also put calls on hold, transfer calls (both blind and consultative transfers), and park and retrieve calls. Anonymous calls do not support conferencing, application sharing and desktop sharing, file transfer, whiteboarding and data collaboration, and call recording.
    
    > [!NOTE]
    > When agents use Lync 2010 Attendant, they can specify that by default all outgoing calls are on behalf of the selected response group. 
  
    > [!NOTE]
    > A consultative transfer is when an agent talks to the person who is to receive a transferred call before the call is actually transferred. Consultative transfers are supported when the person receiving the transfer is not anonymous. If the person initiating the transfer uses a consultative transfer to transfer a call to a PSTN or a Lync user and uses the anonymous option, the call appears to transfer properly to the receiver. However, the transfer fails and the transferred caller is disconnected. The person initiating the transfer can be either anonymous or known, but the effect is the same if the person receiving the transfer is anonymous. 
  
 **Enter the address of the group that will receive the calls**
  
> Type the address of the group that you want to answer calls to the workflow.
    
 **Display name**
  
> Type the name that clients, such as Lync 2013, are to display.
    
    > [!NOTE]
    > Do not include the "\<" or "\>" characters in the display name. Do not enter a display name of "RGS Presence Watcher" or "Announcement Service," because these names are reserved names. 
  
 **Telephone number**
  
> Enter the line URI for the response group (for example, +14255550165).
    
 **Display number**
  
> Enter the formatted number to display for the response group (for example, +1 (425) 555-0165).
    
 **Description**
  
> Specify the workflow description that appears on the Lync 2013 contact card. This setting is optional.
    
 **Workflow Type**
  
> Select **Unmanaged** if the response group has no assigned Response Group Managers. Select **Managed** if the response group has assigned Response Group Managers, and then for each Manager, type the Manager's SIP address and click **Add**.
    
    > [!IMPORTANT]
    > You need to assign the CsResponseGroupManager role to all users who are designated as managers of a response group. If users are not assigned the CsResponseGroupManager role, they will not be able to manage response groups. 
  
## Step 2 Select a Language
<a name="sectionSection1"> </a>

Select the language that you want to use for speech recognition and text-to-speech.
  
## Step 3 Configure a Welcome Message
<a name="sectionSection2"> </a>

You can play a welcome message for callers. The welcome message can be one of the following:
  
- A text message that is converted to speech for callers.
    
- An audio file (WAV or WMA format) that contains the welcome message.
    
 **Play a welcome message. Choose the message format.**
  
> Select to have callers hear a welcome message.
    
 **Use text-to-speech**
  
> Select this option if you want to use text converted to speech for the welcome message, and then type the text for the welcome message in the text box.
    
    > [!NOTE]
    > If you choose to play a welcome message, you must enter something in the **Use text-to-speech** box even if you select a recording. 
  
    > [!NOTE]
    > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message. 
  
 **Select a recording**
  
> Select this option if you want to use an audio file recording for the welcome message. Click the **a recording** link if you want to upload a new audio file. 
    
## Step 4 Specify Your Business Hours
<a name="sectionSection3"> </a>

The business hours settings define when the workflow is available to answer calls and specify the actions to take for calls outside of business hours. You can do the following:
  
- Use a preset schedule. Response Group administrators can use the **New-CsRgsHoursOfBusiness** cmdlet to create predefined schedules that you can use for any number of response groups. 
    
- Use a custom schedule. You can specify the days and hours to define the business hours schedule for a specific response group.
    
- Play a message when someone calls outside of business hours.
    
- Disconnect the call, or forward the caller to voice mail, another SIP URI, or another telephone number when someone calls outside of business hours.
    
 **Your time zone**
  
> Select the time zone for the workflow.
    
    > [!NOTE]
    > The time zone is the time zone where the callers and agents of the workflow reside. It is used to calculate the hours that the workflow is open and closed. For example, if the workflow is configured to use the North American Eastern Time zone, and the workflow is scheduled to open at 7:00 A.M. and close at 11:00 P.M., the open and close times are 7:00 Eastern Time and 23:00 Eastern Time, respectively. (You must enter the times in 24-hour format.) 
  
 **Use a preset schedule**
  
> Select a preset schedule to automatically specify the days and hours that the response group is available.
    
    > [!NOTE]
    > You need to define preset schedules before you configure the workflow. You define preset schedules by using the **New-CsRgsHoursOfBusiness** cmdlet. For details, see the Lync Server Management Shell documentation. 
  
 **Use a custom schedule**
  
> Select this option if you want to create a schedule specific to this workflow.
    
 **Day**
  
> If you are creating a custom schedule, select each day of the week that you want the workflow to be available. If you are using a preset schedule, the days are automatically set based on the selected schedule.
    
 **Open**
  
> If you are creating a custom schedule, use this field with the **Close** field to specify the hours that agents are available to answer calls. If you are using a preset schedule, the hours are automatically set based on the selected schedule. 
    
    You must enter times in 24-hour format. For example, if your office works a 9 A.M. to 5 P.M. workday and closes at noon for lunch, you configure this schedule as **Open** 9:00, **Close** 12:00, **Open** 13:00, and **Close** 17:00. 
    
 **Close**
  
> If you are creating a custom schedule, use this field with the **Open** field to specify the hours that agents are available to answer calls. If you are using a preset schedule, the hours are automatically set based on the selected schedule. 
    
 **Play a message when the response group is outside of business hours.**
  
> Select to have callers hear a message if they call when the response group is not available.
    
 **Use text-to-speech**
  
> If you choose to play a message outside of business hours, select this option to use text converted to speech for the message, and type the text for the message in the text box.
    
    > [!NOTE]
    > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message. 
  
 **Select a recording**
  
> If you choose to play a message outside of business hours, select this option to use an audio file recording for the message. Click the **a recording** link if you want to upload a new audio file. 
    
 **Disconnect call**
  
> Select this option if you want to disconnect the call after playing the outside-of-business-hours message.
    
 **Forward to voice mail**
  
> Select this option if you want to forward the call to voice mail after playing the outside-of-business-hours message, and type the address of the voice mail. The format of the voice mail address is username@domainname (for example, bob@contoso.com).
    
 **Forward to SIP URI**
  
> Select this option if you want to forward the call to another user after playing the outside-of-business-hours message, and type the address of the user. The format for the user address is username@domainname.
    
 **Forward to telephone number**
  
> Select this option if you want to forward the call to another telephone number, and type the telephone number. The format of the telephone number is number@domainname (for example, +14255550121@contoso.com).
    
## Step 5 Specify Your Holidays
<a name="sectionSection4"> </a>

The holiday settings define the days that the response group is closed for business and specify the action to take on those days. You can do the following:
  
- Specify one or more standard holiday sets.
    
- Play a message if someone calls on a holiday.
    
- Disconnect the call, or forward the caller to voice mail, another SIP URI, or another telephone number.
    
 **Standard holiday lists**
  
> Select one or more holiday sets that identify the days that the response group is closed for business.
    
    > [!NOTE]
    > You need to define your holidays and holiday sets before you configure the workflow. To define holidays and holiday sets, use the **New-CsRgsHoliday** and **New-CsRgsHolidaySet** cmdlets. For details, see the Lync Server Management Shell documentation. 
  
 **Play a message during holidays.**
  
> Select to have callers hear a message if they call when the response group is on holiday.
    
 **Use text-to-speech**
  
> If you choose to play a message on holidays, select this option to use text converted to speech for the message, and then enter the text for the message in the text box.
    
    > [!NOTE]
    > Do not include HTML tags in the text you enter. If you include HTML tags, you will receive an error message. 
  
 **Select a recording**
  
> If you choose to play a message on holidays, select this option to use an audio file recording for the message. Click the **a recording** link if you want to upload a new audio file. 
    
 **Disconnect call**
  
> Select this option if you want to disconnect the call after playing the holiday message.
    
 **Forward to voice mail**
  
> Select this option if you want to forward the call to voice mail after playing the holiday message, and enter the address of the voice mail. The format of the voice mail address is username@domainname (for example, bob@contoso.com).
    
 **Forward to SIP URI**
  
> Select this option if you want to forward the call to another user after playing the holiday message, and enter the address of the user. The format for the user address is username@domainname.
    
 **Forward to telephone number**
  
> Select this option if you want to forward the call to another telephone number, and enter the telephone number. The format of the telephone number is number@domainname (for example, +14255550121@contoso.com).
    
## Step 6 Configure a Queue
<a name="sectionSection5"> </a>

The queue holds callers until an agent becomes available. 
  
 **Select the queue that will receive the calls**
  
> Select the queue to use for the response group from the list of available queues.
    
## Step 7 Configure Music on Hold
<a name="sectionSection6"> </a>

Callers listen to the music on hold while they wait for an agent. The music on hold can be one of the following:
  
- The default recording.
    
- A WMA or WAV file that you want to upload.
    
 **Use default**
  
> Select this option if you want to use the default music on hold.
    
 **Select a music file**
  
> Select this option if you want to specify a different audio file recording for the music on hold. Click the **a music** link to upload a new audio file. 
    
## Step 8 Deploy or Cancel
<a name="sectionSection7"> </a>

Click **Deploy** to create or edit the response group workflow. 
  
Click **Cancel** to cancel all your changes. 
  

