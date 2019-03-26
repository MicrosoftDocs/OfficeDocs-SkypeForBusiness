---
title: 'Lync Server 2013: Create or modify a conferencing policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a conferencing policy
ms:assetid: e2974030-2c0a-4634-91e8-93f4e2d674d9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721910(v=OCS.15)
ms:contentKeyID: 49733844
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a conferencing policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-07_

Follow these steps to create a user-level or a site-level conferencing policy. For details about how to assign a user-level policy to a user, see [Assign a per-user conferencing policy in Lync Server 2013](lync-server-2013-assign-a-per-user-conferencing-policy.md). For a list of all available conferencing policy settings, see [Conferencing policy settings reference for Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md).

<div>

## To create a new user or site policy

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing** and then click **Conferencing Policy**.

4.  Click **New**, and then do one of the following:
    
      - To create a user-level policy, click **User policy**. In **New Conferencing Policy**, in **Name**, type a descriptive name for the policy.
    
      - To create a site-level policy, click **Site policy**. In the **Select a Site** search field, type all or part of the name of the site for which you want to create a policy. In the list of sites, click the site that you want, and then click **OK**.
        
        <div>
        

        > [!NOTE]  
        > The site name becomes the conferencing policy name, and it cannot be changed.

        
        </div>

5.  In **Description**, type a description for the policy.

6.  Under **Organizer policy**, in **Maximum meeting size**, type the maximum number of users that you want to allow at a meeting. By default, the maximum meeting size is 250.

7.  To prevent users from inviting anonymous users to meetings, clear the **Allow participants to invite anonymous users** check box. Anonymous users are users who do not have credentials in your organization’s Active Directory Domain Services and who, therefore, are not authenticated. By default, users can invite anonymous users to meetings.

8.  In **Recording**, do one of the following:
    
      - To prevent participants from recording meetings, click **None**. This is the default setting.
    
      - To allow participants to record meetings, click **Enable recording**.

9.  To allow external participants to record meetings, select the **Allow federated and anonymous participants to record** check box. The default is to prevent external participants from recording meetings.

10. In **Audio/video**, do one of the following:
    
      - To prevent the use of audio and video, click **None**.
    
      - To allow the use of audio but not video, click **Enable IP audio**.
    
      - To allow the use of audio and video, click **Enable IP audio/video**. This is the default setting.

11. If you chose to allow the use of audio in **Audio/video**, do the following:
    
      - To prevent users from joining the meeting by dialing in, clear the **Enable PSTN dial-in conferencing** check box. By default, users can dial in to meetings by using the public switched telephone network (PSTN).
    
      - If you allow users to dial in to meetings and you want to allow unauthenticated (anonymous) users to join a meeting by using dial out phoning, select the **Allow anonymous participants to dial out** check box. With dial-out phoning, the conference server calls the user, and the user answers the phone to join the meeting. By default, anonymous users cannot join a meeting by using dial-out phoning.

12. If you chose to allow the use of video in **Audio/video**, check **Allow multiple video streams** .

13. In **Data collaboration**, do one of the following:
    
      - To prevent data collaboration, click **None**.
    
      - To allow data collaboration, click **Enable data collaboration**. This is the default setting.

14. If you chose to allow data collaboration in **Data collaboration**, do the following:
    
      - To prevent external downloads, clear the **Allow federated and anonymous participants to download content** check box. By default, external users can download content.
    
      - To prevent file transfers, clear the **Allow participants to transfer files** check box. By default, users can transfer files.
    
      - To prevent the use of annotations, clear the **Enable annotations** check box. To the use of annotations in shard PowerPoint presentations, clear the **Enable PowerPoint annotations**. By default, annotations are allowed.
    
      - To prevent the use of polls, clear the **Enable polls** check box. By default, polls are allowed.

15. In **Application sharing**, do one of the following:
    
      - To prevent the use of application sharing, click **Disable application sharing**.
    
      - To allow the use of application sharing, click **Enable application sharing**. This is the default setting.

16. If you chose to allow application sharing in **Application sharing**, do the following:
    
      - To prevent meeting participants from taking control of application sharing, clear the **Allow participants to take control** check box. By default, participants can take control of application sharing.
    
      - If you chose to allow meeting participants to take control of application sharing, select the **Allow federated and anonymous participants to take control** check box to allow external users to take control of application sharing. By default, external users cannot take control of application sharing.

17. Under **Participant policy**, do one of the following:
    
      - To prevent both application sharing and desktop sharing, click **Disable application and desktop sharing**.
    
      - To allow application sharing but not desktop sharing, click **Enable application sharing**.
    
      - To allow both application sharing and desktop sharing, click **Enable application and desktop sharing**. This is the default setting.

18. To prevent peer-to-peer file transfers, clear the **Enable peer-to-peer file transfer** check box. By default, peer-to-peer file transfers are allowed.

19. To allow peer-to-peer recording, select the **Enable peer-to-peer recording** check box. By default, peer-to-peer recording is not allowed.

20. To allow participants to join with multiple video streams, select the **Enable participants to join with multiple video streams** check box. By default, multiple video streams are allowed.

21. Click **Commit**.

</div>

<div>

## To modify an existing user or site policy

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing** and then click **Conferencing Policy**.

4.  In the list of conferencing policies, click the policy that you want to change, click **Edit**, and then click **Show details**.

5.  In **Edit Conferencing Policy**, modify any of the policy settings, except for the policy name, which cannot be modified.

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

