---
title: 'Lync Server 2013: Defining your requirements for conferencing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Defining your requirements for conferencing
ms:assetid: 5c83e268-22bf-42b2-bac3-3237b5e02e03
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204935(v=OCS.15)
ms:contentKeyID: 48184255
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining your requirements for conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-30_

When you are determining which conferencing capabilities to deploy, you need to consider the features that you want available to your users and your network bandwidth capabilities. The following list of questions guides you through the conferencing planning process to determine what features of conferencing you should deploy, based on your organization’s requirements.

  - **Do you want to enable web conferencing, which includes document collaboration and application sharing?**
    
    If so, you must enable conferencing for your Front End pool in the Microsoft Lync Server 2013, Planning Tool or in Topology Builder. When you enable conferencing, you enable both web conferencing and A/V conferencing.
    
    Application sharing requires and uses more network bandwidth than document collaboration. Lync Server 2013 provides a throttling mechanism to control each application sharing session. By default, this is set to 1.5 KB/second for each session.
    
    If you do not want to enable application sharing but you do want document collaboration, you can enable conferencing and use meeting policies to disable application sharing. For details about configuring meeting policies, see [Conferencing policies in Lync Server 2013](lync-server-2013-conferencing-policies.md).
    
    To enable users to share PowerPoint presentations, you need to configure Office Web Apps Server. For details about configuring Office Web Apps Server, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - **Do you want to enable A/V conferencing?**
    
    If so, you must enable conferencing for your Front End pool in the Lync Server 2013, Planning Tool or in Topology Builder. When you enable conferencing, you enable both web conferencing and A/V conferencing.
    
    A/V conferencing requires and uses more network bandwidth than web conferencing (which includes document collaboration and application sharing). If you do not want to enable A/V conferencing but you do want to enable web conferencing, you can enable conferencing and use meeting policies to disable A/V conferences.
    
    If you do want to enable audio conferences but not video conferences, you can enable A/V conferencing and use meeting policies to prevent video conferences. Alternatively, you can enable A/V conferencing and enable only certain users to start or participate in A/V conferences.
    
    <div>
    

    > [!NOTE]  
    > Enterprise Voice is not required for you to use A/V conferencing. If you enable A/V conferencing, your users can add audio to their conferences if they have audio devices, even if you use a PBX for your telephone solution.

    
    </div>

  - **Do you want to enable users to join the audio portion of conferences when using a PSTN phone?**
    
    If so, deploy and enable dial-in conferencing. Invited users, both inside and outside your organization, can then join the audio portion of conferences by using a PSTN phone.

  - **Do you want to enable external users with Lync Server 2013 clients to join the types of conferences that you have enabled?**
    
    If so, you should deploy Edge Servers. By allowing external participation in meetings, you maximize your investment in Lync Server 2013. For example, users with laptops with Lync Server 2013 can join conferences from wherever they are—at home, in the airport, or at customer sites.
    
    Additionally, with Edge Servers deployed you can create federated relationships with other organizations-such as your customers or vendors-and users from those organizations can more easily collaborate with your users.
    
    For details about deploying Edge Servers, see [Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) and [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md). For details about enabling external access for Office Web Apps Server, see [Publishing Office Web Apps Server in Lync Server 2013 using a reverse proxy server](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md).

  - **Do you want to control the clients that can join Lync Server 2013 meetings?**
    
    If so, you should configure the meeting join page so that only the client options that you want to support are available. Each time a user clicks a link to join a scheduled meeting, Lync Server 2013 detects whether a client is already installed on the computer. It then starts the default client and opens the meeting join page, which contains links for alternate clients. The meeting join page always contains the option to use Microsoft Lync Web App. In addition to this option, you can decide whether to include links for Attendee and previous versions of Communicator. For details, see [Configuring the meeting join page in Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md).

<div>

## In This Section

  - [Web conferencing requirements in Lync Server 2013](lync-server-2013-web-conferencing-requirements.md)

  - [A/V conferencing requirements in Lync Server 2013](lync-server-2013-a-v-conferencing-requirements.md)

  - [Dial-in conferencing requirements in Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md)

</div>

<div>

## See Also


[Planning for conferencing in Lync Server 2013](lync-server-2013-planning-for-conferencing.md)  
[Deployment checklist for conferencing in Lync Server 2013](lync-server-2013-deployment-checklist-for-conferencing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

