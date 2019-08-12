---
title: 'Lync Server 2013: Configure categories'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure categories
ms:assetid: 4547f514-f0c0-404d-890f-092ddeeac852
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204859(v=OCS.15)
ms:contentKeyID: 48184033
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure categories in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

In Lync Server 2013 Control Panel, you can use the **Category** section of the **Persistent Chat** page to configure categories. A Persistent Chat room category is a logical structure for organizing chat rooms. A category defines a default set of access control lists (ACLs) for controlling the users and user groups who may create or join the chat rooms. You can use categories enforce ethical walls between different subdivisions within their organizations.

Chat room categories may contain chat rooms, but not other categories. Each category describes its contents with metadata, such as Name and Description. In addition, the category has properties which can be set to control the behavior of the chat rooms belonging to it, such as if the chat rooms allow Invitations or File Uploads, or contain Chat History.

<div>

## To configure categories for chat rooms

1.  From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).
    
    <div>
    

    > [!IMPORTANT]  
    > You can also use Windows PowerShell cmdlets. For details, see <A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configuring Persistent Chat Server by using Windows PowerShell cmdlets</A> in the Deployment documentation.

    
    </div>

3.  In the left navigation bar, click **Persistent Chat**, and then click **Category**.
    
    For multiple Persistent Chat Server pool deployments, select the appropriate pool from the drop-down list.

4.  On the **Category** page, click **New** or **Edit**.

5.  In **Select a Service**, select the service corresponding to the Persistent Chat Server pool on which the category needs to be created. The service is the Persistent Chat Server pool that the Persistent Chat (client) uses to identify which pool the category belongs to. A category can belong to only one Persistent Chat Server pool, and cannot be moved to another one, or shared with another pool.

6.  In **New Category**, do the following:
    
    1.  In **Name**, specify a name for the new room category.
    
    2.  In **Description**, provide a detailed description for the room category (for example, a room category for Contoso).
    
    3.  To control whether invitations can be enabled for chat rooms that belong to this category, select or clear the **Enable invitations** check box. If selected, rooms in this category may have invitations on or off; if cleared, the rooms in this category are not allowed to have invitations. If a room has invitations on, when a new member is added to a room, he or she gets a notification of the new room in their Persistent Chat client.
    
    4.  To control file uploads in chat rooms belonging to this category, select or clear the **Enable file upload** check box. If selected, the rooms of this category can enable or disable file uploads; if cleared, the rooms of this category are not allowed to have file uploads.
        
        <div>
        

        > [!IMPORTANT]  
        > This setting is enforced on the server because custom applications or previous Group Chat clients that use Office Communications Server 2007 R2&nbsp;Group Chat Server or Lync Server 2010, Group Chat can post files to a room. The Lync 2013 client does not have file upload/download capability, so if you have a pure Lync 2013 deployment or Lync 2013 client, it is not possible to post files in a Persistent Chat Server chat room.

        
        </div>
    
    5.  To control chat history, select or clear the **Enable chat history** check box. If selected, room chats become persistent; otherwise, chat messages are not persisted. If compliance is enabled, room chats will be saved in compliance, but users will not be able to access older messages. This option can be used for rooms designated for real-time, ad hoc collaborations that don’t need chat history to be persisted.

7.  In **Edit Category**, do the following:
    
      - In **Membership**, in the **Allowed members** section, add or remove users and other Active Directory Domain Services principals (users, distribution groups, organizational units, and so on) that are permitted to be added as members of chat rooms belonging to the category. Principals permitted by a category can search for the rooms in the category (unless the room is hidden, in which case only members of the room can search for it in the directory).
    
      - In **Membership**, in the **Denied members** section, add or remove users and other Active Directory principals associated with members being denied from the room.
    
      - In **Membership**, in the **Creators** section, add or remove users and other Active Directory principals associated with creators for the category. A creator is a user who has permissions to create chat rooms and assign chat room managers and members.

8.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

