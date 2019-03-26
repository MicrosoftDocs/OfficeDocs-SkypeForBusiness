---
title: 'Lync Server 2013: Configure conferencing policy for dial-in'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure conferencing policy for dial-in
ms:assetid: 9bf926d6-0248-4352-98c3-9c5a333debbc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398810(v=OCS.15)
ms:contentKeyID: 48184979
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure conferencing policy for dial-in in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-21_

Conferencing policy is a user account setting that specifies the conferencing experience for participants. You can create conferencing policies with a site scope or a user scope. Conferencing policy settings encompass many aspects of conference scheduling and participation. Several conferencing policy settings support dial-in conferencing for participants. When you configure dial-in conferencing, you should verify that these fields are set appropriately for your organization, and modify them as necessary.

Verify the following fields in your conferencing policy:

  - **Allow participants to invite anonymous users**   This setting allows meeting organizers to invite anonymous (that is, unauthenticated) participants to meetings. This setting is optional for dial-in conferencing. This setting is selected by default in the default global conferencing policy.

  - **Enable PSTN dial-in conferencing**   This setting allows users to join the audio portion of a conference by dialing in from the PSTN. This setting is required for dial-in conferencing. This setting is selected by default in the default global conferencing policy.

  - **Allow anonymous participants to dial out**   This setting allows anonymous users who are already joined to the meeting to dial out to a phone number to join the audio portion of the conference. This setting is optional for dial-in conferencing. This setting is not selected by default in the default global conferencing policy.

  - **Allow participants not enabled for Enterprise Voice to dial out**   This setting allows meeting participants and organizers that are not enabled for Enterprise Voice to dial out to a phone number to join the audio portion of the conference. The dial-out call is authorized based on the organizer’s assigned voice policy. This setting is not selected by default in the default global conferencing policy. The setting default value is disabled.
    
    <div>
    

    > [!NOTE]  
    > To enable this capability, a meeting organizer that is not enabled for Enterprise Voice should have an appropriate voice policy assigned to them to authorize any dial-out from a conference organized by that user. A voice policy can be assigned to a user that is not enabled for Enterprise Voice from the Lync Server Management Shell. If the user does not have a voice policy explicitly assigned to him, the site voice policy will be used to authorize the dial-out request. If there is no site voice policy, the global voice policy will be used.&nbsp;

    
    </div>

The procedure in this section explains how to modify conferencing policy. For details about how to configure all of the settings that define the participant experience in the default conferencing policy, see [Create or modify a collection of meeting configuration settings in Lync Server 2013](lync-server-2013-create-or-modify-a-collection-of-meeting-configuration-settings.md). For details about how to create a conferencing policy for a specific user or group of users, see [Create or modify a conferencing policy in Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md). For a list of all available conferencing policy settings, see [Conferencing policy settings reference for Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md).

<div>

## To modify the conferencing policy for dial-in

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-ServerAdministrator** or **CsAdministrator** role.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing**.

4.  On the **Conferencing Policy** tab, double-click a conferencing policy name to open the **Edit Conferencing Policy** dialog box.

5.  Verify that the fields for dial-in conferencing are appropriate for your organization, and modify the settings if necessary.

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

