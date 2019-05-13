---
title: 'Create or modify a collection of meeting configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify a collection of meeting configuration settings
ms:assetid: ce6773c1-a0d5-4405-8e32-33a6f3a46a1a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721889(v=OCS.15)
ms:contentKeyID: 49733822
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a collection of meeting configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

You can use the settings on the Meeting Configuration page to define various characteristics of the meeting join experience. By default, the global settings define the join experience. You can also create site-level and pool-level meeting join settings. If you create pool-level settings, those settings apply to all meetings hosted by that pool. If you do not create pool-level settings, site-level settings apply, if they exist. If you do not define site-level settings, the global settings apply to all meetings.

<div>

## To create new meeting join settings

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing** and then click **Meeting Configuration**.

4.  On the **Meeting Configuration** page, click **New**, and then do one of the following:
    
      - To create a site-level policy, click **Site configuration**. In the **Select a Site** search field, type all or part of the name of the site for which you want to define meeting join settings. In the resulting list of sites, click the site you want, and then click **OK**.
    
      - To create a pool-level policy, click **Pool configuration**. In the **Select a Service** search field, type all or part of the name of the pool service for which you want to define meeting join settings. In the resulting list of services, click the pool you want, and then click **OK**.

5.  To route participants who dial in from the public switched telephone network (PSTN) through the lobby, clear the **PSTN callers bypass lobby** check box. By default, participants dialing in from the PSTN go directly to the meeting.

6.  To configure who can be a presenter in the meeting, in **Designate as presenter**, do one of the following:
    
      - To not allow anyone other than the organizer to be a presenter, click **None**.
    
      - To allow only participants who are members of your organization to be a presenter, click **Company**. This is the default setting.
    
      - To allow any participants to be a presenter, click **Everyone**.

7.  To have the organizer select a conference type when scheduling a meeting, clear the **Assigned conference type by default** check box. By default, the conference type is automatically assigned.

8.  To prevent anonymous (unauthenticated) users from being automatically admitted, clear the **Admit anonymous users by default** check box. By default, anonymous users are automatically admitted to meetings.

9.  To customize the meeting invite that is sent out to participants, do the following. Note that the maximum length for URLs and custom footer text is 1KB. Except for **Help URL**, if you do not specify a value for the customizations, they will not be included in the meeting. If you do not include a custom help URL, the default help URL for Lync will be displayed in the invite.
    
      - To customize the logo that appears in the meeting invite, in **Logo URL**, enter the location of the logo.
        
        <div>
        

        > [!NOTE]
        > The logo must be a GIF or JPG image with a size of 188 by 30 pixels.

        
        </div>
    
      - To customize the help text that appears in the meeting invite, in **Help URL**, enter the location of the help text.
    
      - To customize the legal text that appears in the meeting invite, in **Legal text URL**, enter the location of the legal text.
    
      - To customize the footer text that appears in the meeting invite, in **Custom footer text**, enter text.

10. Click **Commit**.

</div>

<div>

## To modify an existing collection of meeting configurations

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing** and then click **Meeting Configuration**.

4.  In the list of meeting configurations, click the configuration that you want to change, click **Edit**, and then click **Show details**.

5.  In **Edit Meeting Configuration**, modify any of the configuration settings, except for the configuration name, which cannot be modified.

6.  Click **Commit**.

</div>

<div>

## Creating New Meeting Configuration Settings by Using Windows PowerShell Cmdlets

Meeting configuration settings can be created (at the site scope only) by using Windows PowerShell and the New-CsMeetingConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To create meeting configuration settings that use the default values

  - This command creates a new set of meeting configuration settings for the Redmond site:
    
        New-CsMeetingConfiguration -Identity "site:Redmond"
    
    Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new meeting configuration settings will use the default values for all its properties.

</div>

<div>

## To change a property value when creating meeting configuration settings

  - To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of meeting configuration settings that, by default, admit everyone to a meeting as a presenter use a command like this:
    
        New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone"

</div>

<div>

## To change multiple property values when creating meeting configuration settings

  - Multiple property values can be modified by including multiple parameters. For example, this command admits everyone to a meeting as a presenter and also forces PSTN users to wait in the lobby until they are formally admitted to the meeting:
    
        New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone" -PSTNUCallersBypassLobby $True

</div>

For more information, see the help topic for the [New-CsMeetingConfiguration](https://technet.microsoft.com/en-us/library/Gg398065(v=OCS.15)) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

