---
title: 'Lync Server 2013: Using Call Me At with a Lync-enabled phone'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Using Call Me At with a Lync-enabled phone
ms:assetid: 975a1df8-a159-4aa4-a991-5972a535998e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn383570(v=OCS.15)
ms:contentKeyID: 56470326
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Call Me At with a Lync-enabled phone and Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-09_

The Call Me At feature in Lync provides a way for users to join the audio portion of a conference by using a cell phone, “land line,” or other device connected to the Public Switched Telephone Network (PSTN). When you attempt to join a meeting by using Lync, you will typically be presented with the **Join Meeting Audio** dialog box:

![Use Lync to join meeting audio window screenshot](images/Dn383570.e28f17f0-9f17-44ef-b893-f4ef132f47ac(OCS.15).png "Use Lync to join meeting audio window screenshot")

If you select **Call me at**, you can then pick a phone number from the dropdown list. Lync Server 2013 will place a phone call to the selected number, and you can then use that phone to participate in the audio portion of the conference.

The dropdown list is populated by the phone numbers (for mobile phone, home phone, or other phone) that you have entered on the **Phones** tab in the **Lync – Options** dialog box:

![Lync Phones set up options screenshot](images/Dn383570.03d2f25d-49e2-47b4-b1e9-b1614fc0c11c(OCS.15).png "Lync Phones set up options screenshot")

If you have not entered any phone numbers on the **Phones** tab then you will not have any numbers available in the dropdown box. However, you can always click **New Number** and have Lync Server dial out to any phone number you wish:

![Lync join meeting audio call me window screenshot](images/Dn383570.27f2ac7a-cc1c-465c-b145-202ad03af4f2(OCS.15).png "Lync join meeting audio call me window screenshot")

The Call Me At feature works extremely well provided that you use it in the way it was intended: by having Lync Server call a PSTN phone number. However, you can run into a less-than-optimal experience if you ask Lync Server to call you at a Lync-enabled endpoint (for example, a phone in a conference room). Following is the issue you might run into, as well as two ways to work around the problem.

To begin, here’s what happens when you provide the Call Me At feature with the phone number of a Lync-enabled phone. Suppose Ken Myer tries to join a meeting by having Lync Server call him at 1-206-555-1219, a Lync Server-enabled phone number. Ken will initially be connected to the meeting, but after a few seconds Lync will display the message **Call was not completed or has ended**, and Ken will appear to have been dropped from the meeting:

![Screen shot of Lync call conferencing window](images/Dn383570.c2a81727-8751-41b5-946a-03a1b75b9d95(OCS.15).png "Screen shot of Lync call conferencing window")

Notice, however, that there is a discrepancy within the Lync conversation window. Ken Myer is the only name listed under the **Participants** heading. However, if you look in the title bar of the window, you’ll see that the conference contains a total of 4 participants.

Likewise, if you look in the conversation window of any of the other conference participants you will not see Ken Myer listed anywhere:

![Lync participant list window screenshot](images/Dn383570.fa5990cf-2694-402c-ac06-946aa66b6837(OCS.15).png "Lync participant list window screenshot")

And yet, at the same time, Ken Myer will be able to participate in the audio portion of the call by using his Lync-enabled phone. The Call Me At feature has actually worked, but the user experience is less than optimal.

There are at least two ways to work around this problem. If you have already joined a conference in this fashion (like Ken Myer did), you can typically resolve the issue by engaging in a different modality. For example, if you send an instant message the conversation window will now show all the conference participants, including yourself:

![Lync conversation and participant list screenshot](images/Dn383570.9b5ff6d6-9f73-467c-99a7-ef3aa8bd7e7a(OCS.15).png "Lync conversation and participant list screenshot")

At this point you should be able to participate in the meeting in the expected fashion.

Alternatively, you can avoid this issue altogether by changing the way you join the meeting. If you need to have Lync Server call a Lync Server-enabled phone, you should begin by joining the meeting without an audio connection. To do that, select Don’t join audio when presented with the Join Meeting Audio dialog box:

![Lync don't join meeting audio window screenshot](images/Dn383570.280a148d-cce5-4b02-87f9-9f78f17a81c1(OCS.15).png "Lync don't join meeting audio window screenshot")

After you have successfully connected to the meeting, you can now “invite” the Lync Server-enabled phone to join the meeting as well. To do that, place the mouse over the People icon and then click **Invite More People**:

![Lync invite more participants window screenshot](images/Dn383570.69b81b29-d1d2-4ed3-acb6-e37dd18e3d86(OCS.15).png "Lync invite more participants window screenshot")

That will bring up the **Send an IM** dialog box. Ignore the dialog box title (you’re not actually sending an instant message) and type the phone number of the Lync-enabled phone:

![Send an IM dialog box screenshot](images/Dn383570.cd67a3f0-06d8-41ba-a808-c067f64bec9f(OCS.15).png "Send an IM dialog box screenshot")

After you click **OK**, Lync Server will call the number entered in the dialog box. When the connection is made, you will have full audio capabilities through the Lync-enabled phone, and you will be able to see and interact with the full conference roster.

</div>

<span> </span>

</div>

</div>

</div>

