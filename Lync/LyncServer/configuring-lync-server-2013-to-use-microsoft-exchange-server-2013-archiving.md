﻿---
title: Configuring Lync Server 2013 to use Microsoft Exchange Server 2013 archiving
TOCTitle: Configuring Lync Server 2013 to use Exchange Server 2013 archiving
ms:assetid: 260346d1-edc8-4a0c-8ad2-6c2401c3c377
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ679896(v=OCS.15)
ms:contentKeyID: 49557731
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Microsoft Lync Server 2013 to use Microsoft Exchange Server 2013 archiving

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-24_

Microsoft Lync Server 2013 gives administrators the option of having instant messaging and Web conferencing transcripts archived to a user's Microsoft Exchange Server 2013 mailbox rather than a SQL Server database. If you enable this option, transcripts are written to the Purges folder in the user's mailbox. The Purges folder is a hidden folder found in the Recoverable Items folder. Although this folder is not visible to end-users, the folder is indexed by the Exchange search engine and can be discovered by using Exchange mailbox search and/or Microsoft SharePoint Server 2013. Because information is stored in the same folder used by the Exchange In-Place Hold feature (responsible for archiving email and other Exchange communications), administrators can use a single tool to search for all the electronic communications archived for a user.

<div>


> [!IMPORTANT]  
> To completely disable archiving of Lync conversation, you must also disable Lync conversation history. For more information, see the following topics: <A href="lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md">Managing the Archiving of internal and external communications in Lync Server 2013</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy">New-CsClientPolicy</A>, and <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy">Set-CsClientPolicy</A>.



</div>

In order to archive transcripts to Exchange 2013 you must begin by configuring server-to-server authentication between the two servers. After server-to-server authentication is in place you can then carry out the following tasks in Microsoft Lync Server 2013 (note that, depending on your setup and configuration, you might not need to complete all of these tasks):

1.  Enable Exchange archiving by modifying your Lync Server archiving configuration settings. This step is required for all deployments.

2.  Enable archiving for internal and/or external communications for your users. This step is required for all deployments.

3.  Configure the ExchangeArchivingPolicy property for each user. This step is only required in Lync Server and Exchange are located in different forests.

<div>

## Step 1: Enabling Exchange Archiving

Archiving in Lync Server is primarily managed by using the archiving configuration settings. When you install Lync Server 2013 you are automatically given a single, global collection of these settings. (Administrators can optionally create new collections of archiving settings at the site scope.) By default, archiving is not enabled in the global settings, nor is Exchange archiving enabled in these settings. In order to use Exchange archiving administrators must configure both the EnableArchiving and the EnableExchangeArchiving properties in these configuration settings. The EnableArchiving property can be set to one of three possible values:

  - **None**. Archiving is disabled. This is the default value. If EnableArchiving is set to None then nothing will be archived in either your Lync Server archiving database or in Exchange 2013.

  - **ImOnly**. Only instant message transcripts are archived. If Exchange archiving is enabled these transcripts will be archived in Exchange 2013. If Exchange archiving is disabled then these transcripts will be archived to Lync Server.

  - **ImAndWebConf**. Both instant message transcripts and Web conferencing transcripts are archived. If Exchange archiving is enabled these transcripts will be archived in Exchange 2013. If Exchange archiving is disabled then these transcripts will be archived to Lync Server.

The EnableExchangeArchiving property is a Boolean value: set EnableExchangeArchiving to True ($True) to enable Exchange archiving or set EnableExchangeArchiving to False ($False) to disable Exchange archiving. For example, this command enables the archiving of instant messaging transcripts and also enables Exchange archiving:

    Set-CsArchivingConfiguration -Identity "global" -EnableArchiving ImOnly -EnableExchangeArchiving $True

To disable Exchange archiving, use a command similar to the following, which enables instant messaging archiving but disables archiving to Exchange (in other words, transcripts will be archived to Lync Server):

    Set-CsArchivingConfiguration -Identity "global" -EnableArchiving ImOnly -EnableExchangeArchiving $False

<div>


> [!NOTE]  
> If the EnableArchiving property is set to None then Lync Server will not archive instant messaging and Web conferencing transcripts at all. In that case, the server will simply ignore the value configured for EnableExchangeArchiving.



</div>

Exchange archiving can also be enabled (or disabled) by using the Lync Server Control Panel. To do that, complete the following procedure:

1.  In Control Panel, click **Monitoring and Archiving**, and then click **Archiving Configuration**.

2.  On the **Archiving Configuration** tab, double-click the collection of archiving settings to be modified (for example, the **Global** collection).

3.  In the **Edit Archiving Setting** pane, click the **Archiving setting** dropdown list and select either **Archive IM sessions** (to archive just instant messaging sessions) or **Archive IM and web conferencing sessions** (to archive both instant messaging and Web conferencing sessions).

4.  After choosing the items to be archived, select the **Exchange Server integration** checkbox to enable Exchange archiving. To disable Exchange archiving, clear this checkbox.

<div>


> [!NOTE]  
> The <STRONG>Exchange Server integration</STRONG> checkbox will not be available if the <STRONG>Archiving setting</STRONG> is set to <STRONG>Disable archiving</STRONG>. You must enable archiving first and then enable Exchange archiving.



</div>

If Lync Server 2013 and Exchange 2013 are located in the same forest then archiving for individual users (or at least for users who have email accounts on Exchange 2013) is managed by using Exchange In-Place Hold policies. If you have users who are homed on a previous version of Exchange then archiving for those users will be managed by using Lync Server archiving policies. Note that only users with accounts on Exchange 2013 can have their Lync transcripts archived to Exchange.

If Lync Server 2013 and Exchange 2013 are located in different forests then archiving for individual users is managed by configuring the ExchangeArchivingPolicy property for each individual user account. See Step 3 for more information.

</div>

<div>

## Step 2: Enabling the Archiving of Internal and/or External Communications

After you have enabled archiving (and Exchange archiving) you must then modify the appropriate archiving policies to ensure that user sessions are actually archived. Note that simply enabling archiving (Step 1) does not cause Lync Server to begin archiving instant messaging and Web conferencing transcripts. Instead, you must use archiving policies to enable internal and/or external archiving. When you install Lync Server 2013 you also install a single, global archiving policy that contains two properties:

  - **ArchiveInternal**. When set to True ($True) indicates that internal communication sessions involving only users who have Active Directory accounts in your organization) will be archived.

  - **ArchiveExternal**. When set to True ($True) indicates that internal communication sessions (sessions involving at least one user who does not have an Active Directory account in your organization) will be archived.

By default, both of these property values are set to False, meaning that neither internal nor external communication sessions are archived. To modify the global policy, you can use the Lync Server Management Shell and the Set-CsArchivingPolicy cmdlet. This command enables the archiving of both internal and external communication sessions:

    Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True

Alternatively, you can use the New-CsArchivingPolicy to create a new policy at either the site scope or the per-user scope. For example, this command creates a new per-user archiving policy named RedmondArchivingPolicy:

    New-CsArchivingPolicy -Identity "RedmondArchivingPolicy" -ArchiveInternal $True -ArchiveExternal $True

If you create a per-user policy you will then need to assign that policy to the appropriate users. For example:

    Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName  "RedmondArchivingPolicy"

Archiving policies can also be managed by using the Lync Server Control Panel. Within the Control Panel, click **Monitoring and Archiving** and then click **Archiving Policy**. To modify an existing policy, double-click the policy (e.g., Global) and then, in the **Edit Archiving Policy** pane, select or clear the **Archive internal communications** and the **Archive external communications** checkboxes as needed. To create a new archiving policy, click **New** and then select either **Site policy** or **User policy**. If you create a new user policy then you must access the appropriate user accounts (from the **Users** tab) and assign those users the new policy.

</div>

<div>

## Step 3: Configuring the ExchangeArchivingPolicy Property

If Lync Server 2013 and Exchange 2013 are located in different forests then it is not enough to simply enable Exchange archiving in the archiving configuration settings; that will not result in instant messaging and Web conferencing transcripts being archived in Exchange. Instead, you must also configure the ExchangeArchivingPolicy property on each of the relevant Lync Server user accounts. This property can be set to one of four possible values:

1.  Uninitialized. Indicates that archiving will be based on the In-Place Hold settings configured for the user's Exchange mailbox; if In-Place Hold has not been enabled on the user's mailbox then the user will have his or her messaging and Web conferencing transcripts archived in Lync Server.

2.  **UseLyncArchivingPolicy**. Indicates that the user's instant messaging and Web conferencing transcripts should be archived in Lync Server rather than in Exchange.

3.  **NoArchiving**. Indicates that the user's instant messaging and Web conferencing transcripts should not be archived at all. Note that this setting overrides any Lync Server archiving policies assigned to the user.

4.  **ArchivingToExchange**. Indicates that the user's instant messaging and Web conferencing transcripts should be archived to Exchange regardless of the In-Place Hold settings that have (or have not) been assigned to the user's mailbox.

For example, to configure a user account so that instant messaging and Web conferencing transcripts are always archived to Exchange you can use a command similar to this from the Lync Server Management Shell:

    Set-CsUser -Identity "Ken Myer" -ExchangeArchivingPolicy ArchivingToExchange

If you want to set the same archiving policy for a group of users (for example, all the users homed on a specified Registrar pool) you can use a command similar to this:

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Set-CsUser -ExchangeArchivingPolicy ArchivingToExchange

Note that you must use the Lync Server Management Shell (and Windows PowerShell) in order to configure value of the ExchangeArchivingPolicy property. This property is not exposed to administrators in the Lync Server Control Panel.

If you would like to view a list of all the users who have been assigned a specific archiving policy then you can use a command similar to the following, which returns the Active Directory display name of all the users who have had the ExchangeArchivingPolicy property set to Uninitialized:

    Get-CsUser | Where-Object {$_.ExchangeArchivingPolicy -eq "Uninitialized"} | Select-Object DisplayName

Likewise, this command returns the display name of the users who have not have the ExchangeArchivingPolicy property set to UseLyncArchivingPolicy:

    Get-CsUser | Where-Object {$_.ExchangeArchivingPolicy -ne "UseLyncArchivingPolicy"} | Select-Object DisplayName

</div>

</div>

<span> </span>

</div>

</div>

</div>

